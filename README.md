##################################################################################
## Conky by http://jameshardy88.deviantart.com/art/Conky-JamesHardy88-122466724 ##
##		    Modified by Umair - http://www.NoobsLab.com    		##
##################################################################################
# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window false
background true
own_window_transparent yes
own_window_type conky
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 160 0
#maximum_width 200

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline 1

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 5

# border width
border_width 1

# Default colors and also border colors
default_color ffffff
#default_shade_color ffffff
#default_outline_color 00000f
#own_window_colour ffffff

# Text alignment, other possible values are commented
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 15
gap_y 20

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 1

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none

TEXT
#${if_running rhythmbox}
#${font j.d.:size=10}${color3}${execi 5 lyricsdownloader -t 35 | fold -sw25}
#${else}

SYSTEM ${hr 2}
${voffset 2}${font OpenLogos:size=16}u${font}   Kernel:  ${alignr}${kernel}
${font StyleBats:size=16}A${font}   CPU: ${cpu}% ${alignr}${cpubar cpu0 8,60}
${font StyleBats:size=16}g${font}   RAM: $memperc% ${alignr}${membar 8,60}
${font StyleBats:size=16}j${font}   SWAP: $swapperc% ${alignr}${swapbar 8,60}
${font Webdings:size=16}~${font}  Battery: ${battery_percent BAT1}% ${alignr}${battery_bar 8,60 BAT1}
${font StyleBats:size=16}q${font}   Uptime: ${alignr}${uptime}
${font StyleBats:size=16}k${font}   Processes: ${alignr}$processes ($running_processes running)

Highest CPU $alignr CPU% MEM%
${hr 1}
${top name 1}$alignr${top cpu 1}${top mem 1}
${top name 2}$alignr${top cpu 2}${top mem 2}
${top name 3}$alignr${top cpu 3}${top mem 3}

HD ${hr 2}
${font Pie charts for maps:size=14}7${font}   ${voffset -5}Home:
${voffset 4}${fs_free /home}/${fs_size /home} ${alignr}${fs_bar 8,60 /home}

NETWORK ${hr 2}
${if_existing /proc/net/route wlp3s0}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed wlp3s0} kb/s ${alignr}${upspeedgraph wlp3s0 8,60}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed wlp3s0} kb/s ${alignr}${downspeedgraph wlp3s0 8,60}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup wlp3s0}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown wlp3s0}
${voffset 4}${font PizzaDude Bullets:size=14}Z${font}   Signal: ${wireless_link_qual wlp3s0}% ${alignr}${wireless_link_bar 8,60 wlp3s0}
#${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr wlp3s0}
#${voffset 4}${font PizzaDude Bullets:size=14}b${font}   Public Ip: ${alignr}${execi 1 ~/.conky/scripts/ip.sh}
${else}${if_existing /proc/net/route enp2s0}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed enp2s0} kb/s ${alignr}${upspeedgraph enp2s0 8,60}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed enp2s0} kb/s ${alignr}${downspeedgraph enp2s0 8,60}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup enp2s0}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown enp2s0}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr enp2s0}
${voffset 4}${font PizzaDude Bullets:size=14}b${font}   Public Ip: ${alignr}${execi 1 ~/.conky/scripts/ip.sh}
${endif}${else}${if_existing /proc/net/route eth1}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed eth1} kb/s ${alignr}${upspeedgraph eth1 8,60}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed eth1} kb/s ${alignr}${downspeedgraph eth1 8,60}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup eth1}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown eth1}
#${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr eth1}
#${voffset 4}${font PizzaDude Bullets:size=14}b${font}   Public Ip: ${alignr}${execi 1 ~/.conky/scripts/ip.sh}
${endif}${else}
${font PizzaDude Bullets:size=14}4${font}   Network Unavailable
${endif}
${endif}

SHORTCUT (i3) ${hr 2}
${voffset 4}${font PizzaDude Bullets:size=14}${font}   mod+Return - Terminal
${voffset 4}${font PizzaDude Bullets:size=14}${font}   mod+F1 - Chrome
${voffset 4}${font PizzaDude Bullets:size=14}${font}   mod+F2 - Thunar
${voffset 4}${font PizzaDude Bullets:size=14}${font}   mod+F3 - Rhythmbox
${voffset 4}${font PizzaDude Bullets:size=14}${font}   mod+F4 - TaskManager
${voffset 4}${font PizzaDude Bullets:size=14}${font}   mod+F5 - Steam
