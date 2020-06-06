# erc_handbook

You can find detailed theme instructions in the Docsy user guide: https://docsy.dev/docs/

**Just, install go and hugo as mentioned in the documentation of docsy.**


## Cloning the repo:
Clone the repo using: 
```bash
git clone https://github.com/ERC-BPGC/erc_handbook.git
git submodule update --init --recursive
git submodule update --remote --merge
```

## Running the website locally:
Once you've cloned the site repo, from the repo root folder, run:
```bash
hugo server
```

## Build the website 

Since all of use are working with ROS, using npm (Node Package Manager) is not suggested (npm breaks ROS). Instead install yarn which is another node-js package manager.

-------------------------------
#### Install Yarn (package manager for web applications)
- Install yarn: https://classic.yarnpkg.com/en/docs/install/#debian-stable
- Setup Path: https://github.com/yarnpkg/yarn/issues/5156
--------------------------

```bash
yarn add postcss
```
This will install `postcss` on your laptop. 


To build the website use:
```
hugo
```
This will generate source in the public folder. Put that source in the handbook repo. 



### TO DO:
- Add submodule in this repo to the handbook repo.