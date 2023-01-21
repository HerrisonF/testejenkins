/**Esse pipeline significa que vou fazer o script de forma declarativa**/
pipeline{
    /**esse agent, significa qual agente pode executar**/
    agent any
    /** Os stages substituem o comando NODE, que era usado na forma de script **/
    stages {
        stage('Esteira 1'){
            steps {
                echo 'step 1'
            }
        }
        //Forçando que dois estágios aconteçam juntos, pra só dps vir o step posterior
        stage('teste paralelo'){
            //Essa chave parallel é quem faz a mágica. Ela precisa envolver os steps.
            parallel{
                stage('Esteira 2'){
                    steps {
                        echo 'step 2'
                    }
                }
                stage('Esteira 2'){
                    steps {
                        echo 'step 2'
                    }
                }
            }
        }
        stage('Esteira 3'){
            steps{
                echo 'step 3'
            }
        }
    }
}