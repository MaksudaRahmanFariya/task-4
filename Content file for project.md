<p>In this project we mainly calculated the similarity between two paragraphs . We gave two paragraphs  as input  in html format , generated a list of 5 keywords for individual paragraphs , then counted the number of similar keywords and percentage of similarities .
</p>


<p>We used a pre-trained BRET model for training our data/paragraphs . And we had to import some packages , tokenize , select stop word.</p>
<p>Then we built a function:</p>

<p>def func(d1,d2):</p>
    <p>count1 = CountVectorizer(ngram_range=n_gram_range, stop_words=stop_words).fit([d1])</p>
    <p>count2 = CountVectorizer(ngram_range=n_gram_range, stop_words=stop_words).fit([d2])<p>
    <p>candidates1 = count1.get_feature_names()</p>
    <p>candidates2 = count2.get_feature_names()</p>
    <p>doc_embedding1 = model.encode([d1])</p>
    <p>doc_embedding2 = model.encode([d2])</p>
    <p>candidate_embeddings1 = model.encode(candidates1)</p>
    <p>candidate_embeddings2 = model.encode(candidates2)</p>
    <p>distances1 = cosine_similarity(doc_embedding1, candidate_embeddings1)</p>
    <p>distances2 = cosine_similarity(doc_embedding2, candidate_embeddings2)</p>
    <p>keywords1 = [candidates1[index] for index in distances1.argsort()[0][-top_n:]] words</p>
    <p>keywords2 = [candidates2[index] for index in distances2.argsort()[0][-top_n:]]</p>
    <p>sc=0</p>
    <p>for i in keywords1:</p>
        <p>for j in keywords2:</p>
            <p>if i==j:</p>
                <p>sc+=1</p>
    <p>return(sc)</p>
    
    <p>We removed our stop  words, extracted features , encoded them then tried to measure similarities using cosine_similaritis method .</p>
    <img scr='unnamed.png' alt = 'Image'>
    <p>We would get the output like that</p>
    <h3>How to RUN the project</h3>
    <ol><li>Make a new folder named 'templates' inside the project directory, after downloading the project folder.</li>
<li>Move the 'upload.html' file from project directory to 'templates' folder.</li>
<li>Install the python packages as mentioned in the 'dependencies.txt' file.</li>
<li>Now run the 'main.py' file.</li>
<li>Input two paragraphs which are needed to be compared and click on 'Upload' button.</li>
<li>Score will be generated, based on number of keywords which are same for both paragraphs, based on list of top 5 keywords of each paragraph</li></ol>




