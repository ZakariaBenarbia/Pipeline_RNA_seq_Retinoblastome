# Pipeline_RNA_seq_Retinoblastome

<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Analyse Transcriptomique - Rétinoblastome (GSE125903)</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            line-height: 1.6;
            margin: 0;
            padding: 0;
            background-color: #f4f4f9;
            color: #333;
        }
        header {
            background: #214e7a;
            color: #ffffff;
            padding: 20px 0;
            text-align: center;
            border-bottom: 5px solid #e05b5b;
        }
        header h1 {
            margin: 0;
            font-size: 2.5em;
        }
        header p {
            font-size: 1.1em;
        }
        .container {
            width: 85%;
            margin: auto;
            overflow: hidden;
            padding: 20px 0;
        }
        section {
            padding: 20px;
            margin-bottom: 20px;
            background: #fff;
            border-radius: 8px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }
        h2 {
            color: #214e7a;
            border-bottom: 2px solid #ddd;
            padding-bottom: 10px;
            margin-top: 0;
        }
        .workflow-space, .image-placeholder {
            min-height: 300px;
            background: #e9e9e9;
            border: 2px dashed #999;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 20px auto;
            border-radius: 5px;
            text-align: center;
            font-style: italic;
            color: #666;
        }
        .key-finding {
            font-weight: bold;
            color: #e05b5b;
        }
        ul {
            list-style: none;
            padding: 0;
        }
        ul li::before {
            content: "•";
            color: #7ab971;
            font-weight: bold;
            display: inline-block;
            width: 1em;
            margin-left: -1em;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 15px;
        }
        th, td {
            padding: 10px;
            text-align: left;
            border-bottom: 1px solid #ddd;
        }
        th {
            background-color: #f0f0f0;
        }
        .report-box {
            display: flex;
            gap: 20px;
            align-items: stretch;
            margin-top: 15px;
        }
        .report-link, .report-explanation {
            flex: 1;
            background: #fafafa;
            border: 1px solid #e0e0e0;
            padding: 15px;
            border-radius: 6px;
            box-shadow: 0 1px 3px rgba(0,0,0,0.04);
        }
        .report-link a {
            display: inline-block;
            padding: 10px 14px;
            background: #214e7a;
            color: #fff;
            text-decoration: none;
            border-radius: 4px;
        }
        .report-explanation h4 {
            margin-top: 0;
            color: #214e7a;
        }
    </style>
