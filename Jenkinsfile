/**Esse pipeline significa que vou fazer o script de forma declarativa**/
pipeline{
    /**esse agent, significa qual agente pode executar**/
    agent any
    //Aqui ness environment, eu posso criar variáveis. Que nesse caso é visivel em todo pipeline
    environment{
        BRANCH = 'Master'
    }
    /** Os stages substituem o comando NODE, que era usado na forma de script **/
    stages {
        stage('Esteira 1'){
            //Essas variáveis só estão visíveis nesse escopo do Esteira 1
            environment{
                OUTRO = 'Outro valor'
            }
            steps {
                echo 'step 1'
                sh 'printenv'
            }
        }
        //Forçando que dois estágios aconteçam juntos, pra só dps vir o step posterior
        stage('teste paralelo'){
            //Essa chave parallel é quem faz a mágica. Ela precisa envolver os steps.
            parallel{
                stage('Esteira 2 - A'){
                    steps {
                        echo 'step 2 A'
                        sh 'printenv'
                    }
                }
                stage('Esteira 2 - B'){
                    steps {
                        echo 'step 2 B'
                        sh 'printenv'
                    }
                }
            }
        }
        stage('Esteira 3'){
            steps{
                echo 'step 3'
                sh 'printenv'
            }
        }
    }
}