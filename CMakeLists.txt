cmake_minimum_required (VERSION 3.19.4)
get_filename_component (self ${CMAKE_CURRENT_SOURCE_DIR} NAME)
project (${self})

# set (xelatex "/usr/local/texlive/2021/bin/arm64/xelatex")
# set (xelatex "/Library/TeX/Distributions/.DefaultTeX/Contents/Programs/arm64/xelatex")
# set (xelatex "/Library/TeX/Distributions/.DefaultTeX/Contents/Programs/arm64/xelatex")


add_custom_target (pdf ALL)
add_custom_target (epub ALL)

add_custom_command (TARGET pdf 
	PRE_BUILD 
	COMMAND pandoc -o ${self}.pdf ${CMAKE_CURRENT_SOURCE_DIR}/header.yml ${CMAKE_CURRENT_SOURCE_DIR}/README.md --pdf-engine=xelatex
) # COMMAND pandoc --metadata title="${self}" -o ${self}.pdf ${CMAKE_CURRENT_SOURCE_DIR}/test.md 


add_custom_command (TARGET epub 
	PRE_BUILD 
	COMMAND pandoc --epub-cover-image=${CMAKE_CURRENT_SOURCE_DIR}/author.jpg ${CMAKE_CURRENT_SOURCE_DIR}/header.yml ${CMAKE_CURRENT_SOURCE_DIR}/README.md -o ${self}.epub --pdf-engine=xelatex
)

# add_custom_target (test ALL)
# add_custom_command (TARGET test PRE_BUILD COMMAND pandoc -o test2.md https://pandoc.org/MANUAL.html)
# add_custom_command(TARGET test PRE_BUILD COMMAND pandoc 
# --pdf-engine=xelatex 
# -o test2.pdf ${CMAKE_CURRENT_SOURCE_DIR}/header.yml README.md)

# pandoc -o test.md https://pandoc.org/MANUAL.html
# pandoc --pdf-engine=xelatex -o test.pdf test.md