</head>
<body>

    <header>
        <h1>Analyse Transcriptomique Intégrée du Rétinoblastome</h1>
        <p>Projet basé sur le jeu de données GEO : GSE125903 (Tumeur pédiatrique de la rétine)</p>
    </header>

    <div class="container">

        <section id="introduction">
            <h2>Introduction : Le rétinoblastome, qu'est-ce que c'est ?</h2>
            <p>Le rétinoblastome est une tumeur cancéreuse maligne de la rétine qui touche presque exclusivement les jeunes enfants, généralement avant l'âge de 5 ans. C'est le cancer de l'œil le plus fréquent chez l'enfant, bien qu'il reste une maladie rare (environ 1 naissance sur 15 000 à 20 000).</p>
            <p>L'objectif de cette étude est d'utiliser l'analyse transcriptomique pour cartographier précisément ces altérations moléculaires.</p>
            
            <div class="image-placeholder" style="min-height: 250px;">
                <img src="images/retinoblastoma.jpg" alt="retinoblastoma" style="max-width: 100%; max-height: 100%;">
                </div>
                <div class="image-placeholder" style="min-height: 250px;">
                <img src="images/retinoblastoma2.jpg" alt="retinoblastoma2" style="max-width: 100%; max-height: 100%;">
                </div>
        </section>

        <section id="pipeline">
            <h2>Pipeline d'Analyse Bio-informatique</h2>
            <p>Le travail a suivi un pipeline rigoureux, de l'acquisition des données brutes à l'interprétation biologique, intégrant trois analyses clés (EPIC, DESeq2, WGCNA).</p>
            
            <div class="workflow-space">
                <img src="images/workflow.png" alt="workflow" style="max-width: 100%; max-height: 100%;">
                </div>
        </section>

        <section id="Donnees Brutes FastQ">
            <h2>Donnees Brutes FastQ</h2>
            
            <h3>Sélection du jeu de données</h3>
            <p>
             Le jeu de données GSE125903 a été sélectionné car il fournit des données RNA-seq brutes issues de sept échantillons de rétinoblastome et de trois échantillons de rétine normale. Il permet l’application complète d’un pipeline RNA-seq standard et l’identification des altérations transcriptionnelles associées au rétinoblastome, notamment la perte d’expression de RB1, malgré une différence d’âge potentiellement confondante entre les groupes.            </p>
            
            <div class="image-placeholder" style="min-height: 200px;">
               <img src="images/GEO.png" alt="GEO" style="max-width: 100%; max-height: 100%;">
            </div>
            <div class="image-placeholder" style="min-height: 200px;">
               <img src="images/NCBI.png" alt="NCBI" style="max-width: 100%; max-height: 100%;">
            </div>
            <h4>Téléchargement des Données</h4>
            <ul>
                <li><strong>Outil utilisé:</strong> Faster Download and Extract Reads in FASTQ (Galaxy)</li>
                <li><strong>Commande utilisée</strong> :</li>
                <br>Input type: List of SRA accession, one per line</br>
                <br>Accessions: SRR8507300-309 (10 échantillons)</br>
            </ul>
            <div class="image-placeholder" style="min-height: 200px;">
               <img src="images/Faster.png" alt="Faster" style="max-width: 100%; max-height: 100%;">
        </section>

        <section id="CONTROLE_QUALITE_DES_READS_BRUTS">
            <h2>Contrôle Qualité des Reads Bruts</h2>
            <h1>FastQC</h1>

            <p>Le contrôle qualité initial des reads bruts a été effectué à l'aide de FastQC pour évaluer la qualité globale des séquences avant tout traitement.</p>


            <div class="image-placeholder" style="min-height: 200px;">
               <img src="images/Fastqc.png" alt="Fastqc" style="max-width: 100%; max-height: 100%;">
            </div>
            <h3>Résumé du Contrôle Qualité</h3>
            <table>
                <thead>
                    <tr>
                        <th>Échantillon</th>
                        <th>Forward</th>
                        <th>Reverse</th>
                    </tr>
                </thead>
                <tbody>
                    <tr><td>SRR8507300</td><td><a href="FASTQC_avant/SRR8507300_forward_fastqc.html">SRR8507300_forward</a></td><td><a href="FASTQC_avant/SRR8507300_reverse_fastqc.html">SRR8507300_reverse</a></td></tr>
                    <tr><td>SRR8507301</td><td><a href="FASTQC_avant/SRR8507301_forward_fastqc.html">SRR8507301_forward</a></td><td><a href="FASTQC_avant/SRR8507301_reverse_fastqc.html">SRR8507301_reverse</a></td></tr>
                    <tr><td>SRR8507302</td><td><a href="FASTQC_avant/SRR8507302_forward_fastqc.html">SRR8507302_forward</a></td><td><a href="FASTQC_avant/SRR8507302_reverse_fastqc.html">SRR8507302_reverse</a></td></tr>
                    <tr><td>SRR8507303</td><td><a href="FASTQC_avant/SRR8507303_forward_fastqc.html">SRR8507303_forward</a></td><td><a href="FASTQC_avant/SRR8507303_reverse_fastqc.html">SRR8507303_reverse</a></td></tr>
                    <tr><td>SRR8507304</td><td><a href="FASTQC_avant/SRR8507304_forward_fastqc.html">SRR8507304_forward</a></td><td><a href="FASTQC_avant/SRR8507304_reverse_fastqc.html">SRR8507304_reverse</a></td></tr>
                    <tr><td>SRR8507305</td><td><a href="FASTQC_avant/SRR8507305_forward_fastqc.html">SRR8507305_forward</a></td><td><a href="FASTQC_avant/SRR8507305_reverse_fastqc.html">SRR8507305_reverse</a></td></tr>
                    <tr><td>SRR8507306</td><td><a href="FASTQC_avant/SRR8507306_forward_fastqc.html">SRR8507306_forward</a></td><td><a href="FASTQC_avant/SRR8507306_reverse_fastqc.html">SRR8507306_reverse</a></td></tr>
                    <tr><td>SRR8507307</td><td><a href="FASTQC_avant/SRR8507307_forward_fastqc.html">SRR8507307_forward</a></td><td><a href="FASTQC_avant/SRR8507307_reverse_fastqc.html">SRR8507307_reverse</a></td></tr>
                    <tr><td>SRR8507308</td><td><a href="FASTQC_avant/SRR8507308_forward_fastqc.html">SRR8507308_forward</a></td><td><a href="FASTQC_avant/SRR8507308_reverse_fastqc.html">SRR8507308_reverse</a></td></tr>
                    <tr><td>SRR8507309</td><td><a href="FASTQC_avant/SRR8507309_forward_fastqc.html">SRR8507309_forward</a></td><td><a href="FASTQC_avant/SRR8507309_reverse_fastqc.html">SRR8507309_reverse</a></td></tr>
                </tbody>
            </table>

            <h1>MultiQC</h1>

             <div class="image-placeholder" style="min-height: 200px;">
               <img src="images/Multiqc.png" alt="MultiQC" style="max-width: 100%; max-height: 100%;">
            </div>

            <div class="report-box">
                <div class="report-link">
                    <h4>Rapport MultiQC</h4>
                    <p>Accédez au rapport MultiQC consolidé pour tous les échantillons :</p>
                    <p><a href="FASTQC_avant/MultiQC_on_data_136,_data_138,_and_others__Webpage_html.html" target="_blank">Ouvrir le rapport MultiQC</a></p>
                </div>
                <div class="report-explanation">
                    
                <h4>Résumé</h4>
                    <table>
                        <thead>
                            <tr>
                                <th>Indicateur</th>
                                <th>Statut</th>
                                <th>Résultat &amp; Conséquence</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>Qualité des Bases</td>
                                <td><span style="color:green; font-weight:bold;">BON (Vert)</span></td>
                                <td>Qualité moyenne excellente (Phred &gt; 30) sur toute la longueur des lectures (100 bp).</td>
                            </tr>
                            <tr>
                                <td>Profondeur de Séquençage</td>
                                <td><span style="color:green; font-weight:bold;">BON (Vert)</span></td>
                                <td>Couverture élevée (40 à 80 millions de lectures/échantillon), suffisante pour l'analyse d'expression.</td>
                            </tr>
                            <tr>
                                <td>Duplication de Séquences</td>
                                <td><span style="color:red; font-weight:bold;">ÉCHEC (Rouge)</span></td>
                                <td>Niveaux de duplication très élevés. Indique une sur-amplification PCR. Nécessite une déduplication ou un filtrage.</td>
                            </tr>
                            <tr>
                                <td>Contenu en Adaptateurs</td>
                                <td><span style="color:red; font-weight:bold;">ÉCHEC (Rouge)</span></td>
                                <td>Présence significative d'adaptateurs techniques, surtout après 60 bp. Nécessite un &quot;trimming&quot; (nettoyage).</td>
                            </tr>
                            <tr>
                                <td>Séquences Surreprésentées</td>
                                <td><span style="color:red; font-weight:bold;">ÉCHEC (Rouge)</span></td>
                                <td>Lié aux adaptateurs et aux duplicats.</td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div> 
            
            <h1>Trimmomatic - Nettoyage des Reads</h1>
            <p><strong>Outil :</strong> Trimmomatic (Galaxy Version 0.39)</p>
            <p><strong>Type de données :</strong> Paired-end (deux fichiers FASTQ par échantillon)</p>
            
            <h3>Paramètres de trimming</h3>
            <ul>
                <div class="image-placeholder" style="min-height: 200px;">
                    <img src="images/trim1.png" alt="trim1" style="max-width: 100%; max-height: 100%;">
                 </div>
                <li><strong>SLIDINGWINDOW</strong> : fenêtre de qualité glissante
                    <ul>
                        <li>Taille de fenêtre : 4 bases</li>
                        <li>Qualité minimale requise : 20 (score Phred)</li>
                    </ul>
                    <div class="image-placeholder" style="min-height: 200px;">
                        <img src="images/trim2.png" alt="trim2" style="max-width: 100%; max-height: 100%;">
                     </div>
                </li>
                <li><strong>LEADING</strong> : coupe des bases de faible qualité en 5’
                    <ul>
                        <li>Qualité minimale : 3</li>
                    </ul>
                    <div class="image-placeholder" style="min-height: 200px;">
                        <img src="images/trim3.png" alt="trim3" style="max-width: 100%; max-height: 100%;">
                     </div>
                </li>
                <li><strong>TRAILING</strong> : coupe des bases de faible qualité en 3’
                    <ul>
                        <li>Qualité minimale : 3</li>
                    </ul>
                    <div class="image-placeholder" style="min-height: 200px;">
                        <img src="images/trim4.png" alt="trim4" style="max-width: 100%; max-height: 100%;">
                     </div>
                </li>
                <li><strong>MINLEN</strong> : longueur minimale des reads conservés
                    <ul>
                        <li>Longueur minimale : 39 pb</li>
                    </ul>
                    <div class="image-placeholder" style="min-height: 200px;">
                        <img src="images/trim5.png" alt="trim5" style="max-width: 100%; max-height: 100%;">
                     </div>
                </li>
            </ul>

            <h3>Résumé des opérations de trimming</h3>
            <table>
                <thead>
                    <tr>
                        <th>Opération</th>
                        <th>Rôle</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td><strong>SLIDINGWINDOW</strong></td>
                        <td>Balaye la lecture avec une fenêtre glissante et coupe dès que la qualité moyenne dans la fenêtre passe sous le seuil défini.</td>
                    </tr>
                    <tr>
                        <td><strong>MINLEN</strong></td>
                        <td>Élimine complètement la lecture si sa longueur finale est inférieure à la longueur minimale spécifiée.</td>
                    </tr>
                    <tr>
                        <td><strong>LEADING</strong></td>
                        <td>Coupe les bases au début de la lecture tant que leur qualité est inférieure au seuil.</td>
                    </tr>
                    <tr>
                        <td><strong>TRAILING</strong></td>
                        <td>Coupe les bases à la fin de la lecture tant que leur qualité est inférieure au seuil.</td>
                    </tr>
                </tbody>
            </table>

            <h3>Résultats du trimming</h3>
            <p>Pour <strong>chaque échantillon</strong>, nous obtenons <strong>4 fichiers de sortie</strong> après Trimmomatic :</p>
            <ul>
                <div class="image-placeholder" style="min-height: 200px;">
                    <img src="images/trim6.png" alt="trim6" style="max-width: 100%; max-height: 100%;">
                 </div>
                <li><strong>2 fichiers "paired"</strong> : reads nettoyés conservés en paires, utilisés pour l’alignement.</li>
                <li><strong>2 fichiers "unpaired"</strong> : reads orphelins (une seule extrémité conservée), <em>non utilisés</em> dans les étapes d’alignement et d’analyse différentielle.</li>
            </ul>
            <p>Dans notre jeu de données (10 échantillons), cela correspond à un total de <strong>10 fichiers "paired"</strong> et <strong>10 fichiers "unpaired"</strong> générés.</p>

            <h1>Contrôle Qualité des Reads Après Trimming</h1>
            <h3>Résumé du Contrôle Qualité Après Trimming (FastQC)</h3>
            <table>
                <thead>
                    <tr>
                        <th>Échantillon</th>
                        <th>Forward (paired)</th>
                        <th>Reverse (paired)</th>
                    </tr>
                </thead>
                <tbody>
                    <tr><td>SRR8507300</td><td><a href="FASTQC_apres/Trimmomatic on SRR8507300_forward _R1 paired__fastqc.html">SRR8507300_forward_paired</a></td><td><a href="FASTQC_apres/Trimmomatic on SRR8507300_reverse _R2 paired__fastqc.html">SRR8507300_reverse_paired</a></td></tr>
                    <tr><td>SRR8507301</td><td><a href="FASTQC_apres/Trimmomatic on SRR8507301_forward _R1 paired__fastqc.html">SRR8507301_forward_paired</a></td><td><a href="FASTQC_apres/Trimmomatic on SRR8507301_reverse _R2 paired__fastqc.html">SRR8507301_reverse_paired</a></td></tr>
                    <tr><td>SRR8507302</td><td><a href="FASTQC_apres/Trimmomatic on SRR8507302_forward _R1 paired__fastqc.html">SRR8507302_forward_paired</a></td><td><a href="FASTQC_apres/Trimmomatic on SRR8507302_reverse _R2 paired__fastqc.html">SRR8507302_reverse_paired</a></td></tr>
                    <tr><td>SRR8507303</td><td><a href="FASTQC_apres/Trimmomatic on SRR8507303_forward _R1 paired__fastqc.html">SRR8507303_forward_paired</a></td><td><a href="FASTQC_apres/Trimmomatic on SRR8507303_reverse _R2 paired__fastqc.html">SRR8507303_reverse_paired</a></td></tr>
                    <tr><td>SRR8507304</td><td><a href="FASTQC_apres/Trimmomatic on SRR8507304_forward _R1 paired__fastqc.html">SRR8507304_forward_paired</a></td><td><a href="FASTQC_apres/Trimmomatic on SRR8507304_reverse _R2 paired__fastqc.html">SRR8507304_reverse_paired</a></td></tr>
                    <tr><td>SRR8507305</td><td><a href="FASTQC_apres/Trimmomatic on SRR8507305_forward _R1 paired__fastqc.html">SRR8507305_forward_paired</a></td><td><a href="FASTQC_apres/Trimmomatic on SRR8507305_reverse _R2 paired__fastqc.html">SRR8507305_reverse_paired</a></td></tr>
                    <tr><td>SRR8507306</td><td><a href="FASTQC_apres/Trimmomatic on SRR8507306_forward _R1 paired__fastqc.html">SRR8507306_forward_paired</a></td><td><a href="FASTQC_apres/Trimmomatic on SRR8507306_reverse _R2 paired__fastqc.html">SRR8507306_reverse_paired</a></td></tr>
                    <tr><td>SRR8507307</td><td><a href="FASTQC_apres/Trimmomatic on SRR8507307_forward _R1 paired__fastqc.html">SRR8507307_forward_paired</a></td><td><a href="FASTQC_apres/Trimmomatic on SRR8507307_reverse _R2 paired__fastqc.html">SRR8507307_reverse_paired</a></td></tr>
                    <tr><td>SRR8507308</td><td><a href="FASTQC_apres/Trimmomatic on SRR8507308_forward _R1 paired__fastqc.html">SRR8507308_forward_paired</a></td><td><a href="FASTQC_apres/Trimmomatic on SRR8507308_reverse _R2 paired__fastqc.html">SRR8507308_reverse_paired</a></td></tr>
                    <tr><td>SRR8507309</td><td><a href="FASTQC_apres/Trimmomatic on SRR8507309_forward _R1 paired__fastqc.html">SRR8507309_forward_paired</a></td><td><a href="FASTQC_apres/Trimmomatic on SRR8507309_reverse _R2 paired__fastqc.html">SRR8507309_reverse_paired</a></td></tr>
                </tbody>
            </table>

            <h3>MultiQC après trimming</h3>
            <div class="report-box">
                <div class="report-link">
                    <h4>Rapport MultiQC (après trimming)</h4>
                    <p>Accédez au rapport MultiQC consolidé pour tous les échantillons après nettoyage Trimmomatic :</p>
                    <p><a href="FASTQC_apres/MultiQC_on_data_244,_data_218,_and_others__Webpage_html.html" target="_blank">Ouvrir le rapport MultiQC (après)</a></p>
                </div>
                <div class="report-explanation">
                    <h4>Résumé</h4>
                    <table>
                        <thead>
                            <tr>
                                <th>Indicateur</th>
                                <th>Statut</th>
                                <th>Résultat &amp; Conséquence</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>Qualité des Bases</td>
                                <td><span style="color:green; font-weight:bold;">BON (Vert)</span></td>
                                <td>La qualité reste excellente (Phred &gt; 30) sur toute la longueur des lectures. Aucune perte de qualité après le traitement.</td>
                            </tr>
                            <tr>
                                <td>Profondeur de Séquençage</td>
                                <td><span style="color:green; font-weight:bold;">BON (Vert)</span></td>
                                <td>Le nombre de lectures reste élevé (~26 à 70 millions/échantillon) malgré le filtrage. Suffisant pour l'analyse.</td>
                            </tr>
                            <tr>
                                <td>Duplication de Séquences</td>
                                <td><span style="color:red; font-weight:bold;">ÉCHEC (Rouge)</span></td>
                                <td>Toujours élevé. C'est normal : le trimming ne retire pas les duplicats PCR (cela nécessite une étape de déduplication spécifique si besoin).</td>
                            </tr>
                            <tr>
                                <td>Contenu en Adaptateurs</td>
                                <td><span style="color:orange; font-weight:bold;">CORRIGÉ (Jaune/Vert)</span></td>
                                <td>Problème résolu. Les courbes sont plates et proches de 0 %. Les adaptateurs ont été correctement coupés.</td>
                            </tr>
                            <tr>
                                <td>Distribution des Longueurs</td>
                                <td><span style="color:orange; font-weight:bold;">ALERTE (Orange)</span></td>
                                <td>Les lectures ont maintenant des tailles variables (plus seulement 100 bp), ce qui déclenche une alerte FastQC. C'est un bon signe : cela prouve que le trimming a coupé les parties de mauvaise qualité/adaptateurs.</td>
                            </tr>
                            <tr>
                                <td>Séquences Surreprésentées</td>
                                <td><span style="color:red; font-weight:bold;">ÉCHEC (Rouge)</span></td>
                                <td>Toujours présentes, principalement dues au taux de duplication élevé qui persiste.</td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>

        </section>

        <section id="Alignement des Reads sur le Génome de Référence">
        <h2>Alignement des Reads sur le Génome de Référence</h2>
            <p>L'alignement des reads sur le génome de référence humain (hg38) a été réalisé à l'aide de l'outil <strong>STAR</strong></p>
            <h3>Téléchargement du fichier d'annotation (GTF)</h3>
            <p>Le fichier d'annotation génique <strong>GENCODE</strong> (version 44, ensemble <em>basic</em> pour le génome humain <strong>GRCh38</strong>) a été téléchargé depuis le serveur FTP de l'EBI&nbsp;: 
                <a href="https://ftp.ebi.ac.uk/pub/databases/gencode/Gencode_human/release_44/" target="_blank">https://ftp.ebi.ac.uk/pub/databases/gencode/Gencode_human/release_44/</a>.
            </p>


            <div class="image-placeholder" style="min-height: 200px;">
               <img src="images/genecode.png" alt="gencode" style="max-width: 100%; max-height: 100%;">
            </div>
            <p>Le fichier a été téléversé manuellement dans l'interface Galaxy</p>

            <div class="image-placeholder" style="min-height: 10px;">
                <img src="images/genecode2.png" alt="gencode2" style="max-width: 100%; max-height: 100%;">
            </div>

            <h3>CONFIGURATION COMPLÈTE DE STAR</h3>

            <h4>A. Type de reads</h4>
            <p>Dans Galaxy, nous avons choisi comme type de données&nbsp;: <strong>Paired-end (as individual datasets)</strong>, indiquant que nous avons travaillé avec des lectures en paires R1/R2.</p>

            <h4>B. Sélection des fichiers (paired)</h4>
            <p>Pour <strong>chaque échantillon</strong>, nous avons associé explicitement les fichiers issus de Trimmomatic&nbsp;:</p>
            <ul>
                <li><strong>Forward reads</strong> : dans le champ <em>“RNA-Seq FASTQ/FASTA file, forward reads”</em>, nous avons sélectionné le fichier <strong>R1 paired</strong> (par ex. <em>Trimmomatic on SRR8507307: forward (R1 paired)</em>).</li>
                <li><strong>Reverse reads</strong> : dans le champ <em>“RNA-Seq FASTQ/FASTA file, reverse reads”</em>, nous avons sélectionné le fichier <strong>R2 paired</strong> (par ex. <em>Trimmomatic on SRR8507307: reverse (R2 paired)</em>).</li>

                <div class="image-placeholder" style="min-height: 10px;">
                    <img src="images/star1.png" alt="star1" style="max-width: 100%; max-height: 100%;">
                </div>
            </ul>

            <h4>C. Génome de référence</h4>
            <ul>
                <li>Dans <em>“Custom or built-in reference genome”</em>, nous avons choisi <strong>Use a built-in genome </strong>.</li>
                <li>Dans <em>“Reference genome with or without an annotation”</em>, nous avons sélectionné <strong>use genome reference without builtin gene-model but provide a gtf</strong>.</li>
                <li>Dans <em>“Select reference genome”</em>, nous avons recherché et choisi <strong>hg38 (Human Dec. 2013 GRCh38/hg38)</strong> ou <strong>Homo sapiens (hg38)</strong>.</li>

                <div class="image-placeholder" style="min-height: 10px;">
                    <img src="images/star2.png" alt="star2" style="max-width: 100%; max-height: 100%;">
                </div>
            </ul>
            <p><strong>Attention</strong> : nous avons vérifié systématiquement que le génome sélectionné correspondait bien à <strong>hg38 / GRCh38</strong> pour rester cohérents avec le fichier d’annotation GENCODE v44.</p>

            <h3>Résultats de l’alignement STAR</h3>
            <p>Pour <strong>chaque échantillon</strong>, nous obtenons <strong>3 fichiers de sortie</strong> après STAR:</p>

            <div class="image-placeholder" style="min-height: 10px;">
                <img src="images/Star.png" alt="Star" style="max-width: 100%; max-height: 100%;">
            </div>

            <ul>
                <li><strong>STAR on data 264, data 194, and data 193: mapped.bam</strong>  fichier binaire compressé contenant toutes les lectures RNA-seq qui ont été alignées avec succès sur le génome de référence.</li>
                <li><strong>RNA STAR on data 264, data 194, and data 193: splice junctions.bed</strong> liste des coordonnées génomiques de toutes les jonctions d’épissage détectées à partir des lectures.</li>
                <li><strong>RNA STAR on data 264, data 194, and data 193: log</strong> journal d’exécution complet de STAR, incluant les statistiques clés de qualité et de taux d’alignement.</li>
            </ul>

            <h3>STAR log files</h3>
            <ul>
                <li><a href="STAR/Galaxy265-[RNA STAR on data 264, data 186, and data 185_ log].text">Galaxy265 - log</a></li>
                <li><a href="STAR/Galaxy268-[RNA STAR on data 264, data 178, and data 177_ log].txt">Galaxy268 - log</a></li>
                <li><a href="STAR/Galaxy271-[RNA STAR on data 264, data 198, and data 197_ log].txt">Galaxy271 - log</a></li>
                <li><a href="STAR/Galaxy280-[RNA STAR on data 264, data 190, and data 189_ log].txt">Galaxy280 - log</a></li>
                <li><a href="STAR/Galaxy283-[RNA STAR on data 264, data 202, and data 201_ log].txt">Galaxy283 - log</a></li>
                <li><a href="STAR/Galaxy286-[RNA STAR on data 264, data 214, and data 213_ log].txt">Galaxy286 - log</a></li>
                <li><a href="STAR/Galaxy292-[RNA STAR on data 264, data 182, and data 181_ log].txt">Galaxy292 - log</a></li>
                <li><a href="STAR/Galaxy295-[RNA STAR on data 264, data 206, and data 205_ log].txt">Galaxy295 - log</a></li>
                <li><a href="STAR/Galaxy298-[RNA STAR on data 264, data 210, and data 209_ log].txt">Galaxy298 - log</a></li>
                <li><a href="STAR/Galaxy301-[RNA STAR on data 264, data 194, and data 193_ log].txt">Galaxy301 - log</a></li>
            </ul>
        </section>


        <section id="Quantification de l'Expression des Gènes">
            <h2>Quantification de l'Expression des Gènes avec featureCounts</h2>
            <h3>CONFIGURATION COMPLÈTE</h3>
            <h4>A. Fichiers BAM à analyser</h4>
            <p>Dans le champ <em>Alignment file</em>, nous avons cliqué sur l’icône « multiple datasets » puis sélectionné nos 10 fichiers BAM (mapped.bam) :</p>
            <ul>
                <li>RNA STAR...: mapped.bam</li>
                <li>RNA STAR...: mapped.bam</li>
                <li>RNA STAR...: mapped.bam</li>
                <li>... et les autres mapped.bam</li>
            </ul>
            <p><strong>Total</strong> : 10 fichiers BAM.</p>

            <div class="image-placeholder" style="min-height: 10px;">
                <img src="images/featurecounts1.png" alt="featurecounts1" style="max-width: 100%; max-height: 100%;">
            </div>

            <h4>B. Fichier d’annotation (GTF)</h4>
            <p>Dans <em>Gene annotation file</em>, nous avons  sélectionné le fichier <strong>d’annotation GENCODE v44.</strong>.</p>

            <h3>Résultats de featureCounts</h3>
            <p>Nous avons obtenu 2 fichiers principaux en sortie:</p>

            <div class="image-placeholder" style="min-height: 10px;">
                <img src="images/featurcountsres.png" alt="featurcountsresult" style="max-width: 100%; max-height: 100%;">
            </div>

            <ul>
                <li><strong>featureCounts on data 264 and data 288: Summary</strong>  fichier de résumé statistique détaillé indiquant le nombre de lectures assignées avec succès aux gènes et le nombre de lectures non assignées, ainsi que les raisons de cette non-attribution.</li><br>

                <div class="image-placeholder" style="min-height: 10px;">
                    <img src="images/summary.png" alt="summary" style="max-width: 100%; max-height: 100%;">
                </div>

                <li><strong>featureCounts on data 264 and data 288: Counts</strong>  fichier de matrice de comptage, où chaque valeur correspond au nombre brut de lectures assignées à chaque gène (ou feature) pour chaque échantillon.</li>
                <div class="image-placeholder" style="min-height: 10px;">
                    <img src="images/counts.png" alt="Counts" style="max-width: 100%; max-height: 100%;">
                </div>
            </ul>

        </section>

        <section id="Analyse d'Expression Différentielle">
        <h2>Analyse d'Expression Différentielle</h2>
        <h1>DESeq2</h1>
        <p>L'outil DESeq2 est utilisé pour normaliser la matrice de comptage et déterminer les gènes significativement exprimés différemment entre les conditions.</p><br>
        <p><strong>Péparation de l'entrée :</strong> L'outil DESeq2 nécessite en entrée la matrice de comptage brute (Counts) générée précédemment par featureCounts .</p>
        
        <h3>Étape A : Configuration des Paramètres d'Entrée</h3>
        <ul>
            <li><strong>Définition du Facteur (Factor)</strong> : le facteur biologique principal a été spécifié (ex. : <em>tissue</em>).</li>

            <div class="image-placeholder" style="min-height: 10px;">
                <img src="images/Deseq2_1.png" alt="Deseq2_1" style="max-width: 100%; max-height: 100%;">
            </div>

            <li><strong>Spécification des Niveaux de Facteur (Conditions)</strong> :
                <ul>
                    <li><strong>Niveau 1 (Référence)</strong> : condition de référence définie (ex. : <em>control</em>) et association des fichiers de comptage correspondants (ex. : 511, 510).</li>

                    <div class="image-placeholder" style="min-height: 10px;">
                        <img src="images/Deseq2_2.png" alt="Deseq2_2" style="max-width: 100%; max-height: 100%;">
                    </div>


                    <li><strong>Niveau 2 (Comparaison)</strong> : condition à comparer (ex. : <em>tumor</em>) avec association des fichiers de comptage correspondants (ex. : 508, 507, etc.).</li>

                    <div class="image-placeholder" style="min-height: 10px;">
                        <img src="images/Deseq2_3.png" alt="Deseq2_3" style="max-width: 100%; max-height: 100%;">
                    </div>

                </ul>
            </li>
        </ul>

        <h3>Étape B : Configuration des Options de Sortie</h3>
        <ul>
            <li><strong>Plots (Generate plots)</strong> : activé pour générer les visualisations (ex. : MA Plot).</li><br>
            <li><strong>Normalized counts (Output normalised counts)</strong> : activé pour obtenir la matrice de comptage ajustée par les facteurs de taille DESeq2.</li><br>
            <li><strong>VST-Normalized table (Output VST normalized table)</strong> : activé pour produire les comptages transformés par Variance Stabilizing Transformation, utiles pour PCA/analyses exploratoires.</li><br>
            <li><strong>rLog-Normalized table (Output rLog normalized table)</strong> : activé pour produire les comptages transformés par Regularized Logarithm, utiles pour visualisation et clustering.</li>

            <div class="image-placeholder" style="min-height: 10px;">
                <img src="images/Deseq2_output.png" alt="Deseq2_output" style="max-width: 100%; max-height: 100%;">
            </div>

        </ul>

        <h3>Résultats</h3>
        <p><strong>Fichiers de sortie générés :</strong></p>
        <ul>

            <div class="image-placeholder" style="min-height: 10px;">
                <img src="images/Deseq2results.png" alt="Deseq2results" style="max-width: 100%; max-height: 100%;">
            </div>

            <li><strong>513: DESeq2 result file</strong> : tableau principal des résultats (log2 fold change, p-value brute, p-value ajustée).</li><br>

            <div class="image-placeholder" style="min-height: 10px;">
                <img src="images/result.png" alt="result" style="max-width: 100%; max-height: 100%;">
            </div>

            <li><strong>514: DESeq2 plots</strong> : visualisations graphiques (Volcano Plot, MA Plot) pour interpréter les résultats. <a href="Deseq2/Galaxy514-[DESeq2 plots on data 508, data 507, and others].pdf" target="_blank">Ouvrir le PDF</a></li><br>
            <li><strong>515: Normalized counts file</strong> : matrice de comptage normalisée par les facteurs de taille DESeq2.</li><br>
            <li><strong>516: rLog-Normalized counts file</strong> : matrice transformée par Regularized Logarithm (rLog), utile pour clustering/PCA.</li><br>
            <li><strong>517: VST-Normalized counts file</strong> : matrice transformée par Variance Stabilizing Transformation (VST), utile pour analyses exploratoires.</li>
        </ul>

        </section>

        <section id="Analyses Fonctionnelles et Interprétation Biologique">

            <h2>Analyses Fonctionnelles et Interprétation Biologique</h2>
               <h1>clusterProfiler</h1>
               <h3>Préparation de l'Environnement et Outils R</h3>
               <p>Pour exécuter les analyses statistiques et fonctionnelles, l'environnement logiciel suivant a été utilisé :</p>
                <table>
                    <thead>
                        <tr>
                            <th>Composant</th>
                            <th>Version recommandée</th>
                            <th>Rôle</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>Langage R</td>
                            <td>R = 4.3</td>
                            <td>Moteur statistique et de calcul.</td>
                        </tr>
                        <tr>
                            <td>RStudio</td>
                            <td>RStudio Desktop = 2025.09</td>
                            <td>Interface de développement intégrée (IDE) pour l'exécution des scripts R.</td>
                        </tr>
                    </tbody>
                </table>

                <h3>Installation des Packages Clés</h3>
                <p>Les analyses reposent sur l'installation de packages R issus de CRAN (pour WGCNA) et de Bioconductor (pour DESeq2 et clusterProfiler).</p>

                <div class="image-placeholder" style="min-height: 10px;">
                    <img src="images/package.png" alt="package" style="max-width: 100%; max-height: 100%;">
                </div>
                <h3>Initialiser et préparer les données</h3>
                 <pre><code># 1. Load libraries
