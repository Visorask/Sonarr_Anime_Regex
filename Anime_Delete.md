# To delete extra files

If you have issues with sonarr picking up a bunch of:

```bash
NCED
NCOP
Music Videos
OP's
```

Then I have a solution that will delete these files and get rid of them and not have to worry about them cluttering up your Auto or Manual import process.

In the repo there is a file called `anime_delete` and it will remove all of these files for you through a custom connection to sonarr.

Place this file inside whatever directory you would like and that sonarr has access to.
*Keep in mind if you use docker you will have to put it somewhere the docker container has a volume for*

1. Copy the contents of the script into whatever filepath sonarr has access to. I chose `/config/app/`
2. `nano anime_delete`
3. Edit the `location="/your/path/here"` and make sure it's in quotes.
2. Then save it and `chmod +x anime_delete`
3. In Sonarr go to `Settings-> Connect-> + Symbol -> Custom Script`
4. Change `Name` to whatever you like.
5. Select `On Grab` and `On Import`.
6. Click the Folder icon or type in the path to the script you chose earlier.

[Example Image](images/CustomScript.png)

Now when you download or import any files the script will run and clear out those files that you most likely won't use and if you want them well this script isn't for you.