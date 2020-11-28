# Re-Former

Created as part of the Odin Project Curriculum.

###### A note on node_modules

11/28/20 - I noticed with Rails 6 all my projects had a roughly 70mb `node_modules` folder that I wanted to get rid of since I'm not using any Javascript in my projects at this point. I used this project to experiment with cleaning up space, since I didn't really care about it.

Dragging `node_modules` to the trash certainly does the trick, but I can no longer run the rails server. The damage is not permanent since `$ yarn install` will reinstall dependencies based on the `package.json` file, as explained in the [documentation](https://classic.yarnpkg.com/en/docs/cli/install).

I tried `$ yarn autoclean` (explained [here](https://classic.yarnpkg.com/en/docs/cli/autoclean)), but that only saved 12mb. I didn't change what was created by default in the `.yarnclean` file, however — if I had manually added more perhaps this option would have worked better. (Just a matter of knowing what to add.)

Finally, I tried simply deleting `"@rails/actioncable": "^6.0.0"`, `"@rails/webpacker": "4.3.0"` and `"turbolinks": "^5.2.0"` from the list of `"dependencies"` and `"webpack-dev-server": "^3.11.0"`from the list of `"devDependencies"` in `package.json`, then ran `$ yarn install` again. This brought the directory size down to < 1mb, so was fairly successful. I don't know exactly what functionality I broke by deleting these dependencies, but I didn't think I was using any of it. I think the only Javascript I have used in my Rails projects so far has been what has come automatically with `Devise`. Perhaps this process would have broken something in my projects that used `Devise`.