library(clusterProfiler)
library(org.Hs.eg.db)
library(dplyr)

# 2. Set Directory
setwd("/home/zakaria/Desktop/M2 Bioinformatique/Transcriptome et Génomique Appliquée/Dataset/GSE125903/")

# 3. Load and Clean Data
stats_df <- read.delim("DESeq2/deseq2_stats.tsv", header = FALSE)
ids_df   <- read.delim("DESeq2/annotation_map.tsv")

colnames(stats_df) <- c("GeneID", "baseMean", "log2FoldChange", "lfcSE", "stat", "pvalue", "padj")
stats_df$GeneID <- gsub("\\..*", "", stats_df$GeneID)
ids_df$ENSEMBL  <- gsub("\\..*", "", ids_df$ENSEMBL)

# 4. Merge and extract Upregulated Entrez IDs
merged_data <- inner_join(stats_df, ids_df, by = c("GeneID" = "ENSEMBL"))

genes_up_entrez <- merged_data %>% 
  filter(padj < 0.05 & log2FoldChange > 0) %>%
  filter(!is.na(ENTREZID)) %>%
  pull(ENTREZID)</code></pre>
               



              <h3>Processus Biologiques : Gene Ontology (GO).</h3>
              <div class="image-placeholder" style="min-height: 10px;">
                <img src="images/go.png" alt="go" style="max-width: 100%; max-height: 100%;">
            </div>

              <h3>Resultats</h3>

             <div class="image-placeholder" style="min-height: 10px;">
                <img src="images/GO_BP_Dotplot.png" alt="GO_BP_Dotplot" style="max-width: 100%; max-height: 100%;">
            </div>

              <h3>Voies Biologiques : Base de données KEGG, Reactome.</h3>
              <div class="image-placeholder" style="min-height: 10px;">
                <img src="images/KEGG.png" alt="KEGG" style="max-width: 100%; max-height: 100%;">
            </div>

              <h3>Resultats</h3>
              <div class="image-placeholder" style="min-height: 10px;">
                <img src="images/KEGG result.png" alt="KEGG result" style="max-width: 100%; max-height: 100%;">
            </div>

             <h3>Signatures de Cellules Immunitaires : MSigDB (module C7).</h3>
             <pre><code># 1. Charger les bibliothèques nécessaires
