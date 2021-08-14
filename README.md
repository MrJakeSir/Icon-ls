<div align="center">
  <h1>Icon ls</h1>
</div>

<div>
  <p>
    <ul>
      <li><a href="#installation">Instalation</a></li>
      <li><a href="#usage">Usage</a></li>
      <li><a href="#config">Configuration</a></li>
    </ul>
  </p>
</div>

-----

<div>
  <h1 id="installation">Installation</h1>
  
  <p>
    The first thing that we need, are <a href="https://nerdfonts.com" target="blank_">the nerd fonts</a>, so we can see and personalize the icons in the script <br>
  
  So to do this, we will download any font from <a href="https://nerdfonts.com/font-downloads" target='blank_'>here</a> and copy them to your fonts directory

  <h4>If you dont have the .fonts directory...</h4>
  <pre>
    mkdir ~/.fonts
    mv any-font.zip ~/.fonts
    unzip ~/.fonts/any-font.zip
  </pre>

  and you'll have your font installed

  then, you need to <b>change your terminal font to the installed one</b>, so check your terminal emulator wiki to do that

  <hr>
  
  After installing the font, you can install the script now
  <pre>
    curl https://raw.githubusercontent.com/MrJakeSir/Icon-ls/master/ls.py -o path/to/script
  </pre>

  after you install the script, you have two options:

  <ul>
    <li>You can create a binary file by using <a href="https://www.pyinstaller.org/">pyinstaller</a> or py2bin</li>
    <li>Or you can create a simple alias in your .zshrc to call the script</li>
  </ul>

  I will explain <b>the second option</b> because it is way easier and its the same thing
  
  we need to go our home directory
  <pre>
    cd
  </pre>
  
  and then edit your shell config file
  for this, you can use vim, neovim, emacs, nano or any other
  
  <pre>
    # USE YOUR TEXT EDITOR HERE
    
    # For zsh
    nvim .zshrc

    # bash shell
    nvim .bashrc
  </pre>
  
  then, add this line to the end of your file, changing the <i>path/to/script.py</i> to your actual path 
  
  <pre>
    alias ls="python3 path/to/script.py"
  </pre>
  
  <b>restart your terminal</b> and you're done!
  

  </p>

</div>

-----

<div>
  <h1 id="usage">Usage</h1>
  <p>
  Type in your terminal 
  <code>ls</code>
  
  <b>Options</b>
  <pre>
      -h  --help                      Shows this dialog
      -sh -a --show-hidden            Shows the hidden files
      -oh -hi --only-hidden           Shows ONLY the hidden files
      -ex --exclude                   Excludes a file extension, for example:
                                              ls -ex 'py'
                                              This will exclude all the python files
  </pre>


  </p>
</div>


<div>
  <h1 id="config">Configuration</h1>
  <p>
  All you need is in the class <b>Extensions</b>
  It contains all the configuration options, you don't have to 
  create any directory in .config, you just mofify the script itself.

  <h2>Changing icons</h2>
  All the icons are in the variable called <b>self.extensions</b>, 
  it is just a python dictionary, you can add filetypes there with its icon,
  you just need to add the dictionary item

  <pre>
    self.extensions = {
      #... some items here
      'filetype': '<icon>'
    }
  </pre>

  <h2>Changing colors</h2>
  For this, will be a little more complex than just changing the icons.
  First of all, we need to search for this line of code:
  <pre>
    # Change this to custom if you want                                                                                                                                                       
    # to specify a color for each filetype                                                                                                                                                            # if it is custom, it will use self.filetype_color dictionary                                                                                                                             
    # to the colorscheme                                                                                                                                                                      
    self.colortype = 'rainbow'
    # self.colortype = 'custom'  
  </pre>
  
  Once found, you have to comment the line self.colortype = 'rainbow'
  by adding a hash symbol at the start of the line, then, you need to
  remove the comment from the line below of it.

  after doing that, it will look something like this
  <pre>
    # Change this to custom if you want                                                                                                                                                       
    # to specify a color for each filetype                                                                                                                                                            # if it is custom, it will use self.filetype_color dictionary                                                                                                                             
    # to the colorscheme                                                                                                                                                                      
    # self.colortype = 'rainbow'
    self.colortype = 'custom'
  </pre>

  After doing this, we need to find also this line of code
  
  <pre>
    # You can change the filetype color here
    # or you can also add more customized filetypes
    # the colors are in Red, Green and Blue format
    #   filetype    =    (r, g, b)
    self.filetype_color = dict(
        directory = (230, 255, 230),
        file = (255, 230, 230),
        # Examples for different filetypes
        # python = (252, 244, 3),
        # lua = (0, 0, 255)
    )

  </pre>

  </p>
</div>
