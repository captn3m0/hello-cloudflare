A public letter to Cloudflare to fix their snoopy vendor.

# What

For the last few years, various websites hosted on GitHub Pages and fronted using Cloudflare have been blocked in India due to Cloudflare relying on a upstream network provider with a misconfigured network (Airtel). The network flow looks like this:

`User -> Any ISP -> Cloudflare -> Airtel (Cloudflare peering partner) -> GitHub Pages`

If a website is using "Flexible SSL" or "No SSL" as configured on Cloudflare, the connection between Cloudflare and GitHub isn't encrypted, and Airtel blocks many such websites. Because Cloudflare terminates the TLS connection at their end, the browser shows a padlock, thus giving more authenticity to this incorrect block.

# Impact

These are just a few of the many websites blocked. This disproportionately impacts the developer community, and especially older websites that had a reason to use Cloudflare on top of GitHub Pages - TLS support. Now that GitHub Pages natively offers SSL, most of these websites can directly be hosted on GitHub Pages.

<details><summary>Here's a list of various such reports: (Click to expand)</summary>

Website | Reports
----------------------|----------------------
teachyourselfcs.com  | https://twitter.com/oznova_/status/1467957261221830657
neovim.io            | https://twitter.com/sanchayan_maity/status/1479131300040564737 https://github.com/neovim/neovim.github.io/issues/254
usebottles.com       | https://news.ycombinator.com/item?id=29358915 https://github.com/bottlesdevs/website/issues/12
thephpleague.com     | https://www.reddit.com/r/india/comments/r3bc78/hey_anyone_facing_issues_with_airtel/ https://github.com/thephpleague/thephpleague.github.io/issues/102
tldr.sh | https://www.reddit.com/r/developersIndia/comments/p3kxi4/why_are_some_nonporn_dev_related_websites_blocked/ https://github.com/tldr-pages/tldr/issues/7626
pennapps.com | https://twitter.com/skxrxn/status/1479520588955742209?s=20
termux.com | https://twitter.com/geekodour/status/1478963440412626946 https://github.com/termux/termux.github.io/issues/56
rsms.me | https://twitter.com/sahilk/status/1479489063874752512 https://twitter.com/sahilk/status/1441104954408587264
shantanugoel.com     | https://twitter.com/prohack/status/1422233887522975744 https://forum.internetfreedom.in/t/website-blocking-report-and-wynk-ads-shantanugoel-com/2318
codewithrockstar.com | https://github.com/RockstarLang/codewithrockstar.com/issues/11 https://news.ycombinator.com/item?id=29481644
web.mightyme.in      | https://stackoverflow.com/questions/70420313/getting-the-website-has-been-blocked-as-per-order-of-ministry-of-electronics-an
buyday.in        | https://stackoverflow.com/a/70426860
boxbilling.org | https://github.com/boxbilling/boxbilling/issues/1178 https://twitter.com/MichaelAnandR/status/1471935979787194373
Node-OS.com              | https://github.com/NodeOS/nodeos.github.io/issues/28
konvajs.com          | https://github.com/konvajs/konva/issues/1161
breaks.eu.org        | https://www.reddit.com/r/developersIndia/comments/rg4fqb/airtel_blocked_my_projects_website_please_help/
platesphp.com        | https://github.com/thephpleague/plates/issues/288 https://www.reddit.com/r/india/comments/r3bc78/hey_anyone_facing_issues_with_airtel/
coreui.io            | https://old.reddit.com/r/india/comments/p12qtq/why_did_govt_of_india_blocked_a_html_template/ https://github.com/coreui/coreui-website/issues/19
4fw.pw | https://github.com/captn3m0/hello-cloudflare/issues/2
mpp.su | https://github.com/captn3m0/hello-cloudflare/issues/2
about.hacktohell.org | https://twitter.com/hacktohell/status/1479484933785538562
one9x.org | https://twitter.com/Ramank775/status/1465979965002846209
kossiitkgp.org | https://twitter.com/OrkoHunter/status/1425089684535975937
orkohunter.net | https://twitter.com/OrkoHunter/status/1425089684535975937
treyhunner.com | https://twitter.com/abdulmuneer/status/1466289536833523714
wowjs.uk | https://twitter.com/rahulrrnair/status/1465629811368357888
akshatmittal.com | https://twitter.com/iakshatmittal/status/1479517378455040002
garudahacks.com | https://twitter.com/skxrxn/status/1479520588955742209?s=20
noflojs.org | https://github.com/noflo/noflo/issues/863
docs.pixelfed.org | https://github.com/pixelfed/docs/issues/80
nodered.org | https://community.cloudflare.com/t/website-blocked-for-some-users-in-india/300620
catalogue.nodered.org | https://community.cloudflare.com/t/website-blocked-for-some-users-in-india/300620
codeception.com | https://github.com/Codeception/codeception.github.com/issues/591
srijanshetty.in | https://twitter.com/srijanshetty/status/1468523289467179008
</details>
Several of these websites are critical to many developers, and none of these deserve to get blocked in India. Some of the above website are no longer blocked, because the website owner switched away from Flexible SSL to Strict SSL. However, this only happens when someone notices the block, debugs the issue correctly, and the website owner understands and fixes the issue. This is not a viable solution in this case.

There's [more reports on Twitter](https://twitter.com/search?q=blocked%20as%20per%20order%20of%20Ministry%20of%20Electronics%20and%20Information%20Technology).

# Call to Cloudflare

Hey @Cloudflare, please take care of this. Indian developers have been blocked out various critical websites because your upstream vendor (peering partner) has a misconfiguration. This has been going on for years, with no action or update at your end. 

Here's a few simple requests:

1. Get Airtel to fix the issue at their end.
2. Switch to a different upstream (peer) if that doesn't happen.
3. Publish a transparency report acknowledging the issue and confirming how many websites were incorrectly blocked without a court-order.
4. Notify Flexible SSL users that use GitHub Pages that their websites are getting blocked in India.

Flexible SSL is a decade-old product that has no place in the modern web. Users should get a big red warning when enabling such a product in today's times with free SSL certificates.

# Help, my website is blocked

If you got a report about your website being blocked in India, with a message that reads:

> The website has been blocked as per order of Ministry of Electronics and Information Technology under IT Act, 2000.

Here's what you can do:

1. Switch from Cloudflare to direct GitHub Pages, which supports TLS now.
2. Enable HTTPS on GitHub pages, and switch the upstream on Cloudflare to get strict SSL instead of flexible.

If you aren't using Cloudflare, please open an issue.

If you'd like to notify a site owner, please send them this link: https://github.com/captn3m0/hello-cloudflare/blob/main/README.md#help-my-website-is-blocked

# Help fight Censorship in India

If you'd like to support the fight to fix the state of Internet censorship in India, and bring more transparency on how it works, please [donate to the Internet Freedom Foundation](https://internetfreedom.in/donate/). You will need a valid Indian PAN Card.
