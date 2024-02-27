# 1ère compilation : erreur de compilation


<h2>Commandes éxécutés :</h1>


<h3>1. Lancer mvn clean</h2>

<p>'mvn clean' Nettoye ce qu'il s'est passé avant.


<h3>2. Lancer mvn compile</h3>

<p>'mvn compile' Compile les classes : création du répertoire target qui contient ensuite la version compilée des classes 
(target/classes).

<hr>

# 2ème compilation : construire une application


<h3>1. Créer un main</h3>

```java
public static void main(String[] args) {
		System.out.println("Hello Blagnac");
	}
```


<h3>2. Une fois que vous avez réussi à compiler (mvn compile), lancez la fabrication d’une version exécutable :</h3>

<p>'mvn package' Crée une version éxécutable des classes compilées.


<h3>3. Observez la création du fichier JAR et testez-le :</h3>

'java -jar target/tp_qualite-1.0.jar' Exécute cette nouvelle version éxécutable.


# Améliorations


<h3>1. Reprenez un de vos exercices précédents et mettez les sources dans src/java.</h3>

```java
/**
 * Exo
 * @author Leonardo
 */
public class Exo {
	public static void main(String[] args) {
		System.out.println("1, 2, 3, Test Exo");
        afficher();
	}

    public static void afficher() {
        System.out.println("Bonjour");
    }
}
```


<h3>2. Ajustez éventuellement le pom.xml pour que les étapes précédentes produisent les résultats escomptés. Pensez à vérifier que votre fichier .jar est exécutable. Que devez-vous corriger dans votre pom.xml ? Quelle est la commande pour le lancer ?</h3>

<p> Remplacer :

```xml
<plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-jar-plugin</artifactId>
            <configuration>
                <archive>
                    <manifest>
                        <mainClass>HelloJava</mainClass> 
                    </manifest>
                </archive>
            </configuration>
        </plugin>
```

<p> Par : 

```xml
<plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-jar-plugin</artifactId>
            <configuration>
                <archive>
                    <manifest>
                        <mainClass>Exo</mainClass> 
                    </manifest>
                </archive>
            </configuration>
        </plugin>
```


<h3>3. Commentaires vu en Dev</h3>

```xml
<mainClass>Exo</mainClass> <!-- Ligne a changer pour compiler la bonne classe -->
```


<h3>4. Cherchez dans la documentation Maven les commandes permettant de générer une documentation javadoc, et les adaptions à faire sur votre projet (et éventuellement pom.xml) afin que Maven génère la documentation automatiquement pour vous.</h3>

<p> Pour générer la Javadoc de manière automatique il faut ajouter ce code au fichier xml :

```xml
 <!-- Ajout du plugin pour la javadoc automatique -->
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-javadoc-plugin</artifactId>
            <version>3.3.2</version>
            <configuration>
                <source>1.8</source> 
                <doclint>none</doclint> 
            </configuration>
        </plugin>
```
<p>Il faut ensuite ajouter la javadoc avec 'mvn javadoc:javadoc' ensuite compiler avec 'mvn compile', puis créer une version éxécutable avec 'mvn package'.
