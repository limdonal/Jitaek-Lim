import os
from pptx import Presentation
from pptx.util import Inches

# Load your custom PowerPoint template
template_path = "your_template_path.potx"
prs = Presentation(template_path)

# Add content to the presentation
for content in content_list:
    slide_layout = prs.slide_layouts[0]  # Choose the slide layout you want to use
    slide = prs.slides.add_slide(slide_layout)

    # Add text
    text = slide.shapes.title
    text.text = content['title']

    # Add image (if applicable)
    if 'image' in content:
        img_path = content['image']
        left, top, width, height = Inches(1), Inches(2), Inches(6), Inches(4)
        slide.shapes.add_picture(img_path, left, top, width=width, height=height)

# Save the presentation
output_path = os.path.join("your_output_directory", "output.pptx")
prs.save(output_path)
