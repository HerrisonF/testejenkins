/**Esse pipeline significa que vou fazer o script de forma declarativa**/
pipeline{
    /**esse agent, significa qual agente pode executar**/
    agent any
    //Aqui ness environment, eu posso criar variáveis. Que nesse caso é visivel em todo pipeline
    environment{
        BRANCH = 'Release'
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
                //O SH lê o comando de do texto, pelo que entendi
                sh 'printenv'
            }
        }
        //Forçando que dois estágios aconteçam juntos, pra só dps vir o step posterior
        stage('teste paralelo'){
            //Essa chave parallel é quem faz a mágica. Ela precisa envolver os steps.
            parallel{
                stage('Esteira 2 - A'){
                    //O when é um bloco condicionador.
                    when {
                        //Nesse caso, só vou executar o step 2 A, se a branch for Master ou hotfix
                        expression { BRANCH ==~ /(Master|Hotfix)/ }
                    }
                    steps {
                        echo 'step 2 A'
                    }
                }
                stage('Esteira 2 - B'){
                    steps {
                        echo 'step 2 B'
                    }
                }
            }
        }
        stage('Esteira 3'){
            when{
                expression {  BRANCH ==~ /(Release)/ }
            }
            steps{
                echo 'step 3'
            }
        }
    }
}