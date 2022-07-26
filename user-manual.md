# User Manual



Please make sure you are familiar with the content guidelines and are aware of what is public content in the community. You can find more detail in [Content and Moderation](content-and-moderation-policy.md). This document does not cover everything in the #rules, #faq, #announcements, #status channels, so make sure you check those out!

That said, enjoy creating beautiful images! In this page:

* [User Manual](user-manual.md#user-manual)
  * [Basic Commands in Bot Channels](user-manual.md#basic-commands-in-bot-channels)
  * [Parameters to "/imagine"](user-manual.md#parameters-to-imagine)
  * [Stylize Values](user-manual.md#stylize-values)
  * [Quality Values](user-manual.md#undefined)
  * [Emoji Reactions to Generation Output](user-manual.md#emoji-reactions-to-generation-output)
  * [Image Prompting with URL](user-manual.md#image-prompting-with-url)
  * [Advanced Text Weights](user-manual.md#advanced-text-weights)
  * [Prompt Preferences and Settings](user-manual.md#prompt-preferences-and-settings)
  * [Deprecated: May Want To Avoid](user-manual.md#deprecated-may-want-to-avoid)

### Basic Commands in Bot Channels

Commands are functions of the Midjourney bot that can be typed in any bot channel or thread under a bot channel. A bot channel is a channel under the "Image Generation" section on the Discord server.

`/imagine` Creates an image from text (4 images in 50 seconds)

`/info` Shows information about your profile and plan and usage.

`/invite` Generates an invite link and send it to your DM that you can send someone to join the server. It will give them some job time to try out the bot. You do not need to provide their name or address, you will give them the link it generates.

`/ideas` Give some random ideas for prompt

`/help` Displays bot options for handy reference

`/subscribe` Get a link to the subscription page

`/settings` View and edit your personal settings

`/show` You can now use the `/show <jobid>` command to produce the resulting image and upscale+variation buttons, based on a job id. This allows you to take a job into a different channel, upscale a job from an archived thread, or other similar situations (like being moved from a newbies channel).

You can find more documentation on using these in our [FAQs](FAQs.md).

### Parameters to "/imagine"

Parameters are "inputs" to the command.  Some are required, like a prompt, others are optional and will change how the prompt is interpreted and the image is created.

For instance, a full imagine command might contain several things, like an image URL, some weights, other switches:

`/imagine prompt: http://myimageonline.jpg A forest spirit at night --iw 0.2 --no trees --hd`

Below are some of the "switches" you can add at the end of the command, using the "--" delimiter.

`--w` Width of image. Works better as multiple of 64 (or 128 for `--hd`)

`--h` Height of image. Works better as multiple of 64 (or 128 for `--hd`)

`--seed` Sets the random seed, which can sometimes help keep things more steady / reproducible between generations. Any positive integer (e.g., 2, 534, 345554).

`--no` Negative prompting (`--no plants` would try to remove plants)

`--video` Saves a progress video, which is sent to you in the ✉️-triggered DM (you must react with the envelope to get the video link)

`--iw` Sets image prompt weight relative to text weight. Default is 0.25.&#x20;

`--fast` Faster images, less consistency

`--version <1 or 2>` or `--v <1 or 2>`  Uses old algorithms 1 (which was formerly the "vibe" option, sometimes better for macro or textures) or 2, the last improvement.  We are at 3 now, which you do not need to specify.  So specify `--version 2` to use the previous older model, or `--version 1` for the one before.

`--stylize <number>`, or `--s <number>` The stylize argument sets how strong of a 'stylization' your images have, the higher you set it, the more opinionated it will be. Default number is 2500. [See below](user-manual.md#stylize-values) for more info.

`--quality <number>` , or `--q <number>` How much rendering quality time you want to spend. Default number is 1. Higher values cost more, [see below](user-manual.md#quality-values).

`--hd` Uses a different algorithm that’s potentially better for larger images, but with less consistent composition. Best for abstract and landscape prompts.

`--stop` Stop the generation at an earlier percentage. Must be between 10-100

`--uplight` Use "light" upscaler for subsequent upscales. Results are then closer to the original image (less detail added during upscale)

`--sameseed` Sets the same seed across all images of the resulting grid

`--aspect` Sets a desired aspect ratio, instead of manually setting height and width with `--h` and `--w`. Try `--aspect 16:9` for example, to get a 16:9 aspect ratio (\~448x256). (Shortcut `--ar`.)

**Size shortcuts**

These are synonyms for longer commands.  In other words, using `--wallpaper` is the same as saying   `--w 1920 --h 1024 --hd`.

`--wallpaper`: `--w 1920 --h 1024 --hd`

`--sl`: `--w 320 --h 256`

`--ml`: `--w 448 --h 320`

`--ll`: `--w 768 --h 512 --hd`

`--sp`: `--w 256 --h 320`

`--mp`: `--w 320 --h 448`

`--lp`: `--w 512 --h 768 --hd`

You can see an illustrated guide to all these parameters on [this page](imagine-parameters.md).  You can read more about image sizes and how to interpret them on [Understanding Image Size](resource-links/understanding-image-size.md).

### Stylize Values

These can all be used with the shortcut version `--s` instead.

`--stylize 625` If you basically want to turn it off and be less artistic.

`--stylize 1250` Good for when you want it to be 'less strict' but still 'pretty' (this is probably recommended for skilled users).

`--stylize 2500` The **default value**, so you don't have to specify this.

`--stylize 20000` If you want it to 'take over' and start drifting from your text, but not go crazy.&#x20;

`--stylize 60000` Hands off the wheels, who knows what will happen. It may look nothing like your prompt.

### Quality Values

The shortcut version is `--q`.

`--quality 0.25` Rough results, 4x faster / cheaper.&#x20;

`--quality 0.5` Less detailed results but 2x faster / cheaper.

`--quality 1` The **default value**, you do not need to specify it.

`--quality 2` More detailed results, but 2x slower and 2x the price (2 minutes per image).&#x20;

`--quality 5` kind of experimental, 'might' be more creative or detailed (also might be worse!) (5 minutes per image).

### Emoji Reactions to Generation Output

"React" to a generation with various emojis to trigger actions from the bot.

![how to add a reaction emoji](.gitbook/assets/reaction\_editing.gif)

✉️ The envelope emoji reaction sends an image to your DMs with the seed # and job ID. If the result was a grid, it will send each individual image. You may have to hunt for this emoji by typing "envelope" in your emoji list.

⭐️ Marks image as "favorite". This shows in a separate feed on the web gallery and sends the image to the #favorites channel.

❌ Cancels or deletes a generation at any time. It is also removed from the web gallery. Please help us by removing content you accidentally generated that is in violation of our PG-13 content guidelines (see [Content and Moderation](content-and-moderation-policy.md)).

### Image Prompting with URL

Add one or more image URLs to your prompt and it will use those images as visual inspiration. You can mix words with images or just have images alone. See [Image Prompt Questions](FAQs.md#image-prompt-questions) for more info and an animated gif below showing how to upload and use an image.

![Uploading an image to use with an image prompt](.gitbook/assets/Discord\_FHZfwDLhLY.gif)

`--iw:` Adjusts the weight of the image URLs vs the text. They default to 0.25.  Experiment and see what you like. Also see [FAQ here](FAQs.md#image-prompt-questions).

**Note**: There is currently no way to apply different weights to different image prompts. This will be addressed in the future.

**Also Note**: This is _not_ the same as building on top of (or "initializing" from) a starting input image as you may see in other generation tools. Midjourney does not currently offer the ability to use a starting image, due to concerns about community public content.  Instead, we let you use an image as inspiration, usually with text, to guide the generation.

### Advanced Text Weights

You can suffix any part of the prompt with `::0.5` to give that part a weight of 0.5. If the weight is not specified, it defaults to 1. See also [Text Prompt Questions](FAQs.md#text-prompt-questions).

Some examples:

* `/imagine hot dog::1.5 food::-1` — This sends a text prompt of `hot dog` with the weight 1.5 and `food` of weight -1
* `/imagine hot dog::1.25 animal::-0.75` — Sends `hot dog` of weight 1.25 and `animal` of negative 0.75
* `/imagine hot dog:: food::-1 animal` — Sends `hot dog` of weight 1, `food` of weight -1 and `animal` of weight 1

Prompts with a negative total weight are not allowed.

**Note**: The `--no` command is equivalent to using weight -0.5.  For instance, `--no farms` means don't include farms in the output, same as `farms::-.5`

### Prompt Preferences and Settings

`/settings` will give you some buttons to choose your preferences, like the `/prefer` command but visually.  Each row is a toggle button, meaning turning one on will turn the others off.&#x20;

![/settings options](<.gitbook/assets/image (6).png>)

`/prefer suffix <text>` — This will automatically append this suffix after all prompts you submit. Leave empty to reset.

**Note:** Only --options are currently officially supported as values for the suffix option, not just any regular text.

`/prefer auto_dm True` — Jobs will be automatically DMed to you. Set False to turn this off.

`/prefer option set <name> <value>` — This creates a personal option, which then translates to specified value when you invoke it by prepending it with --. Only you can use this option. For example, `/prefer option set mine --hd --w 512` creates an option called "mine" that translates to `--hd --w 512`. So you can use `/imagine rubber ducks are awesome --mine`, and it will be the exact same as if you did `/imagine rubber ducks are awesome --hd --w 512`. Leave the value field empty to delete an option.

![the /prefer option and value input](.gitbook/assets/prefer\_image.png)

`/prefer option list` — This will list your currently set personal options. You may keep a maximum of 20 personal options.

### Deprecated: May Want To Avoid

`--hq` `--newclip` `--nostretch` `--beta` `/pixels`\
``
