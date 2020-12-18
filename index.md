
 
<html>
      <p style="font-weight: bold;
                font-style: italic;
                font-size: 50px;
                text-align:center;"> A healthy mind in a healthy body</p>
</html>


Health departments recommend a healthy diet for good health and well-being. However, we all know that “comfort food” (burgers, cookies, …), although being unhealthy, makes one feel good.
Therefore, the following questions arise: Is eating healthy really essential to well-being? What is the influence of a food or nutrient on one’s mental health? Is there a specific nutrient that makes one happy? 

Let's find out!

<div class="figure"
     style="text-align:center">
  <img src=".\images\healthy_food.png"
       width="800">
</div>



# Healthy diet definition

First, we need to define what a healthy diet is.
There are plenty of websites, videos and articles on healthy diets. Among the various sources, we decided to use two different definitions of the composition of a healthy diet:
* Wikipedia <sup id="fnref:wiki_site"><a href="#fn:wiki_site" class="footnote">1</a></sup> , because it is a popular website on which many people look for information. Thus, people might take it as a reliable source towards healthy eating.

* US Food and Drug Administration (FDA) <sup id="fnref:fda_site"><a href="#fn:fda_site" class="footnote">2</a></sup> , an official source with scientific background. 


The FDA updated their recommendations in March 2020. We decided to take both the original and the updated one to distinguish if one leads to better results.

Both websites state recommendations for daily nutrients intake. The Wikipedia article focuses on fruits, vegetables, grains, dairy, red meat, poultry, eggs and fish while the FDA one focuses on fat, fibre, carb, protein and saturated fats.

Each definition gave us a pipeline to follow to eat healthy.

<div class="figure"
     style="text-align:center">
  <img src=".\images\FDA_score_def.png"
       width="500">
</div>

<div class="figure"
     style="text-align:center">
  <img src=".\images\wiki_score_def.png"
       width="700">
</div>

The healthy scores were then computed as follows :

<div class="figure"
     style="text-align:center">
  <img src=".\images\formule_score.png"
       width="700">
</div>
    

# Are food and well-being correlated ?

First, let’s  compute the Spearman rank coefficient between the different nutrients as well as the Wikipedia score and the well-being of London residents. 

<div class="figure"
     style="text-align:center">
  <img src=".\images\spearman_fda_score.png"
       width="500">
</div>


The nutrient with the highest correlation with well-being is the fibre. It is surprising to see that both FDA scores are negatively correlated with the well-being. 

Then, let’s plot the Spearman rank correlation between the different types of food and the well-being of London residents.

<div class="figure"
     style="text-align:center">
  <img src=".\images\spearman_wiki_score.png"
       width="500">
</div>


Here, the food with the highest positive correlation with well being are fruits and vegetables. It makes sense, as most health offices recommend eating plenty of fruits and vegetables.
On the other hand, grains are negatively correlated.

As vegetables and fruits are rich in fiber, it seems that both scores agree.
However, whole grains are also a great source of fiber while grains are negatively correlated with well-being. This might be due to the fact that most Londoners eat more refined grains. 

The Wikipedia score is positively correlated with the well-being. 

All nutrients and foods used are statistically significant predictors of well-being according to the Spearman rank correlation because the t-test p-value against the null hypothesis that the coefficient is equal to 0 is lower than 0.05. 



# Can we predict happiness with our healthy scores?
Let's try to predict well-being by fitting an ordinary least squares regression to nutrients as well as foods, FDA and Wikipedia scores.


<div class="figure"
     style="text-align:center">
  <img src=".\images\regression_scores.png"
       width="800">
</div>

Unfortunately, it seems like our healthy scores cannot predict well-being.
The regressions tried to capture a trend but the datapoints don't seems to have one. 


We performed a regression to predict well-being using different types of food. The statistically significant coefficient value are shown on the figure below.

<div class="figure"
     style="text-align:center">
  <img src=".\images\regression_cat_coeffs.png"
       width="500">
</div>



<div class="withSidenote">

  <p>The result is surprising: apparently drinking water lowers your well-being whereas drinking wine makes you happier! </p>

  <figure class="sidenote display">
    <img src=".\images\meme_drake.png"
         width='300'>
</figure>
</div>




# Can we classify happiness and unhappiness with food intake?

Having a look at the distribution of the well-being, we thought of classifying areas into happy (well-being &#8805; 0 ) and unhappy (well-being &#60; 0 ).

<div class="figure"
     style="text-align:center">
  <img src=".\images\distrib_well_being.png"
       width="500">
</div>

We trained a random forest classifier. The figure below shows that the model performs morderately well on the test set and is highly overfitting.

<div class="figure"
     style="text-align:center">
  <img src=".\images\valid_curve.png"
       width="800">
</div>

However, when plotting the classes as a function of scores, we can clearly see that these scores cannot predict happiness because there is no tendency that would allow to classify the datapoints correctly. 


<div class="figure"
     style="text-align:center">
  <img src=".\images\well_wiki_score.png"
       width="500">
</div>

<div class="figure"
     style="text-align:center">
  <img src=".\images\well_fda_score.png"
       width="500">
</div>

# What have we learned?

Happiness is a complex notion ruled by a large variety of factors and food consumption is only one of them. Results of our research follow this intuition.

Food consumption only explains one aspect of human well-being. Indeed, we would need more indicators such as wealth or crime rate. Moreover, the indicators we used in our analysis did not take into account all types of food (such as oils, alcohol,...). Some data could be added such as average vitamins per product and other nutrients in order to conduct more analyses.

Some fun experiments could be realised to better understand the link between well-being and food consumption. For example, with the help of volunteers, some London residents could change their diet towards another area’s diet and see how their happiness changes.







<div class="figure"
     style="text-align:center">
  <img src=".\images\wine_brownies.png"
       width="700">
</div>

 
<html>
      <p style="font-weight: bold;
                font-style: italic;
                font-size: 50px;
                text-align:center;"> Bon Appétit! And don't forget to drink wine and eat brownies ! </p>
</html>







# Reference
<div class="footnotes">
    <ol>
        <li id="fn:wiki_site">
              <p><a href="https://en.wikipedia.org/wiki/Healthy_diet">Healthy diet, <em>Wikipedia</em>, last consulted: 18.12.2020 </a>&nbsp;<a href="#fnref:wiki_site" class="reversefootnote">↩</a></p>
            </li>

        <li id="fn:fda_site">
              <p><a href="https://www.fda.gov/media/135301/download">Daily Value and Percent Daily Value: Changes on the New Nutrition and Supplement Facts Labels , <em>FDA</em>, March 2020 </a>&nbsp;<a href="#fnref:fda_site" class="reversefootnote">↩</a></p>
            </li>
        
        <li id="fn:data_site">
              <p><a href="https://data.london.gov.uk/dataset/ward-profiles-and-atlas">Greater London Authority (GLA) , <em>Ward Profiles and Atlas</em>, last consulted: 18.12.2020 </a>&nbsp;<a href="#fnref:data_site" class="reversefootnote">↩</a></p>
            </li>
             
      
    </ol>
</div>