library(clusterProfiler)
library(org.Hs.eg.db)
library(dplyr)

# 2. Définir le chemin (Working Directory)
setwd("/home/zakaria/Desktop/M2 Bioinformatique/Transcriptome et Génomique Appliquée/Dataset/GSE125903/")

# 3. Ré-importer les fichiers de données (Ajustez les noms si nécessaire)
# On suppose que vos fichiers sont dans le dossier actuel
stats_df <- read.delim("DESeq2/deseq2_stats.tsv", header = FALSE)
ids_df   <- read.delim("DESeq2/annotation_map.tsv")

# 4. Nettoyage et Préparation des données
colnames(stats_df) <- c("GeneID", "baseMean", "log2FoldChange", "lfcSE", "stat", "pvalue", "padj")

# Supprimer les versions des IDs Ensembl (ex: ENSG000001.5 -> ENSG000001)
stats_df$GeneID <- gsub("\\..*", "", stats_df$GeneID)
ids_df$ENSEMBL  <- gsub("\\..*", "", ids_df$ENSEMBL)

# Fusionner les stats avec les IDs Entrez
merged_data <- inner_join(stats_df, ids_df, by = c("GeneID" = "ENSEMBL"))

# 5. Créer l'objet manquant : genes_up_entrez
genes_up_entrez <- merged_data %>% 
  filter(padj < 0.05 & log2FoldChange > 0) %>%
  filter(!is.na(ENTREZID)) %>%
  pull(ENTREZID)

# 6. Lancer l'analyse MSigDB C7 (avec votre fichier de 6Mo)
c7_gmt <- read.gmt("c7.all.v2023.2.Hs.entrez.gmt")
msig_res <- enricher(gene = genes_up_entrez, 
                     TERM2GENE = c7_gmt, 
                     pvalueCutoff = 0.05)

# 7. Afficher le résultat
dotplot(msig_res, showCategory=10, title="Upregulated Immunologic Signatures (C7)")</code></pre>
              <h3>Resultats</h3>

              <div class="image-placeholder" style="min-height: 10px;">
                <img src="images/MSigDB_C7_Dotplot.png" alt="MSigDB_C7_Dotplot" style="max-width: 100%; max-height: 100%;">
            </div>
                 <h1>EPIC</h1>
                 <pre><code># 1. Charger les bibliothèques
library(EPIC)
library(dplyr)
library(tidyr)
library(tibble)
library(ggplot2)

# Définir le répertoire de travail
setwd("/home/zakaria/Desktop/M2 Bioinformatique/Transcriptome et Génomique Appliquée/Dataset/GSE125903/")

# ==============================================================================
# 1. PRÉPARATION ET FUSION DES COMPTAGES INDIVIDUELS (Inchangé)
# ==============================================================================

file_list_control <- list.files("Epic/control/", pattern = "\\.tsv$|\\.txt$", full.names = TRUE)
file_list_tumor   <- list.files("Epic/tumor/", pattern = "\\.tsv$|\\.txt$", full.names = TRUE)
file_list <- c(file_list_control, file_list_tumor)

