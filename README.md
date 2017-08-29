import org.codehaus.groovy.runtime.ResourceGroovyMethods

class GenerateTask extends DefaultTask {

//    String[] plugins = ["corLocation",
//                        "corQQ",
//                        "corSina",
//                        "corWeiXin",
//                        "corBaiduMap",
//                        "corGaodeMap",
//                        "corJsonXmlTrans",
//                        "corScanner",
//                        "corJPush",
//                        "corAliPay",
//                        "corImage",
//                        "corDataBaseMgr",
//                        "corFileMgr",
//                        "corScrollPicture",
//                        "corWheelPickView",
//                        "corCamera",
//                        "corMobSMS",
//                        "corNative",
//                        "corUmeng",
//                        "corXmlHttpMgr",
//                        "corVideo",
//                        "corDevice",
//                        "corAudio",
//                        "corChatKeyboard"]
    String[] plugins = ["corQQ",
                        "corSina",
                        "corWeiXin",
                        "corAliPay",
                        "corImage",
                        "corXmlHttpMgr",
                        "corVideo"]
    String htmlPath = ""

    @TaskAction
    def generateCode(){
        println "htmlPath: $htmlPath"
        println "project.file(htmlPath).exists(): ${project.file(htmlPath).exists()}"
        if(!project.file(htmlPath).exists()){
            new File(htmlPath)
            println "project.file(htmlPath).exists()1: ${project.file(htmlPath).exists()}"
        }
        plugins.sort().each {plugin->
            println '<div @click="openH(\''+plugin +'\')" class="divD co-bd-r1 co-bd-b1 co-flex co-ac co-jc co-ver">'
            println '    <div class="coicon coicon-manage co-fs-5">'
            println '    </div>'
            println '    <div class="co-fs-01">' + plugin + '</div>'
            println '</div>'
        }
    }
}

task generateCode(type:GenerateTask){
    htmlPath = "${project.getProjectDir()}/${project.name}.html"
}
