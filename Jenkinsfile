node('master') {

    def build_ok = true

    stage ('\u27A1 Checkout'){
        sh "echo 'checkout ok'"
    }


    def BUILD_LIST = readFile('/tmp/cmd_list.sh').split()
    for (CMDRUN in BUILD_LIST) {

        try {
            stage(CMDRUN) {

                println "Building ..."
                sh CMDRUN

            }

        }
        catch (e) { build_ok = false }

    }


    if(build_ok) { currentBuild.result = "SUCCESS" }
    else { currentBuild.result = "FAILURE" }

}