full_counts_matrix <- data.frame(row.names = NULL)
for (file in file_list) {
  # Lecture du fichier : header=FALSE, 2 colonnes (ID Gène, Compte)
  current_counts <- read.delim(file, header = FALSE, col.names = c("GeneID", "Count"))
  
  dir_name <- basename(dirname(file)) 
  sample_name <- basename(file)
  new_col_name <- paste0(dir_name, "_", gsub("\\..*", "", sample_name))
  
  current_counts <- current_counts %>% 
    select(GeneID, Count) %>%
    column_to_rownames("GeneID")
  colnames(current_counts) <- new_col_name

  if (nrow(full_counts_matrix) == 0) {
    full_counts_matrix <- current_counts
  } else {
    full_counts_matrix <- merge(full_counts_matrix, current_counts, by = "row.names", all = TRUE)
    rownames(full_counts_matrix) <- full_counts_matrix$Row.names
    full_counts_matrix$Row.names <- NULL
  }
}
full_counts_matrix[is.na(full_counts_matrix)] <- 0
print(paste("Matrice de comptage fusionnée créée avec succès (", ncol(full_counts_matrix), " échantillons)."))

# SAUVEGARDE de la Matrice Fusionnée 
write.csv(full_counts_matrix, "GSE125903_Full_Merged_Counts_for_EPIC.csv")
print("Matrice de comptage fusionnée sauvegardée au format CSV.")

# ==============================================================================
# 2. CONVERSION D'ID VERS SYMBOLE (CORRECTION AVEC CONVERSION NUMÉRIQUE)
# ==============================================================================

# 1. Charger le fichier d'annotation
annotation_map <- read.delim("DESeq2/annotation_map.tsv")
annotation_map$ENSEMBL <- gsub("\\..*", "", annotation_map$ENSEMBL)

# 2. Préparer la Matrice pour la Fusion
full_counts_matrix <- full_counts_matrix %>% 
  rownames_to_column("ENSEMBL") %>%
  mutate(ENSEMBL = gsub("\\..*", "", ENSEMBL))

# 3. Fusionner pour ajouter les Symboles de Gènes
mapped_matrix <- inner_join(annotation_map, full_counts_matrix, by = "ENSEMBL")

# 4. Finaliser la Matrice EPIC (CORRECTION ICI : Forcer le type numérique)
epic_input_matrix <- mapped_matrix %>%
  filter(SYMBOL != "") %>% 
  
  # Forcer les colonnes d'échantillons à être de type numérique avant de sommer
  # mutate(across(...)) nécessite d'identifier les colonnes de comptage 
  mutate(across(starts_with(c("control_", "tumor_")), as.numeric)) %>%
  
  group_by(SYMBOL) %>%
  
  # Nouvelle fonction summarise : Appliquer sum UNIQUEMENT aux colonnes de comptage
  summarise(across(starts_with(c("control_", "tumor_")), sum)) %>%
  column_to_rownames("SYMBOL")

print(paste("Matrice EPIC prête avec", nrow(epic_input_matrix), "Symboles de Gènes."))

# ==============================================================================
# 3. ANALYSE EPIC ET SAUVEGARDE (Inchangé)
# ==============================================================================

# Lancer la Déconvolution
epic_results <- EPIC(bulk = as.matrix(epic_input_matrix), reference = "TRef")
cell_fractions <- epic_results$cellFractions

# Sauvegarde des résultats numériques de déconvolution
write.csv(cell_fractions, "Epic/Resultats_Deconvolution_EPIC.csv")

# Visualisation Barplot
df_plot <- as.data.frame(cell_fractions) %>%
  rownames_to_column("Sample") %>%
  pivot_longer(cols = -Sample, names_to = "CellType", values_to = "Proportion")

plot_deconv <- ggplot(df_plot, aes(x = Sample, y = Proportion, fill = CellType)) +
  geom_bar(stat = "identity") +
  theme_minimal() +
  labs(title = "Estimation des Populations Cellulaires (EPIC) - GSE125903",
       y = "Proportion",
       x = "Échantillons") +
  theme(axis.text.x = element_text(angle = 45, hjust = 1)) +
  scale_fill_brewer(palette = "Set1")

# Sauvegarde du graphique de déconvolution
ggsave("Epic/Deconvolution_EPIC_Barplot.png", plot = plot_deconv, width = 12, height = 8)

print("Analyse de Déconvolution EPIC terminée. Graphique et table de résultats sauvegardés.")</code></pre>


            <h3>Resultats</h3>

            <div class="image-placeholder" style="min-height: 10px;">
                <img src="images/Deconvolution_EPIC_Barplot.png" alt="Deconvolution_EPIC_Barplot" style="max-width: 100%; max-height: 100%;">
            </div>

             <table>
                 <thead>
                     <tr>
                         <th>Type Cellulaire</th>
                         <th>Description</th>
                         <th>Contrôles (2 premiers échantillons)</th>
                         <th>Tumeurs (5 derniers échantillons)</th>
                         <th>Tendance</th>
                     </tr>
                 </thead>
                 <tbody>
                     <tr style="background-color:#FFF2CC;">
                         <td><strong>Macrophages (Jaune)</strong></td>
                         <td>Représente les Microglies dans la rétine.</td>
                         <td>Très faible ou absent.</td>
                         <td>Clairement présent dans presque toutes les tumeurs.</td>
                         <td><span style="color:#d35400; font-weight:bold;">Augmentation</span></td>
                     </tr>
                     <tr style="background-color:#FFE699;">
                         <td><strong>Endothelial (Orange)</strong></td>
                         <td>Cellules des vaisseaux sanguins.</td>
                         <td>Présent, mais faible.</td>
                         <td>Augmentation notable (surtout tumor_SRR8507306_tumor).</td>
                         <td><span style="color:#d35400; font-weight:bold;">Augmentation (Angiogenèse)</span></td>
                     </tr>
                     <tr style="background-color:#E2F0D9;">
                         <td><strong>CAFs (Vert)</strong></td>
                         <td>Fibroblastes Associés au Cancer (Stromaux).</td>
                         <td>Faible.</td>
                         <td>Présent et légèrement variable dans les tumeurs.</td>
                         <td><span style="color:#27ae60; font-weight:bold;">Augmentation</span></td>
                     </tr>
                     <tr style="background-color:#EDE7F6;">
                         <td><strong>CD8_Tcells (Violet)</strong></td>
                         <td>Lymphocytes T Cytotoxiques.</td>
                         <td>Très faible.</td>
                         <td>Faible, mais visible dans certaines tumeurs.</td>
                         <td><span style="color:#8e44ad; font-weight:bold;">Stable/Faible</span></td>
                     </tr>
                 </tbody>
             </table>

        </section>
        <section id="WGCNA">
            <h2>Analyse Avancée : Réseaux de Co-Expression</h2>
            <h1>Weighted Gene Co-Expression Network Analysis (WGCNA)</h1>
            <h3>WGCNA</h3>
            <pre><code># ==============================================================================
