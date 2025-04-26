# Copier un dossier dans Google Drive avec `rclone` (sans vidéos)

## 1. Lister les répertoires de la racine du drive

```bash
rclone lsd drive:

2. Lister les sous-répertoires de Master_Cnam

rclone lsd drive:Master_Cnam

3. Créer un nouveau dossier sur le drive

rclone mkdir "drive:Master_Cnam/STA101-Analyse des données méthodes descriptives"

4. Identifier les plus gros fichiers hors vidéos en local

find ./ -type f ! \( -name "*.mp4" -o -name "*.avi" -o -name "*.mkv" -o -name "*.mov" \) -exec du -ah {} + | sort -rh | head -n 10

5. Faire un test de copie sans vidéos (simulation)

rclone copy ~/Master_Cnam/STA101-Analyse\ des\ données\ méthodes\ descriptives/ "drive:Master_Cnam/STA101-Analyse des données méthodes descriptives/" --progress --exclude "*.{mp4,avi,mov}" --dry-run

6. Lancer la copie réelle sans vidéos

rclone copy ~/Master_Cnam/STA101-Analyse\ des\ données\ méthodes\ descriptives/ "drive:Master_Cnam/STA101-Analyse des données méthodes descriptives/" --progress --exclude "*.{mp4,avi,mov}"
