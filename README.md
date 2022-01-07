A public letter to CloudFlare to fix their snoopy vendor.

# What

For the last few years, various websites hosted on GitHub Pages and fronted using CloudFlare have been blocked in India due to CloudFlare relying on a upstream network provider with a misconfigured network (Airtel). The network flow looks like this:

`User->CloudFlare->Airtel->GitHub Pages`

If a website is using "Flexible SSL" or "No SSL" as configured on CloudFlare, the connection between CloudFlare and GitHub isn't encrypted, and Airtel blocks many such websites. Because CloudFlare terminates the TLS connection at their end, the browser shows a padlock, thus giving more authenticity to this incorrect block.

# Impact

These are just a few of the many websites blocked. This disproportionately impacts the developer community, and especially older websites that had a reason to use CloudFlare on top of GitHub Pages - TLS support. Now that GitHub Pages natively offers SSL, most of these websites can directly be hosted on GitHub Pages.

Here's a list of various such reports:

| Website              | Reports                                                                                                                                                | Notes        |
|----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|--------------|
| shantanugoel.com     | https://twitter.com/prohack/status/1422233887522975744 https://forum.internetfreedom.in/t/website-blocking-report-and-wynk-ads-shantanugoel-com/2318   | Now resolved |
| teachyourselfcs.com  | https://twitter.com/oznova_/status/1467957261221830657                                                                                                 | Now resolved |
| codewithrockstar.com | https://github.com/RockstarLang/codewithrockstar.com/issues/11 https://news.ycombinator.com/item?id=29481644                                           | Now resolved |
| neovim.io            | https://twitter.com/sanchayan_maity/status/1479131300040564737 https://github.com/neovim/neovim.github.io/issues/254                                   | Not Resolved |
| web.mightyme.in      | https://stackoverflow.com/questions/70420313/getting-the-website-has-been-blocked-as-per-order-of-ministry-of-electronics-an                           |              |
| buyday.in        | https://stackoverflow.com/a/70426860                                                                                                                   |              |
| usebottles.com       | https://news.ycombinator.com/item?id=29358915 https://github.com/bottlesdevs/website/issues/12                                                         | Not Resolved |
| Node-OS.com              | https://github.com/NodeOS/nodeos.github.io/issues/28                                                                                                   | Not Resolved |
| konvajs.com          | https://github.com/konvajs/konva/issues/1161                                                                                                           | Not Resolved |
| breaks.eu.org        | https://www.reddit.com/r/developersIndia/comments/rg4fqb/airtel_blocked_my_projects_website_please_help/                                               | Resolved     |
| platesphp.com        | https://github.com/thephpleague/plates/issues/288 https://www.reddit.com/r/india/comments/r3bc78/hey_anyone_facing_issues_with_airtel/                 | Not Resolved |
| thephpleague.com     | https://www.reddit.com/r/india/comments/r3bc78/hey_anyone_facing_issues_with_airtel/ https://github.com/thephpleague/thephpleague.github.io/issues/102 | Not Resolved |
| coreui.io            | https://old.reddit.com/r/india/comments/p12qtq/why_did_govt_of_india_blocked_a_html_template/ https://github.com/coreui/coreui-website/issues/19       |              |
| tldr.sh | https://www.reddit.com/r/developersIndia/comments/p3kxi4/why_are_some_nonporn_dev_related_websites_blocked/ https://github.com/tldr-pages/tldr/issues/7626 |
| 4fw.pw | https://github.com/captn3m0/hello-cloudflare/issues/2 | 
| mpp.su | https://github.com/captn3m0/hello-cloudflare/issues/2 |

Several of these websites are critical to many developers, and none of these deserve to get blocked in India.

There's [lots more reports on Twitter](https://twitter.com/search?q=blocked%20as%20per%20order%20of%20Ministry%20of%20Electronics%20and%20Information%20Technology).

# Help, my website is blocked

If you got a report about your website being blocked in India, with a message that reads:

>The website has been blocked as per order of Ministry of Electronics and Information Technology under IT Act, 2000.

Here's what you can do:

1. Switch from CloudFlare to direct GitHub Pages, which supports TLS now.
2. Enable HTTPS on GitHub pages, and switch the upstream on CloudFlare to get strict SSL instead of flexible.

If you aren't using CloudFlare, please open an issue.

# Call to CloudFlare

Hey @CloudFlare, please take care of this. Indian developers have been blocked out various critical websites because your upstream vendor has a misconfiguration. This has been going on for years, with no action or update at your end. 

Here's a few simple requests:

1. Get Airtel to fix the issue at their end.
2. Switch to a different upstream if that doesn't happen.
3. Publish a transparency report acknowledging the issue and confirming how many websites were incorrectly blocked without a court-order.
4. Notify Flexible SSL users that use GitHub Pages that their websites are getting blocked in India.

Flexible SSL is a decade-old product that has no place in the modern web. Users should get a big red warning when enabling such a product in today's times with free SSL certificates.

# Help fight Censorship in India

If you'd like to support the fight to fix the state of internet censorship in India, and bring more transparency to how it works, please [Donate to the Internet Freedom Foundation](https://internetfreedom.in/donate/). You will need a valid Indian PAN Card.