# PARTIE E : ANALYSE DES RÉSEAUX DE CO-EXPRESSION (WGCNA) - NETTOYAGE DÉSACTIVÉ
# ==============================================================================

# 1. Charger les bibliothèques
library(WGCNA)
library(dplyr)
library(tibble)

# 1b. Définir le répertoire de travail
setwd("~/Desktop/M2 Bioinformatique/Transcriptome et Génomique Appliquée/TP/Dataset/GSE125903")

# Permettre l'exécution du multithreading
enableWGCNAThreads() 

# ==============================================================================
# 2. PRÉPARATION ET NETTOYAGE DES DONNÉES
# ==============================================================================

# Charger la matrice de comptage fusionnée
epic_input_matrix <- read.csv("GSE125903_Full_Merged_Counts_for_EPIC.csv", row.names = 1) 

# Transposition (Échantillons en lignes, Gènes en colonnes)
datExpr <- as.data.frame(t(epic_input_matrix))

# Conversion forcée de TOUTES les colonnes en numérique 
datExpr[] <- lapply(datExpr, as.numeric) 

# Nettoyage des données (DÉSACTIVÉ)
# Nous désactivons cette étape car N=7 est trop petit et le nettoyage supprime trop d'échantillons.
# gsg = goodSamplesGenes(datExpr, verbose = 3)
# if (!gsg$allOK) {
#   datExpr = datExpr[gsg$magoodSamples, gsg$maGegenes]
# }
# Pour un petit N, il est préférable de ne pas nettoyer à ce stade, quitte à avoir plus de bruit.

print(paste("Matrice d'expression prête avec", nrow(datExpr), "échantillons."))


# 3. Création du Trait Clinique (Trait)
sampleNames = rownames(datExpr)
traitData = data.frame(
  Sample = sampleNames,
  Condition = ifelse(grepl("tumor", sampleNames), 1, 0) 
)
row.names(traitData) = sampleNames
datTraits = traitData %>% 
  select(Condition) %>%
  as.matrix()


# ==============================================================================
# 4. CONSTRUCTION DU RÉSEAU ET IDENTIFICATION DES MODULES
# ==============================================================================

# Étape A : Choix du paramètre d'échelle doux (Soft Threshold Power, beta)
powers = c(c(1:10), seq(from = 12, to = 20, by = 2))
# CECI PEUT PRENDRE QUELQUES MINUTES
sft = pickSoftThreshold(datExpr, powerVector = powers, verbose = 5) 

# Visualisation du choix de Beta (pour le rapport)
png("Epic/WGCNA_SoftThreshold_Plot.png", width = 900, height = 500)
par(mfrow = c(1,2))
plot(sft$fitIndices[, 1], -sign(sft$fitIndices[, 3]) * sft$fitIndices[, 2],
     xlab = "Soft Threshold Power (beta)", ylab = "Scale Free Topology Model Fit, R^2",
     type = "n", main = paste("Scale independence"))
text(sft$fitIndices[, 1], -sign(sft$fitIndices[, 3]) * sft$fitIndices[, 2],
     labels = powers, col = "red", cex = 0.9)
abline(h = 0.85, col = "red") 
plot(sft$fitIndices[, 1], sft$fitIndices[, 5],
     xlab = "Soft Threshold Power (beta)", ylab = "Mean Connectivity",
     type = "n", main = paste("Mean connectivity"))
text(sft$fitIndices[, 1], sft$fitIndices[, 5], labels = powers, col = "red", cex = 0.9)
dev.off()


# Étape B : Définir le Beta optimal
softPower = sft$powerEstimate 
if (is.na(softPower)) {
  softPower = 8 
  print(paste("Estimation de softPower échouée ou non trouvée, en utilisant la valeur par défaut :", softPower))
} else {
  print(paste("Soft power optimal sélectionné :", softPower))
}


# Étape C : Construction du réseau et identification des modules
net = blockwiseModules(
  datExpr, 
  power = softPower,
  maxBlockSize = 6000, 
  TOMType = "unsigned", 
  minModuleSize = 30,
  reassignThreshold = 0, 
  mergeCutHeight = 0.25,
  numericLabels = TRUE, 
  pamRespectsDendro = FALSE,
  verbose = 3
)

# Sauvegarder les résultats WGCNA
save(net, datExpr, datTraits, softPower, file = "Epic/WGCNA_Network_Results.RData")

# ==============================================================================
# 5. CORRÉLATION DES MODULES AVEC LE TRAIT CLINIQUE 
# ==============================================================================

moduleColors = labels2colors(net$colors)
MEs = net$MEs 
moduleTraitCor = cor(MEs, datTraits, use = "p")
moduleTraitPvalue = corPvalueStudent(moduleTraitCor, nrow(datExpr))

# 6. Visualisation de la Corrélation Module-Trait
png("Epic/WGCNA_ModuleTrait_Heatmap.png", width = 1000, height = 800)
textMatrix = paste(signif(moduleTraitCor, 2), "\n(", signif(moduleTraitPvalue, 1), ")", sep = "")
dim(textMatrix) = dim(moduleTraitCor)


par(mar = c(6, 8.5, 3, 3))
labeledHeatmap(
  Matrix = moduleTraitCor,
  xLabels = colnames(datTraits),
  yLabels = names(MEs),
  ySymbols = names(MEs),
  colorLabels = FALSE,
  colors = blueWhiteRed(50),
  textMatrix = textMatrix,
  setStdMargins = FALSE,
  cex.text = 0.8,
  zlim = c(-1, 1),
  main = paste("Corrélation Module Eigengenes et Condition Clinique (Tumeur/Contrôle)")
)
dev.off()

print("Analyse WGCNA terminée. Veuillez consulter 'Epic/WGCNA_ModuleTrait_Heatmap.png'.")</code></pre>
           <h3>Resultats</h3>

           <div class="image-placeholder" style="min-height: 10px;">
            <img src="images/WGCNA_SoftThreshold_Plot.png" alt="WGCNA_SoftThreshold_Plot" style="max-width: 100%; max-height: 100%;">
        </div>
        <div class="image-placeholder" style="min-height: 10px;">
            <img src="images/WGCNA_Heatmap_Final.png" alt="WGCNA_Heatmap_Final" style="max-width: 100%; max-height: 100%;">
        </div>
        <h3 style="color:#214e7a;">Le Résultat Clé : Le Module ME1</h3>
        <p><strong>Corrélation forte (-0.88)</strong> : le coefficient de corrélation entre le module ME1 et le statut tumoral est de -0.88, indiquant une relation négative très puissante (proche de -1).</p>
        <p><strong>Significativité (p-value = 0.01)</strong> : la valeur p associée (0.01) est inférieure au seuil de 0.05, ce qui rend cette corrélation statistiquement significative.</p>

        <h3 style="color:#7ab971;">Interprétation Biologique</h3>
        <p>Une <strong>corrélation négative</strong> de -0.88 signifie que lorsque l’on passe de la condition contrôle à la condition tumeur, l’expression des gènes de ce module diminue de manière drastique.</p>
        <p><strong>Conclusion</strong> : le Module 1 (ME1) regroupe des gènes fortement exprimés dans le tissu sain (rétine normale) mais largement éteints ou perdus dans la tumeur.</p>
        <p><strong>Hypothèse</strong> : ce module contient vraisemblablement des gènes liés aux fonctions normales de l’œil (photoréception, transmission neuronale) que les cellules cancéreuses perdent en se dédifférenciant.</p>
        <h3 style="color:#e05b5b;">Les Autres Modules</h3>
        <p><strong>ME3 et ME2 (couleur saumon)</strong> : présentent une corrélation positive modérée (~0,39 et ~0,35), suggérant une possible sur-expression dans la tumeur, mais leurs p-values élevées (~0,4) indiquent une absence de significativité statistique. Nous ne pouvons donc rien conclure de fiable à leur sujet.</p>
        <p><strong>ME0, ME4, ME5, ME6</strong> : ne montrent aucune corrélation significative avec la condition tumeur/contrôle et ne sont pas interprétés davantage.</p>

         <h1>Dernière étape : Extraire les gènes du Module 1</h1>

         <div class="image-placeholder" style="min-height: 10px;">
            <img src="images/m1.png" alt="m1" style="max-width: 100%; max-height: 100%;">
        </div>

        <h3>Resultats</h3>

        <div class="image-placeholder" style="min-height: 10px;">
            <img src="images/m1_genes.png" alt="m1_genes" style="max-width: 100%; max-height: 100%;">
        </div>
        <h3>Convertir les IDs en Noms de Gènes</h3>
        <pre><code># ==============================================================================
