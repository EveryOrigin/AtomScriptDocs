# CommandSender

命令发送者将会作为变量sender注入到脚本注册命令的handlerFunction()内

可以直接调用

但是这里获取到的不是Bukkit的CommandSender类型或Player

而是TabooLib的各平台实现

假设命令执行者是玩家 那就是TabooLib的BukkitPlayer

## BukkitCommandSender

属性:

    #可以通过这个属性获取原平台CommandSender
    #比如服务端是Bukkit，那orgin就是org.bukkit.command.CommandSender的实现类
    origin

    #命令发送者的名字
    name

    #是否为op
    isOp()

方法:

    #是否在线
    isOnline():Boolean

    #发送一条信息
    sendMessage(message:String)

    #使其执行指令
    performCommand(command:String):Boolean

    #检查是否有权限
    hasPermission(permission:String):Boolean

    #执行指令
    dispatchCommand(sender:CommandSender)


!> 以下属性基本与方法基本每个平台都能直接调用

## BukkitPlayer

一般来说直接用这个就好了，不过想要原对象的话就使用sender.orgin去调用平台原方法

orgin的属性和方法跟这个基本一样

冒号后面是返回值类型

属性可以直接用 xxx = 值 去修改。别问我有啥用了

属性：

    #通过这个origin可以获取到org.bukkit.entity.Player
    origin

    name:String

    uniqueId:UUID

    #延迟值
    ping:Int

    #所处地区
    locale:String

    #所处世界名
    world:String

    #坐标
    location:Location

    #玩家的指南针指向的位置
    compassTarget:Location

    #床坐标
    bedSpawnLocation:Location

    #显示名
    displayName:String

    #在玩家列表里的显示名
    playerListName:String?

    #游戏模式
    gamemode

    #是否潜行
    isSneaking

    #是否奔跑
    isSprinting

    #是否格挡
    isBlocking

    #是否华翔
    isGliding

    #是否发光
    isGlowing

    #是否游泳
    isSwimming

    #是否使用激流附魔
    isRiptiding

    #是否在睡觉
    isSleeping

    #睡觉的时长
    sleepTicks

    #是否死亡
    isDead

    #是否正在交谈
    isConversing

    #是否被拴住
    isLeashed

    #是否站在地上
    isOnGround

    #是否在载具内
    isInsideVehicle

    #重力是否适用
    hasGravity

    #攻击冷却
    attackCooldown

    #时间
    playerTime

    #第一次进入服务器的时间
    firstPlayed

    #最后在线的时间
    lastPlayed

    #多久没攻击?受伤
    noDamageTicks:Int

    #剩余氧气值
    remainingAir:Int

    #最大氧气值
    maximumAir:Int

    #等级
    level:Int

    #经验值
    exp:Float

    #疲劳度
    exhaustion: Float

    #饱食度
    saturation: Float

    #饥饿度
    foodLevel:Int

    #生命值
    health: Double

    #最大生命值
    maxHealth: Double

    #是否允许飞行
    allowFlight: Boolean

    #是否正在飞行
    isFlying: Boolean

    #飞行速度
    flySpeed: Float

    #行走速度
    walkSpeed: Float

    #姿势名
    pose: String

    #面朝的方向名字
    facing: String

    #是否为Op
    isOp: Boolean

方法:

    #是否在线
    isOnline(): Boolean

    #踢出玩家，并给出原因，也可以不填原因
    kick(message: String?)

    #让玩家说话
    chat(message: String)

    #给玩家播放声音
    #播放坐标，声音名，音量, 音高
    playSound(location: Location, sound: String, volume: Float, pitch: Float)

    #发送Title
    #主标题 , 副标题(这两个都是选填) , 淡入时间 ， 停留时间 ， 淡出时间 
    sendTitle(title: String?, subtitle: String?, fadein: Int, stay: Int, fadeout: Int)

    #发送ActionBar，我没记错的话就是物品栏上的小字
    sendActionBar(message: String)

    #发送消息给玩家
    sendMessage(message: String)

    #发送粒子效果
    #这个后面写教程
    sendParticle(particle: ProxyParticle, location: Location, offset: Vector, count: Int, speed: Double, data: ProxyParticle.Data?)

    #使玩家执行命令
    performCommand(command: String): Boolean

    #是否有权限
    hasPermission(permission: String): Boolean

    #传送玩家至某个坐标
    teleport(loc: Location)