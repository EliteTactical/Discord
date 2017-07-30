const Discord = require ('discord.js');
const ytdl = require ('ytdl-core');
const client = new Discord.Client();

function commandIs(str, msg){
    return msg.content.toLowerCase().startsWith("#" + str);
}

function pluck(array) {
    return array.map(function(item) { return item["name"]; });
}

function hasRole(mem, role) {
    if(pluck(mem.roles).includes(role)){
        return true;
    } else {
        return false;
    }
}

client.on('ready', () => {
    client.user.setGame('#help')
    console.log ('Elite Bot is now online')
});

client.setInterval(() => {
    console.log('Hey');
}, 60000);

client.setInterval(() => {
    console.log(`${new Date()}`);
}, 60000);

client.on('guildMemberAdd', member => {
    member.guild.defaultChannel.send(`Welcome to the showers, ${member}!`)
})

client.on('guildMemberAdd', member => {
    member.guild.dm(`Welcome to the shower, ${member}!`)
})

client.on('guildMemberRemove', member => {
    member.guild.defaultChannel.send(`${member} has been gassed!`)
})

client.on('message', message => {    
    var args = message.content.split(/[ ]+/);

    if(commandIs("hi", message)){
        message.channel.sendMessage('Hey there, '+ message.author.username);
    }


    if(commandIs("youtube", message)){
        if(args.length === 1){
            message.channel.sendMessage('You did not define an argument. Usage: `!youtube [episode number]`');
        } else if(args.length === 2){
            message.channel.sendMessage("Hello, youtube, this is episode " + args[1]);
        }else {
            message.channel.sendMessage("You defined to many arguments. Usage: `!youtube [episode number]`");
        }


    }if(commandIs("say", message)){
      if(hasRole(message.member, "HITLER") || hasRole(message.member, "NAZI'S") || hasRole(message.member, "Owner") || hasRole(message.member, "Admin")){
            if(args.length === 1){
            message.channel.sendMessage('You did not define an argument. Usage: `say [Message to say]`');
        } else {
            message.channel.sendMessage(args.join(" ").substring(5));
        }
      } else {
           message.channel.sendMessage("You are not `Hitler`");
      }
    }


    if(commandIs("help", message)){
        message.channel.sendMessage('[All Normal Bot Commands]\n\n#hi             |  Bot will say hello.\n#say            |  Makes bot say something.\n#ban            |  Bot will ban tagged user.\n#comp           |  Shows competitive commands.\n#kick           |  Bot will kick tagged user.\n#clear          |  Clears msg\'s\n#delete         |  Deletes previous message\n#pranked        |  Pulls a prank.\n#SecretCommands |  Shows secret commands...', {code: 'css'});
    }

    if(commandIs("siegeranks", message)){
        message.channel.sendMessage('[Rainbow Six Siege Ranks:]\n#Copper    | PLEB\n#Bronze    | N00B\n#Silver    | N00BISH\n#Gold      | DECENT\n#Platinum  | GREAT\n#Diamond   | PRO', {code: 'css'});
    }


if (commandIs("why", message)){
    message.channel.sendMessage('Please stop bullying EJ, hes is my only friend and my best friend. :(')
}

if(commandIs("dick", message)){
    message.channel.sendMessage('You have one more chance, mess it up, and I kick you -_-.')
}


    if (commandIs("delete", message)){
          if(hasRole(message.member, "HITLER") || hasRole(message.member, "NAZI'S") || hasRole(message.member, "Owner") || hasRole(message.member, "Admin")){
            if(args.length >= 3){
            message.channel.sendMessage('You defined too many arguments.` Usage: !delete (number of messages to delete)`');
        } else {
            var msg;
            if(args.length === 1){
                msg=2;
            } else {
                msg=parseInt(args[1] + 1);
            }
            message.channel.fetchMessages({limit: msg}).then(messages => message.channel.bulkDelete(messages)).catch(console.error);
        }
      } else {
           message.channel.sendMessage("You are not `Owner or Admin`");
      }
    }

    if(commandIs("kick", message)){
         if(hasRole(message.member, "HITLER") || hasRole(message.member, "NAZI'S") || hasRole(message.member, "Owner") || hasRole(message.member, "Admin")){
            if(args.length === 1){
            message.channel.sendMessage('You did not define an argument. Usage: `kick [user to kick]`');
        } else {
            message.guild.member(message.mentions.users.first()).kick();
        }
    
    } else {
        message.channel.sendMessage("You are not `Owner or Admin`");
    }

}

    if(commandIs("ban", message)){
         if(hasRole(message.member, "HITLER") || hasRole(message.member, "NAZI'S") || hasRole(message.member, "Owner") || hasRole(message.member, "Admin")){
             if(args.length === 1){
                 message.channel.sendMessage('You did not define an argument. Usage: `ban` [user to ban]`');
             } else {
                 message.guild.member(message.mentions.users.first()).ban();
             }
         } else {
             message.channel.sendMessage("You are not `Owner or Admin`");
         }
    }

    if(commandIs("clear", message)){
        if(hasRole(message.member, "HITLER") || hasRole(message.member, "NAZI'S") || hasRole(message.member, "Owner") || hasRole(message.member, "Admin")){
            if(args.length >= 24){
                message.channel.sendMessage('You defined too many arguments. `Usage:` !clear');
            } else {
                var msg;
                if(args.length === 24){
                    msg=25;
                } else {
                    msg=parseInt(args[1] + [24]);
                }
            }
            message.channel.fetchMessages({limit:msg}).then(messages => message.channel.bulkDelete(messages)).catch(console.error);
        } else {
            message.channel.sendMessage("You are not `Owner or Admin`");
        }
    }

    if(commandIs("link", message)){
        message.channel.sendMessage('YouTube - https://www.youtube.com/channel/UCtqMkA40BFvt88elIm-ZNFw\
        Twitter - https://twitter.com/xEliteTactical');
    }

    if(commandIs("meme1", message)){
        message.channel.sendMessage('https://ifunny.co/fun/Chy6ZjXt4?gallery=user&query=Analucifer');
    }

    if(commandIs("meme2", message)){
        message.channel.sendMessage('https://ifunny.co/fun/U9uDFsNs4'); 
    }

    if(commandIs("meme3", message)){
        message.channel.sendMessage('https://cdn.discordapp.com/attachments/275028473180061708/328258592300072960/kjlrbsfkgresuhjkin5.jpg');
    }

    if(commandIs("meme4", message)){
        message.channel.sendMessage('https://cdn.discordapp.com/attachments/321188201240985611/328259839744540673/ilureg8o7g78sh5.jpg');
    }

    if(commandIs("meme5", message)){
        message.channel.sendMessage('https://cdn.discordapp.com/attachments/321188201240985611/328259804080504832/eJwFwVsKwyAQAMC7-B_fxk0uE0TFSBNXdBsopXfvzJe9x8V2dhL1uQuR6ow4Ep-EI5TMC2K5cuh18oi3CEQhnnduNIX2Tmqw3iiQ.png');
    }

    if(commandIs("meme6", message)){
        message.channel.sendMessage('https://cdn.discordapp.com/attachments/321188201240985611/328259739387559946/fwaefaeraerwf.jpg');
    }

    if(commandIs("meme7", message)){
        message.channel.sendMessage('https://cdn.discordapp.com/attachments/321188201240985611/328259709331308544/ghear6541g97ae4789g.jpg');
    }

     if(commandIs("meme8", message)){
        message.channel.sendMessage('https://cdn.discordapp.com/attachments/328260067109371904/328268102435471360/feuhlrfinlfraeuin8f98fahrf98afh98.jpg'); 
    }

    if(commandIs("meme9", message)){
        message.channel.sendMessage('https://cdn.discordapp.com/attachments/328260067109371904/328270261935800322/nkgiuafashifr7faf.jpg'); 
    }

    if(commandIs("meme0", message)){
        message.channel.sendMessage('https://cdn.discordapp.com/attachments/321188201240985611/328259690116939776/eJwNyksOhCAQBcC7cADobj6v9TKGqEETFSPMyszdZ2pdr_k8hxnN1vvdRueWvc31WWzr9clltaXWcqz53pud6-ly73nezvXqzQki.png');
    }

    if(commandIs("memes0", message)){
        message.channel.sendMessage('https://cdn.discordapp.com/attachments/321188201240985611/328259603987038208/eJwViVEOxBAUAO_ivzx0sb1MIyoqUU94vjZ797Vfk5n5sNkLO9hN1MYhxJVHwH7xQdh9ijwhphJ9y4MHfIQn8uF-YqUhlH2BcrvV.png');
    }

    if(commandIs("memes1", message)){
        message.channel.sendMessage('https://cdn.discordapp.com/attachments/328260067109371904/328273585770594304/eJwNzMENwyAMAMBdGAAbnBQr2yCCCFKIEXZfVXdvb4D7uPe63eEus6kHwNm1yDq9mqzcqm8i7a55dvVFBmSzXK5RH1OIacfIW6LA.png');
    }

    if(commandIs("memes2", message)){
        message.channel.sendMessage('http://www.mediafire.com/convkey/91ad/rnkqwl0hy6u1kdezg.jpg');
    }

    if(commandIs("memes3", message)){
        message.channel.sendMessage('https://i.redd.it/fpt0dnropm5z.jpg');
    }

    if(commandIs("memes4", message)){
        message.channel.sendMessage('https://cdn.discordapp.com/attachments/328260067109371904/328331821823688705/image.jpg');
    }
    
    if(commandIs("memes5", message)){
        message.channel.sendMessage('https://cdn.discordapp.com/attachments/328260067109371904/328331779251372032/image.jpg');
    }

    if(commandIs("memes6", message)){
        message.channel.sendMessage('https://cdn.discordapp.com/attachments/328260067109371904/328331740680683530/image.jpg');
    }

    if(commandIs("memes7", message)){
        message.channel.sendMessage('https://cdn.discordapp.com/attachments/328260067109371904/328332910606155787/image.jpg');
    }

    if(commandIs("dead", message)){
        message.channel.sendMessage('https://cdn.discordapp.com/attachments/328260067109371904/328332961093124098/image.jpg');
    }

    if(commandIs("gif0", message)){
        message.channel.sendMessage('https://cdn.discordapp.com/attachments/328260067109371904/328333355378540544/image.gif');
    }

    if(commandIs("memes8", message)){
        message.channel.sendMessage('http://ifunny.co/fun/9RPZR2F84');
    }

    if(commandIs("gif1", message)){
        message.channel.sendMessage('https://cdn.discordapp.com/attachments/328260067109371904/328334372052926464/image.gif');
    }

    if(commandIs("gif2", message)){
        message.channel.sendMessage('https://cdn.discordapp.com/attachments/328260067109371904/328336835111682048/image.gif');
    }

    if(commandIs("gif3", message)){
        message.channel.sendMessage('https://cdn.discordapp.com/attachments/328260067109371904/328659410949898250/image.gif');
    }

    if(commandIs("gif4", message)){
        message.channel.sendMessage('http://ifunny.co/fun/lVkUAapw4');
    }

    if(commandIs("pubgstats", message)){
        message.channel.sendMessage('*solo wins* - **2**\
        *Duos Wins* - **5**\
        *Squad Wins* - **8**')
    }

    if(commandIs("pranked", message)){
        message.channel.sendMessage(message.author + ' **:regional_indicator_k::regional_indicator_y::regional_indicator_s:**');
    }

    if(commandIs("comp", message)){
        message.channel.sendMessage('[Competitive Commands]\n\n#siegeranks    | Shows all Ranbiw Six Siege Ranks.\n#obistats      | Shows Obi\'s Stats\n#Fuistats      | Shows Fui\'s Stats\n#elitestats    | Shows Elite\'s Stats\n#turbostats    | Shows Turbo\'s Stats\n#mellandstats  | Shows Melland\'s Stats', {code: 'css'});
    }

    if(commandIs("elitestats", message)){
        message.channel.sendMessage({embed: {
            color: 1752220,
            author: {
                name: 'Elite\'s Stats',
                icon_url: client.user.avatarURL
            },
            title: 'Click Here For Stats',
            url: 'https://game-rainbow6.ubi.com/en-us/uplay/player-statistics/4255f83c-ac9d-4b2e-b560-9dfdcdfbc428/multiplayer',
            description: 'Login, then it will show Elite\'s stats',
            field: [
                {
                    name: 'Pranked',
                    value: 'Jakob is brown'
                }
            ],
            timestamp: new Date(),
            footer: {
                icon_url: client.user.avatarURL,
                text: 'Trust this domain'
            }
        }});
    }


    if(commandIs("obistats", message)){
        message.channel.sendMessage({embed: {
            color: "15158332",
            author: {
                name: 'Obi\'s Stats',
                icon_url: client.user.avatarURL
            },
            title: 'Click Here For Stats',
            url: 'https://game-rainbow6.ubi.com/en-us/uplay/player-statistics/4255f83c-ac9d-4b2e-b560-9dfdcdfbc428/multiplayer',
            description: 'Login, then it will show Obi\'s stats',
            field: [
                {
                    name: 'Pranked',
                    value: 'Jakob is brown'
                }
            ],
            timestamp: new Date(),
            footer: {
                icon_url: client.user.avatarURL,
                text: 'Trust this domain'
            }
        }});
    }


    if(commandIs("turbostats", message)){
        message.channel.sendMessage({embed: {
            color: "10181046",
            author: {
                name: 'Turbo\'s Stats',
                icon_url: client.user.avatarURL
            },
            title: 'Click Here For Stats',
            url: 'https://game-rainbow6.ubi.com/en-us/uplay/player-statistics/b01c72d8-7e08-4d05-81e0-1530f5f2ec26/multiplayer',
            description: 'Login, then it will show Turbo\'s stats',
            field: [
                {
                    name: 'Pranked',
                    value: 'jakob is brown'
                }
            ],
            timestamp: new Date(),
            footer: {
                icon_url: client.user.avatarURL,
                text: 'Trust this domain'
            }
        }});
    }


    if(commandIs("mellandstats", message)){
        message.channel.sendMessage({embed: {
            color: "10181046",
            author: {
                name: 'Melland\'s Stats',
                icon_url: client.user.avatarURL
            },
            title: 'Click Here For Stats',
            url: 'https://game-rainbow6.ubi.com/en-us/uplay/player-statistics/c4a25399-38ea-4074-8d9a-7368f1f4d63a/multiplayer',
            description: 'Login, then it will show Melland\'s stats',
            field: [
                {
                    name: 'Pranked',
                    value: 'Jakob is brown'
                }
            ],
            timestamp: new Date(),
            footer: {
                icon_url: client.user.avatarURL,
                text: 'Trust this domain'
            }
        }});
    }


    if(commandIs("fuistats", message)){
        message.channel.sendMessage({embed: {
            color: "3066993",
            author: {
                name: 'Fully\'s Stats',
                icon_url: client.user.avatarURL
            },
            title: 'Click Here For Stats',
            url: 'https://game-rainbow6.ubi.com/en-us/uplay/player-statistics/c219e4d2-4f70-4a24-9de1-0ea711d56128/multiplayer',
            description: 'Login, then it will show Fully\'s Stats',
            field: [
                    {
                        name: 'Pranked',
                        value: 'Jakob is brown'
                    }
                ],
                timestamp: new Date(),
                footer: {
                    icon_url: client.user.avatarURL,
                    text: 'Trust this domain'
                }
        }});
    }

    if(commandIs("secretcommands", message)){
        message.channel.sendMessage('Thats not the right command... Try something else' + message.author);
    }

    if(commandIs("gfuel", message)){
        message.channel.sendMessage('You just wasted a lot of time finding this *secret* command, It is nothing ;).');
    }

    if(commandIs("trashgames", message)){
        message.channel.sendMessage('[Most trash games ever created]\n\n#1: Siege\n#Why?: The banning system is run by niggers with down syndrome', {code: 'css'});
    }
});

client.login('MzI0NDI2MTU4OTQwNzQ5ODI3.DCMgfg.APxm4pi3tad9LlaI06Ros9sGb6I');