# CONVERSION DES ENSEMBL IDs EN SYMBOLES (Human Readable)
# ==============================================================================

library(org.Hs.eg.db)
library(AnnotationDbi)

# 1. Nettoyer les IDs (Retirer les versions .5, .16 à la fin des ENSG)
# Votre liste s'appelle 'genes_in_ME1'
clean_ids <- sub("\\..*", "", genes_in_ME1)

# 2. Convertir en Symboles de gènes
gene_symbols <- mapIds(
  org.Hs.eg.db,
  keys = clean_ids,
  column = "SYMBOL",
  keytype = "ENSEMBL",
  multiVals = "first"
)

# 3. Créer un tableau propre avec ID et Symbole
results_table <- data.frame(
  Ensembl_ID = clean_ids,
  Gene_Symbol = gene_symbols
)

# 4. Afficher les 20 premiers résultats pour confirmer
print("Voici les gènes identifiés dans le module clé :")
print(head(results_table, 20))

# 5. Sauvegarder ce tableau final pour votre rapport
write.csv(results_table, "Epic/FINAL_Module_ME1_Genes_Identifies.csv", row.names = FALSE)

print("Fichier sauvegardé : 'Epic/FINAL_Module_ME1_Genes_Identifies.csv'")</code></pre>


           <h3>Resultats</h3>
           <table>
               <thead>
                   <tr>
                       <th>Ensembl_ID</th>
                       <th>Gene_Symbol</th>
                   </tr>
               </thead>
               <tbody>
                   <tr><td>ENSG00000163914</td><td>RHO</td></tr>
                   <tr><td>ENSG00000091513</td><td>TF</td></tr>
                   <tr><td>ENSG00000130561</td><td>SAG</td></tr>
                   <tr><td>ENSG00000114349</td><td>GNAT1</td></tr>
                   <tr><td>ENSG00000211445</td><td>GPX3</td></tr>
                   <tr><td>ENSG00000265203</td><td>RBP3</td></tr>
                   <tr><td>ENSG00000132915</td><td>PDE6A</td></tr>
                   <tr><td>ENSG00000185527</td><td>PDE6G</td></tr>
                   <tr><td>ENSG00000135821</td><td>GLUL</td></tr>
                   <tr><td>ENSG00000129221</td><td>AIPL1</td></tr>
                   <tr><td>ENSG00000129535</td><td>NRL</td></tr>
                   <tr><td>ENSG00000109103</td><td>UNC119</td></tr>
                   <tr><td>ENSG00000120885</td><td>CLU</td></tr>
                   <tr><td>ENSG00000149489</td><td>ROM1</td></tr>
                   <tr><td>ENSG00000078369</td><td>GNB1</td></tr>
                   <tr><td>ENSG00000112706</td><td>IMPG1</td></tr>
                   <tr><td>ENSG00000166165</td><td>CKB</td></tr>
                   <tr><td>ENSG00000111674</td><td>ENO2</td></tr>
                   <tr><td>ENSG00000150991</td><td>UBC</td></tr>
                   <tr><td>ENSG00000109047</td><td>RCVRN</td></tr>
               </tbody>
           </table>

            <p>La colonne Gene_Symbol confirme l'interprétation du module ME1 (corrélation -0.88 avec la tumeur) : il s'agit d'un programme transcriptionnel de photorécepteur normal qui est éteint dans le rétinoblastome.</p><br>
            
            <h1>Interprétation Biologique des Gènes Clés</h1>
            <table>
                <thead>
                    <tr>
                        <th>Symbole du Gène</th>
                        <th>Rôle Biologique (Rétine)</th>
                        <th>Pertinence pour le Rétinoblastome</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>RHO</td>
                        <td>Rhodopsine, le pigment essentiel pour la vision dans les bâtonnets.</td>
                        <td>Marqueur de la dédifférenciation. La perte de RHO est un signe classique que la cellule a abandonné sa fonction rétinienne.</td>
                    </tr>
                    <tr>
                        <td>SAG</td>
                        <td>S-Arrestine (ou Arrestin-1). Protéine essentielle pour l'arrêt de la cascade de phototransduction.</td>
                        <td>Fait partie intégrante du cycle de la phototransduction. Sa perte prouve l'inactivation de la voie.</td>
                    </tr>
                    <tr>
                        <td>GNAT1</td>
                        <td>Sous-unité alpha de la transducine. Fait la liaison entre RHO et la phosphodiestérase (PDE).</td>
                        <td>Élément clé de la cascade de signalisation de la vision.</td>
                    </tr>
                    <tr>
                        <td>PDE6A / PDE6G</td>
                        <td>Phosphodiestérase 6. Hydrolyse le cGMP lors de la phototransduction, fermant les canaux ioniques.</td>
                        <td>Essentiel à la réponse cellulaire à la lumière.</td>
                    </tr>
                    <tr>
                        <td>AIPL1</td>
                        <td>Aryl Hydrocarbon Receptor Interacting Protein-Like 1. Impliqué dans la maturation des PDE.</td>
                        <td>Souvent muté dans les cécités héréditaires (Amaurose de Leber).</td>
                    </tr>
                    <tr>
                        <td>NRL</td>
                        <td>Neuronal Retina Leucine Zipper. Facteur de transcription clé qui régule le développement et la fonction des bâtonnets.</td>
                        <td>Régulateur principal de la plupart des gènes ci-dessus. Sa perte bloque l'identité des bâtonnets.</td>
                    </tr>
                </tbody>
            </table>
            











       
        </section>



        <section id="conclusion">
            <h2>Conclusion</h2>
            <div style="background: #f0f8ff; padding: 15px; border-left: 5px solid #214e7a; font-size: 1.1em;">
                <p>Le module ME1 (corrélation -0,88, p = 0,01) représente le programme de gènes le plus significativement régulé par la condition tumorale.</p>
                <p><strong>Le cœur des photorécepteurs</strong> : la présence massive de gènes de la cascade de phototransduction (RHO, SAG, GNAT1, PDE6A/G) et de leurs régulateurs principaux (NRL) démontre que ce module code pour la fonction des bâtonnets (photorécepteurs).</p>
                <p><strong>Perte d’identité</strong> : la corrélation négative indique que cette signature est éteinte ou drastiquement réduite dans les cellules du rétinoblastome. Ce phénomène traduit la dédifférenciation, où les cellules tumorales perdent leur fonction spécialisée (vision) pour se concentrer sur la prolifération.</p>
                <p>Ces résultats suggèrent que les gènes du module ME1 pourraient être utilisés comme <strong>biomarqueurs</strong> pour suivre le niveau de dédifférenciation ou l’agressivité de la tumeur.</p>
            </div>
        </section>

    </div>
</body>
</html>
