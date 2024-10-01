# [_pc-setup-manuals](./)

```cmd
cmd /c for /d %d in (*) do ( cd %d & for %f in (*.png *.jpg) do ( cd & md _trash & ffmpeg -i "%f" "%~nf.webp" & move "%f" _trash\ ) & cd .. ) 

cmd /c for %f in (*.webp) do ( cd & md jpg & ffmpeg -i "%f" "%~nf.jpg" & move "%~nf.jpg" jpg )
cmd /c for %f in (*.webp) do ( cd & md png & ffmpeg -i "%f" "%~nf.png" & move "%~nf.png" png )
cmd /c for %f in (*.webp) do ( cd & ffmpeg -i "%f" "%~nf.png" )
cmd /c for %f in (*.webp) do ( cd & ffmpeg -i "%f" -vcodec png -y "%~nf.png" & md webp & move "%f" webp & md png & move "%~nf.png" png )
cmd /c for %f in (*.png *.jpg) do ( cd & ffmpeg -i "%f" "%~nf.webp" & md _trash & move "%f" _trash )
cmd /c for %f in (*.gif *.mov) do ( cd & ffmpeg -i "%f" "%~nf.webm" & md _trash & move "%f" _trash )
cmd /c for %f in (*.mp4) do ( cd & ffmpeg -i "%f" "%~nf.webm" )
cmd /c for %f in (*.mov) do ( cd & ffmpeg -i "%f" "%~nf.mp4" )
```

```sh
#!/bin/sh
for i in *; do
    if [ -d "${i}" -a "${i}" != "_trash" ] ; then
        cd "${i}";
            pwd;

            ls *.jpg *.png
            for img in *.jpg *.png; do
                pwd;
                if [ ! -d _trash ] ; then mkdir _trash; fi;
                if [ -f "${img}" ] ; then
                    which ffmpeg && ffmpeg -i "${img}" -y "${img%.*}.webp" && mv "${img}" _trash/;
                    which ffmpeg && rename -v 's/.jpg.webp/.webp/g' *
                    which ffmpeg && rename -v 's/.png.webp/.webp/g' *
                fi
            done;

            ls *.gif
            for img in *.gif; do
                pwd;
                if [ ! -d _trash ] ; then mkdir _trash; fi;
                if [ -f "${img}" ] ; then
                    which ffmpeg && ffmpeg -i "${img}" -y "${img%.*}.webm" && mv "${img}" _trash/;
                    which ffmpeg && rename -v 's/.gif.webm/.webm/g' *
                fi
            done;

            rmdir * 2> /dev/null
            echo ''

            for ii in *; do
                if [ -d "${ii}" -a "${ii}" != "_trash" ] ; then
                    cd "${ii}"
                        pwd

                        ls *.jpg *.png
                        for img in *.jpg *.png; do
                            pwd;
                            if [ ! -d _trash ] ; then mkdir _trash; fi;
                            if [ -f "${img}" ] ; then
                                which ffmpeg && ffmpeg -i "${img}" -y "${img%.*}.webp" && mv "${img}" _trash/;
                                which ffmpeg && rename -v 's/.jpg.webp/.webp/g' *
                                which ffmpeg && rename -v 's/.png.webp/.webp/g' *
                            fi
                        done;

                        ls *.gif
                        for img in *.gif; do
                            pwd;
                            if [ ! -d _trash ] ; then mkdir _trash; fi;
                            if [ -f "${img}" ] ; then
                                which ffmpeg && ffmpeg -i "${img}" -y "${img%.*}.webm" && mv "${img}" _trash/;
                                which ffmpeg && rename -v 's/.gif.webm/.webm/g' *
                            fi
                        done;

                        rmdir * 2> /dev/null
                        echo ''

                        for iii in *; do
                            if [ -d "${iii}" -a "${iii}" != "_trash" ] ; then
                                cd "${iii}"
                                    pwd

                                    ls *.jpg *.png
                                    for img in *.jpg *.png; do
                                        pwd;
                                        if [ ! -d _trash ] ; then mkdir _trash; fi;
                                        if [ -f "${img}" ] ; then
                                            which ffmpeg && ffmpeg -i "${img}" -y "${img%.*}.webp" && mv "${img}" _trash/;
                                            which ffmpeg && rename -v 's/.jpg.webp/.webp/g' *
                                            which ffmpeg && rename -v 's/.png.webp/.webp/g' *
                                        fi
                                    done
                                    ls *.gif
                                    for img in *.gif; do
                                        pwd;
                                        if [ ! -d _trash ] ; then mkdir _trash; fi;
                                        if [ -f "${img}" ] ; then
                                            which ffmpeg && ffmpeg -i "${img}" -y "${img%.*}.webm" && mv "${img}" _trash/;
                                            which ffmpeg && rename -v 's/.gif.webm/.webm/g' *
                                        fi
                                    done

                                    rmdir * 2> /dev/null
                                    echo ''
                                cd ..
                            fi
                        done
                    cd ..
                fi
            done
            rmdir * 2> /dev/null
        cd ..;
        rmdir * 2> /dev/null
    fi;
done;

```
