## Adding cli-debrid to existing instance of plex,zurg,rclone on unraid

## Download cli_debrid from app store in unraid
- click install - use dev version to install
- in settings --> fill according the picture 

<img width="787" alt="Screenshot 2025-05-19 at 16 37 40" src="https://github.com/user-attachments/assets/5db5ff71-d138-4434-b9e4-2bf938741b04" />

<img width="720" alt="image" src="https://github.com/user-attachments/assets/99928a70-1946-4eef-837b-b97299d18629" />

- in the field Mount: u fill the path to the folder where your *__all__*, Movies, Shows are ... so whenever your rclone mount your rd content on you host machine... 

- or where do you have your plex libraries pointed to ... for me its /mnt/user/appdata/remoteshit/ in here i have the __all__, Movies, Shows .... 

- once done and docker container is up, Open onboarding via browser **http://your-server-ip:5000**

## Wizzard should open

- Enable **Phalanx**
- Login: `admin / admin`
- Cpmfigure new admin if u want ....
- 
- Configure:
  - File collection: **Plex**
  - click authorize PLEX - YOU WILL GET OVERLAY WINDOW - work there - select server-next-next ...
  - Real-Debrid API key get your key and paste it there
  - Trakt client ID & secret - go accroding the wizzard

Authorize Trakt via: [https://trakt.tv/activate](https://trakt.tv/activate)

## Add Scraper

- Select **Torrentio** (even if Jackett selected earlier)
- Click **Add Scraper**

- open up https://torrentio.strem.fun/configure
- select your preferences
- when done right click on install amd copy the output you get somewhere you can edit it ..

- final should look like this
   ```providers=yts,eztv,rarbg,1337x,thepiratebay,kickasstorrents,torrentgalaxy,magnetdl,horriblesubs,nyaasi,tokyotosho,anidex,ilcorsaronero,mejortorrent,wolfmax4k,cinecalidad|language=italian,spanish,german```

- next 

- Configure resolution settings (e.g., split 1080p and 4K)
- Add overseerr as content source using URL and API key
- access overseerr via browser, to get your api, go through the first time wizard if you have to...
- Skip extras and **Finish Setup**

## Helpful Links

- [Overseerr Webhooks](https://github.com/godver3/cli_debrid/wiki/Webhooks#overseerr)
- [Zurg Webhooks](https://github.com/godver3/cli_debrid/wiki/Webhooks#zurg)
- [GitHub](https://github.com/godver3/cli_debrid)
- [Wiki](https://github.com/godver3/cli_debrid/wiki)
- [Discord](https://discord.gg/ynqnXGJ4hU)

## Final CLI Settings


- Add Jellyfin URL + Token under **Debug Tab**
- Toggle **Organize by Resolution**
- Click **Start Program**

## Test Scraping

- Add 1080p & 4K movies and TV shows
- Check **Main → Queue** and **Home**
- Verify files in your server’s symlink folders


## optional - Add Jackett Scraper

- Visit: `http://<your-server-ip>:9117`
- Set admin password
- Enter FlareSolverr API: `http://<your-server-ip>:8191`
- Add indexers (e.g., 1337x)
- Copy Jackett API Key

Back to CLI UI:
- Go to: `Settings → Scrapers → Add New`
- Select **Jackett**, input API Key & URL
- Enable it

## optional - Backup Your Setup

```bash
sudo curl -sO https://raw.githubusercontent.com/delete2020/cli_debrid-setup-/main/setup.sh && \
sudo chmod +x setup.sh && \
sudo ./setup.sh
```

Choose Option **3** – You’ll get a `.tar.gz` backup of your config.
