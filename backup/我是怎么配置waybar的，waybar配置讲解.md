首先看一下俺配置好后的效果
<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/223c07bf-b3d3-4c84-9119-ff5c3e6fda00" />
那么我们要配置waybar就要先得到它的配置文件，它的默认配置文件在/etc/xdg/waybar/下，我们需要把它复制到.config/waybar下，如果没有就使用mkdir创建一个,然后再复制
`cp /etc/xdg/waybar/* .config/waybar`
我们使用ls命令会发现有两个文件：config.jsonc和style.css，这两个一个是设置模块和其他，一个是设置样式的
如果你不想配置，那么你可以克隆我的配置：https://github.com/Aidens-fox/archlinuxinstall-swaywmConfiguration
我们打开config.jsonc
````
// -*- mode: jsonc -*-
{
    // "layer": "top", // Waybar at top layer
     "position": "bottom", // 显示位置
    "height": 25, // 显示大小
    // "width": 1280, // 导航栏宽度
    "spacing": 4, // 模块间距
    // 选择模块顺序
    "modules-left": [
	"idle_inhibitor",
	"disk",
        "sway/workspaces",
        "sway/mode",
        "sway/scratchpad",
        "custom/media"
    ],
    "modules-right": [
        "pulseaudio",
        "network",
        "power-profiles-daemon",
        "cpu",
        "memory",
        "temperature",
        "backlight",
        "keyboard-state",
        "battery",
        "battery#bat2",
        "clock",
        "tray",
    ],
    // 模块配置
//     "sway/workspaces": {
  //       "disable-scroll": true,
    //     "all-outputs": true,
      //   "warp-on-scroll": false,
        // "format": "{name}: {icon}",
  //       "format-icons": {
    //         "1": "",
      //       "2": "",
        //     "3": "",
      //       "4": "",
        //     "5": "",
	  //   "6": "󱂬",
	//     "7": "󰹑",
           //  "urgent": "",
        //     "focused": "",
      //       "default": ""
    //     }
  //   },


       "disk":{
			"format": "󰋊  {percentage_free}%",
	},

    "keyboard-state": {
        "numlock": true,
        "capslock": true,
        "format": "{name} {icon}",
        "format-icons": {
            "locked": "",
            "unlocked": ""
        }
    },
    "sway/mode": {
        "format": "<span style=\"italic\">{}</span>"
    },
    "sway/scratchpad": {
        "format": "{icon} {count}",
        "show-empty": false,
        "format-icons": ["", ""],
        "tooltip": true,
        "tooltip-format": "{app}: {title}"
    },
    "mpd": {
        "format": "{stateIcon} {consumeIcon}{randomIcon}{repeatIcon}{singleIcon}{artist} - {album} - {title} ({elapsedTime:%M:%S}/{totalTime:%M:%S}) ⸨{songPosition}|{queueLength}⸩ {volume}% ",
        "format-disconnected": "Disconnected ",
        "format-stopped": "{consumeIcon}{randomIcon}{repeatIcon}{singleIcon}Stopped ",
        "unknown-tag": "N/A",
        "interval": 5,
        "consume-icons": {
            "on": " "
        },
        "random-icons": {
            "off": "<span color=\"#f53c3c\"></span> ",
            "on": " "
        },
        "repeat-icons": {
            "on": " "
        },
        "single-icons": {
            "on": "1 "
        },
        "state-icons": {
            "paused": "",
            "playing": ""
        },
        "tooltip-format": "MPD (connected)",
        "tooltip-format-disconnected": "MPD (disconnected)"
    },
    "idle_inhibitor": {
        "format": "{icon}",
        "format-icons": {
            "activated": "",
            "deactivated": ""
        }
    },
    "tray": {
        // "icon-size": 21,
        "spacing": 10,
        // "icons": {
        //   "blueman": "bluetooth",
        //   "TelegramDesktop": "$HOME/.local/share/icons/hicolor/16x16/apps/telegram.png"
        // }
    },
    "clock": {
        // "timezone": "America/New_York",
        "tooltip-format": "<big>{:%Y %B}</big>\n<tt><small>{calendar}</small></tt>",
        "format-alt": "{:%Y-%m-%d}"
    },
    "cpu": {
	 "format": "{usage}% ",
        "tooltip": false
    },
    "memory": {
        "format": "{}% "
    },
    "temperature": {
        // "thermal-zone": 2,
        // "hwmon-path": "/sys/class/hwmon/hwmon2/temp1_input",
        "critical-threshold": 80,
        // "format-critical": "{temperatureC}°C {icon}",
        "format": "{temperatureC}°C {icon}",
        "format-icons": [""]
    },
    "backlight": {
        // "device": "acpi_video1",
        "format": "{percent}% {icon}",
        "format-icons": ["", "", "", "", "", "", "", "", ""]
    },
    "battery": {
        "states": {
            // "good": 95,
            "warning": 30,
            "critical": 15
        },
        "format": "{capacity}% {icon}",
        "format-full": "{capacity}% {icon} ",
        "format-charging": "{capacity}% ",
        "format-plugged": "{capacity}% ",
        "format-alt": "{time} {icon}",
        // "format-good": "", // An empty format will hide the module
        // "format-full": "",
        "format-icons": ["", "", "", "", ""]
    },
    "battery#bat2": {
        "bat": "BAT2"
    },
    "power-profiles-daemon": {
      "format": "{icon}",
      "tooltip-format": "Power profile: {profile}\nDriver: {driver}",
      "tooltip": true,
      "format-icons": {
        "default": " ",
        "performance": " ",
        "balanced": " ",
        "power-saver": " "
      }
    },
    "network": {
        // "interface": "wlp2*", // (Optional) To force the use of this interface
        "format-wifi": "{essid} ({signalStrength}%) ",
        "format-ethernet": "{ipaddr}/{cidr} ",
        "tooltip-format": "{ifname} via {gwaddr} ",
        "format-linked": "{ifname} (No IP) ",
        "format-disconnected": "Disconnected ⚠",
        "format-alt": "{ifname}: {ipaddr}/{cidr}"
    },
    "pulseaudio": {
        // "scroll-step": 1, // %, can be a float
        "format": "{volume}% {icon} {format_source}",
        "format-bluetooth": "{volume}% {icon} {format_source}",
        "format-bluetooth-muted": " {icon} {format_source}",
        "format-muted": " {format_source}",
        "format-source": "{volume}% ",
        "format-source-muted": "",
        "format-icons": {
            "headphone": "",
            "hands-free": "",
            "headset": "",
            "phone": "",
            "portable": "",
            "car": "",
            "default": ["", "", ""]
        },
        "on-click": "pavucontrol"
    },
    "custom/media": {
        "format": "{icon} {text}",
        "return-type": "json",
        "max-length": 40,
        "format-icons": {
            "spotify": "",
            "default": "🎜"
        },
        "escape": true,
        "exec": "$HOME/.config/waybar/mediaplayer.py 2> /dev/null" // Script in resources folder
        // "exec": "$HOME/.config/waybar/mediaplayer.py --player spotify 2> /dev/null" // Filter player based on name
    },
    "custom/power": {
        "format" : "⏻ ",
		"tooltip": false,
		"menu": "on-click",
		"menu-file": "$HOME/.config/waybar/power_menu.xml", // Menu file in resources folder
		"menu-actions": {
			"shutdown": "shutdown",
			"reboot": "reboot",
			"suspend": "systemctl suspend",
			"hibernate": "systemctl hibernate"
		}
    }
}

````

     

      如果你不想配置，那么你可以克隆我的配置：https://github.com/Aidens-fox/archlinuxinstall-swaywmConfiguration
我们再讲讲style.css，这个主要是把颜色给统一了

(-: