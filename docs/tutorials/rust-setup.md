# **Setting up Development Container for Rust**

* Primary author : [Thomas Roche](https://thomas092101)
* Reviewer: [David Ona](https://github.com/david-ona)

## **Requirements**

* [Docker](https://www.docker.com/products/docker-desktop/) for creating and managing containers
* [Visual Studio Code](https://code.visualstudio.com/) with Microsoft Dev Container extension installed

### **Creating a new project**

* Initialize and enter new Git Repository  
> **mkdir comp423-rust-tutorial**  
> **cd comp423-rust-tutorial**  
> **git init**  

* Create and Configure Dev Container  
    + First, we will want to create a <code>.devcontainer</code> directory in the root of your project.  Inside this directory we will
    add a new file <code>.devcontainer/devcontainer.json</code>  
    > **mkdir devcontainer**  
    > **git add devcontainer.json**  

    + Next, we want to configure the Dev Container before launching it. We will be making some changes to the file you just created. 

    The <code>devcontainer.json</code> file defines the configurations for the development environment.  Here, we're specifying: 

    + **name**: Descriptive name for your container  
    + **image**: A base image of the container from Microsoft  
    + **extensions**: For this parameter, we should add the <code>rust-analyzer</code> VSCode plugin  
    + **version**: Here we want the container to, at startup, show that it is running a recent version of Rust.  We achieve this with the <code>rustc --version</code> command  


<div class="language-json highlight"><pre id="__code_5"><span></span><button class="md-clipboard md-icon" title="Copy to clipboard" data-clipboard-target="#__code_5 > code"></button><code class="md-code__content"><span id="__span-5-1"><a id="__codelineno-5-1" name="__codelineno-5-1" href="https://comp423-25s.github.io/resources/MkDocs/tutorial/#__codelineno-5-1"></a><span class="p">{</span>
</span><span id="__span-5-2"><a id="__codelineno-5-2" name="__codelineno-5-2" href="https://comp423-25s.github.io/resources/MkDocs/tutorial/#__codelineno-5-2"></a><span class="w">  </span><span class="nt">"name"</span><span class="p">:</span><span class="w"> </span><span class="s2">"COMP423 Rust Tutorial"</span><span class="p">,</span>
</span><span id="__span-5-3"><a id="__codelineno-5-3" name="__codelineno-5-3" href="https://comp423-25s.github.io/resources/MkDocs/tutorial/#__codelineno-5-3"></a><span class="w">  </span><span class="nt">"image"</span><span class="p">:</span><span class="w"> </span><span class="s2">"mcr.microsoft.com/devcontainers/rust:1"</span><span class="p">,</span>
</span><span id="__span-5-4"><a id="__codelineno-5-4" name="__codelineno-5-4" href="https://comp423-25s.github.io/resources/MkDocs/tutorial/#__codelineno-5-4"></a><span class="w">  </span><span class="nt">"customizations"</span><span class="p">:</span><span class="w"> </span><span class="p">{</span>
</span><span id="__span-5-5"><a id="__codelineno-5-5" name="__codelineno-5-5" href="https://comp423-25s.github.io/resources/MkDocs/tutorial/#__codelineno-5-5"></a><span class="w">    </span><span class="nt">"vscode"</span><span class="p">:</span><span class="w"> </span><span class="p">{</span>
</span><span id="__span-5-6"><a id="__codelineno-5-6" name="__codelineno-5-6" href="https://comp423-25s.github.io/resources/MkDocs/tutorial/#__codelineno-5-6"></a><span class="w">      </span><span class="nt">"settings"</span><span class="p">:</span><span class="w"> </span><span class="p">{},</span>
</span><span id="__span-5-7"><a id="__codelineno-5-7" name="__codelineno-5-7" href="https://comp423-25s.github.io/resources/MkDocs/tutorial/#__codelineno-5-7"></a><span class="w">      </span><span class="nt">"extensions"</span><span class="p">:</span><span class="w"> </span><span class="p">[</span><span class="s2">"rust-lang.rust-analyzer"</span><span class="p">]</span>
</span><span id="__span-5-8"><a id="__codelineno-5-8" name="__codelineno-5-8" href="https://comp423-25s.github.io/resources/MkDocs/tutorial/#__codelineno-5-8"></a><span class="w">    </span><span class="p">}</span>
</span><span id="__span-5-9"><a id="__codelineno-5-9" name="__codelineno-5-9" href="https://comp423-25s.github.io/resources/MkDocs/tutorial/#__codelineno-5-9"></a><span class="w">  </span><span class="p">},</span>
</span><span id="__span-5-10"><a id="__codelineno-5-10" name="__codelineno-5-10" href="https://comp423-25s.github.io/resources/MkDocs/tutorial/#__codelineno-5-10"></a><span class="w">  </span><span class="nt">"postCreateCommand"</span><span class="p">:</span><span class="w"> </span><span class="s2">"rustup update && rustc --version"</span>
</span><span id="__span-5-11"><a id="__codelineno-5-11" name="__codelineno-5-11" href="https://comp423-25s.github.io/resources/MkDocs/tutorial/#__codelineno-5-11"></a><span class="p">}</span>
</span></code></pre></div>
