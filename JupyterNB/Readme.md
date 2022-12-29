# To convert jupyter notebook to slides presentation:
1. Whitin each slide swith the slide presentation option between:
   1. `Slide`: the cell will be a new slide.  
   2. `Sub-Slide`: the cell will be shown in the current slide as a replacement for previous content. It will be available in arrow-down navigation.   
   3. `Fragment`: the cell will appear in the current slide, it will append to the previous content. It will be available in arrow-down and arrow-right navigation.   
   4. `Skip`: the content will not be displayed in the presentation.   
   5. `Notes`: notes for slide, the cell content is not displayed in the presentation.   
2. Run on the command line:   
   ```jupyter nbconvert file_name.ipynb --to slides --no-input presentation.ipynb```
