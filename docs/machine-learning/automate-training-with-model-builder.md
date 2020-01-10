---
title: Co je tvůrce modelů a jak to funguje?
description: Postup pro automatické učení modelu Machine Learning pomocí Tvůrce modelů ML.NET
ms.date: 01/07/2020
ms.custom: overview
ms.openlocfilehash: ac704b7961a8442a9174cdef5a4cd2a619236a4e
ms.sourcegitcommit: cbdc0f4fd39172b5191a35200c33d5030774463c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2020
ms.locfileid: "75777396"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a><span data-ttu-id="184fa-103">Co je tvůrce modelů a jak to funguje?</span><span class="sxs-lookup"><span data-stu-id="184fa-103">What is Model Builder and how does it work?</span></span>

<span data-ttu-id="184fa-104">ML.NET model Builder je intuitivní grafické rozšíření sady Visual Studio, které slouží k sestavování, výuce a nasazování vlastních modelů strojového učení.</span><span class="sxs-lookup"><span data-stu-id="184fa-104">ML.NET Model Builder is an intuitive graphical Visual Studio extension to build, train, and deploy custom machine learning models.</span></span>

<span data-ttu-id="184fa-105">Tvůrce modelů pomocí automatizovaného strojového učení (AutoML) zkoumá různé algoritmy a nastavení strojového učení, které vám pomůžou najít ten, který nejlépe vyhovuje vašemu scénáři.</span><span class="sxs-lookup"><span data-stu-id="184fa-105">Model Builder uses automated machine learning (AutoML) to explore different machine learning algorithms and settings to help you find the one that best suits your scenario.</span></span>

<span data-ttu-id="184fa-106">K používání tvůrce modelů nepotřebujete odborné znalosti strojového učení.</span><span class="sxs-lookup"><span data-stu-id="184fa-106">You don't need machine learning expertise to use Model Builder.</span></span> <span data-ttu-id="184fa-107">Potřebujete jenom některá data a problém, který je potřeba vyřešit.</span><span class="sxs-lookup"><span data-stu-id="184fa-107">All you need is some data, and a problem to solve.</span></span> <span data-ttu-id="184fa-108">Tvůrce modelů generuje kód pro přidání modelu do vaší aplikace .NET.</span><span class="sxs-lookup"><span data-stu-id="184fa-108">Model Builder generates the code to add the model to your .NET application.</span></span>

![Animace uživatelského rozhraní rozšíření tvůrce modelů sady Visual Studio](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> <span data-ttu-id="184fa-110">Tvůrce modelů je aktuálně ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="184fa-110">Model Builder is currently in Preview.</span></span>

## <a name="scenarios"></a><span data-ttu-id="184fa-111">Scénáře</span><span class="sxs-lookup"><span data-stu-id="184fa-111">Scenarios</span></span>

<span data-ttu-id="184fa-112">Můžete přenášet mnoho různých scénářů do Tvůrce modelů a vygenerovat pro svou aplikaci model strojového učení.</span><span class="sxs-lookup"><span data-stu-id="184fa-112">You can bring many different scenarios to Model Builder, to generate a machine learning model for your application.</span></span>

<span data-ttu-id="184fa-113">Scénář je popis typu předpovědi, kterou chcete použít pro vaše data.</span><span class="sxs-lookup"><span data-stu-id="184fa-113">A scenario is a description of the type of prediction you want to make using your data.</span></span> <span data-ttu-id="184fa-114">Příklad:</span><span class="sxs-lookup"><span data-stu-id="184fa-114">For example:</span></span>

- <span data-ttu-id="184fa-115">Předpověď budoucího objemu prodejů produktů na základě historických dat o prodeji</span><span class="sxs-lookup"><span data-stu-id="184fa-115">predict future product sales volume based on historical sales data</span></span>
- <span data-ttu-id="184fa-116">klasifikace zabarvení jako kladné nebo záporné na základě revizí zákazníků</span><span class="sxs-lookup"><span data-stu-id="184fa-116">classify sentiments as positive or negative based on customer reviews</span></span>
- <span data-ttu-id="184fa-117">zjištění, zda je bankovní transakce podvodný</span><span class="sxs-lookup"><span data-stu-id="184fa-117">detect whether a banking transaction is fraudulent</span></span>
- <span data-ttu-id="184fa-118">směrování problémů s názory zákazníků na správný tým ve vaší společnosti</span><span class="sxs-lookup"><span data-stu-id="184fa-118">route customer feedback issues to the correct team in your company</span></span>

### <a name="which-machine-learning-scenario-is-right-for-me"></a><span data-ttu-id="184fa-119">Který scénář strojového učení je pro mě nejvhodnější?</span><span class="sxs-lookup"><span data-stu-id="184fa-119">Which machine learning scenario is right for me?</span></span>

<span data-ttu-id="184fa-120">V Tvůrci modelů je nutné vybrat scénář.</span><span class="sxs-lookup"><span data-stu-id="184fa-120">In Model Builder, you need to select a scenario.</span></span> <span data-ttu-id="184fa-121">Typ scénáře závisí na typu předpovědi, kterou se pokoušíte provést.</span><span class="sxs-lookup"><span data-stu-id="184fa-121">The type of scenario depends on what type of prediction you are trying to make.</span></span>

#### <a name="predict-a-category-when-there-are-only-two-categories"></a><span data-ttu-id="184fa-122">Předpověď kategorie (pokud jsou k dispozici pouze dvě kategorie)</span><span class="sxs-lookup"><span data-stu-id="184fa-122">Predict a category (when there are only two categories)</span></span>

<span data-ttu-id="184fa-123">Binární klasifikace se používá ke kategorizaci dat do dvou kategorií (ano/ne; úspěch/chyba; pravda/nepravda; kladné nebo záporné).</span><span class="sxs-lookup"><span data-stu-id="184fa-123">Binary classification is used to categorize data into two categories (yes/no; pass/fail; true/false; positive/negative).</span></span>

![Diagram znázorňující příklady binární klasifikace včetně zjišťování podvodů, zmírnění rizik a blokování aplikací](media/binary-classification-examples.png)

<span data-ttu-id="184fa-125">Analýza mínění se dá použít k předpovědi kladné nebo záporné míněníí zpětné vazby od zákazníků.</span><span class="sxs-lookup"><span data-stu-id="184fa-125">Sentiment analysis can be used to predict positive or negative sentiment of customer feedback.</span></span> <span data-ttu-id="184fa-126">Je příkladem úlohy strojového učení s binární klasifikací.</span><span class="sxs-lookup"><span data-stu-id="184fa-126">It is an example of the binary classification machine learning task.</span></span>

<span data-ttu-id="184fa-127">Pokud váš scénář vyžaduje klasifikaci ve dvou kategoriích, můžete použít tuto šablonu s vlastní datovou sadou.</span><span class="sxs-lookup"><span data-stu-id="184fa-127">If your scenario requires classification into two categories, you can use this template with your own dataset.</span></span>

#### <a name="predict-a-category-when-there-are-three-or-more-categories"></a><span data-ttu-id="184fa-128">Předpověď kategorie (pokud existují tři nebo více kategorií)</span><span class="sxs-lookup"><span data-stu-id="184fa-128">Predict a category (when there are three or more categories)</span></span>

<span data-ttu-id="184fa-129">Pro kategorizaci dat do tří nebo více tříd lze použít klasifikaci s více třídami.</span><span class="sxs-lookup"><span data-stu-id="184fa-129">Multiclass classification can be used to categorize data into three or more classes.</span></span>

![Příklady klasifikace s více třídami včetně klasifikace dokumentů a produktů, směrování lístků podpory a stanovení priorit zákaznických problémů](media/multiclass-classification-examples.png)

<span data-ttu-id="184fa-131">Klasifikace problému se dá použít ke kategorizaci vašich názorů zákazníků (například na GitHubu) s použitím názvu a popisu problému.</span><span class="sxs-lookup"><span data-stu-id="184fa-131">Issue classification can be used to categorize customer feedback (for example, on GitHub) issues using the issue title and description.</span></span> <span data-ttu-id="184fa-132">Je to příklad úlohy Machine Learning pro klasifikaci více tříd.</span><span class="sxs-lookup"><span data-stu-id="184fa-132">It is an example of the multi-class classification machine learning task.</span></span>

<span data-ttu-id="184fa-133">Šablonu klasifikace problému můžete použít pro váš scénář, pokud chcete rozdělit data do tří nebo více kategorií.</span><span class="sxs-lookup"><span data-stu-id="184fa-133">You can use the issue classification template for your scenario if you want to categorize data into three or more categories.</span></span>

#### <a name="predict-a-number"></a><span data-ttu-id="184fa-134">Předpovědět číslo</span><span class="sxs-lookup"><span data-stu-id="184fa-134">Predict a number</span></span>

<span data-ttu-id="184fa-135">Regrese se používá k předpovědi čísel.</span><span class="sxs-lookup"><span data-stu-id="184fa-135">Regression is used to predict numbers.</span></span>

![Diagram znázorňující příklady regrese, jako je předpověď ceny, Prognóza prodeje a prediktivní údržba](media/regression-examples.png)

<span data-ttu-id="184fa-137">Předpověď cen se dá použít k předvídání cen za domácí ceny pomocí umístění, velikosti a dalších vlastností domu.</span><span class="sxs-lookup"><span data-stu-id="184fa-137">Price prediction can be used to predict house prices using location, size, and other characteristics of the house.</span></span> <span data-ttu-id="184fa-138">Jedná se o příklad úlohy regresního strojového učení.</span><span class="sxs-lookup"><span data-stu-id="184fa-138">It is an example of the regression machine learning task.</span></span>

<span data-ttu-id="184fa-139">Šablonu předpovědi cen můžete použít pro váš scénář, pokud chcete předpovědět číselnou hodnotu s vlastní datovou sadou.</span><span class="sxs-lookup"><span data-stu-id="184fa-139">You can use the price prediction template for your scenario if you want to predict a numerical value with your own dataset.</span></span>

#### <a name="classify-images-into-categories"></a><span data-ttu-id="184fa-140">Klasifikace imagí do kategorií</span><span class="sxs-lookup"><span data-stu-id="184fa-140">Classify images into categories</span></span>

<span data-ttu-id="184fa-141">Tento scénář je zvláštní případ třídy s více třídami, kde vstupní data, která mají být zařazena do kategorií, jsou sada imagí.</span><span class="sxs-lookup"><span data-stu-id="184fa-141">This scenario is a special case of multiclass classification, where the input data to be categorized is a set of images.</span></span>

<span data-ttu-id="184fa-142">Klasifikaci obrázku lze použít k identifikaci obrázků různých kategorií.</span><span class="sxs-lookup"><span data-stu-id="184fa-142">Image classification can be used to identify images of different categories.</span></span> <span data-ttu-id="184fa-143">Například různé typy terénu nebo zvířat nebo výrobní vady.</span><span class="sxs-lookup"><span data-stu-id="184fa-143">For example, different types of terrain or animals or manufacturing defects.</span></span>

<span data-ttu-id="184fa-144">Šablonu klasifikace obrázku můžete použít pro váš scénář, pokud máte sadu imagí a chcete klasifikace imagí do různých kategorií.</span><span class="sxs-lookup"><span data-stu-id="184fa-144">You can use the image classification template for your scenario if you have a set of images, and you want to classify the images into different categories.</span></span>

#### <a name="custom-scenario"></a><span data-ttu-id="184fa-145">Vlastní scénář</span><span class="sxs-lookup"><span data-stu-id="184fa-145">Custom scenario</span></span>

<span data-ttu-id="184fa-146">Vlastní scénář umožňuje ručně zvolit scénář.</span><span class="sxs-lookup"><span data-stu-id="184fa-146">The custom scenario allows you to manually choose your scenario.</span></span>

## <a name="data"></a><span data-ttu-id="184fa-147">Datové</span><span class="sxs-lookup"><span data-stu-id="184fa-147">Data</span></span>

<span data-ttu-id="184fa-148">Jakmile vyberete svůj scénář, tvůrce modelů vás vyzve k zadání datové sady.</span><span class="sxs-lookup"><span data-stu-id="184fa-148">Once you have chosen your scenario, Model Builder asks you to provide a dataset.</span></span> <span data-ttu-id="184fa-149">Data se používají ke školení, vyhodnocení a výběru nejlepšího modelu pro váš scénář.</span><span class="sxs-lookup"><span data-stu-id="184fa-149">The data is used to train, evaluate, and choose the best model for your scenario.</span></span>

![Diagram znázorňující kroky tvůrce modelů](media/model-builder-steps.png)

<span data-ttu-id="184fa-151">Tvůrce modelů podporuje datové sady ve formátech. TSV,. csv,. txt a také ve formátu SQL Database.</span><span class="sxs-lookup"><span data-stu-id="184fa-151">Model Builder supports datasets in .tsv, .csv, .txt formats, as well as SQL database format.</span></span> <span data-ttu-id="184fa-152">Pokud máte soubor. txt, sloupce by měly být oddělené `,`, `;` nebo `/t` a soubor musí obsahovat řádek záhlaví.</span><span class="sxs-lookup"><span data-stu-id="184fa-152">If you have a .txt file, columns should be separated with `,`, `;` or `/t` and the file must have a header row.</span></span>

<span data-ttu-id="184fa-153">Pokud je datová sada tvořena obrázky, podporované typy souborů jsou `.jpg` a `.png`.</span><span class="sxs-lookup"><span data-stu-id="184fa-153">If the dataset is made up of images, the supported file types are `.jpg` and `.png`.</span></span>

<span data-ttu-id="184fa-154">Další informace najdete v tématu [načtení dat o školení do Tvůrce modelů](how-to-guides/load-data-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="184fa-154">For more information, see [Load training data into Model Builder](how-to-guides/load-data-model-builder.md).</span></span>

### <a name="choose-the-output-to-predict-label"></a><span data-ttu-id="184fa-155">Vyberte výstup, který chcete předpovědět (popisek)</span><span class="sxs-lookup"><span data-stu-id="184fa-155">Choose the output to predict (label)</span></span>

<span data-ttu-id="184fa-156">Datová sada je tabulka řádků příkladů cvičení a sloupce atributů.</span><span class="sxs-lookup"><span data-stu-id="184fa-156">A dataset is a table of rows of training examples, and columns of attributes.</span></span> <span data-ttu-id="184fa-157">Každý řádek má:</span><span class="sxs-lookup"><span data-stu-id="184fa-157">Each row has:</span></span>

- <span data-ttu-id="184fa-158">**popisek** (atribut, který chcete předpovědět)</span><span class="sxs-lookup"><span data-stu-id="184fa-158">a **label** (the attribute that you want to predict)</span></span>
- <span data-ttu-id="184fa-159">**funkce** (atributy, které se používají jako vstupy pro předpověď popisku).</span><span class="sxs-lookup"><span data-stu-id="184fa-159">**features** (attributes that are used as inputs to predict the label).</span></span>

<span data-ttu-id="184fa-160">Pro scénář předpovědi pro domácí ceny můžou tyto funkce:</span><span class="sxs-lookup"><span data-stu-id="184fa-160">For the house-price prediction scenario, the features could be:</span></span>

- <span data-ttu-id="184fa-161">čtvercové záběry domu</span><span class="sxs-lookup"><span data-stu-id="184fa-161">the square footage of the house</span></span>
- <span data-ttu-id="184fa-162">počet ložnicemi a bathrooms</span><span class="sxs-lookup"><span data-stu-id="184fa-162">the number of bedrooms and bathrooms</span></span>
- <span data-ttu-id="184fa-163">PSČ</span><span class="sxs-lookup"><span data-stu-id="184fa-163">the zip code</span></span>

<span data-ttu-id="184fa-164">Popisek je cena za cenu na pracovišti pro tento řádek hodnot čtvercového záběru, Bedroom a koupeln a PSČ.</span><span class="sxs-lookup"><span data-stu-id="184fa-164">The label is the historical house price for that row of square footage, bedroom, and bathroom values and zip code.</span></span>

![Tabulka znázorňující řádky a sloupce údajů o cenách domu s funkcemi, které se skládají z poštovních místností – PSČ a popisek ceny](media/model-builder-data.png)

### <a name="example-datasets"></a><span data-ttu-id="184fa-166">Příklady datových sad</span><span class="sxs-lookup"><span data-stu-id="184fa-166">Example datasets</span></span>

<span data-ttu-id="184fa-167">Pokud ještě nemáte vlastní data, vyzkoušejte jednu z těchto datových sad:</span><span class="sxs-lookup"><span data-stu-id="184fa-167">If you don't have your own data yet, try out one of these datasets:</span></span>

|<span data-ttu-id="184fa-168">Scénář</span><span class="sxs-lookup"><span data-stu-id="184fa-168">Scenario</span></span>|<span data-ttu-id="184fa-169">Úloha ML</span><span class="sxs-lookup"><span data-stu-id="184fa-169">ML task</span></span>|<span data-ttu-id="184fa-170">Datové</span><span class="sxs-lookup"><span data-stu-id="184fa-170">Data</span></span>|<span data-ttu-id="184fa-171">Popisek</span><span class="sxs-lookup"><span data-stu-id="184fa-171">Label</span></span>|<span data-ttu-id="184fa-172">Funkce</span><span class="sxs-lookup"><span data-stu-id="184fa-172">Features</span></span>|
|-|-|-|-|-|
|<span data-ttu-id="184fa-173">Předpověď ceny</span><span class="sxs-lookup"><span data-stu-id="184fa-173">Price prediction</span></span>|<span data-ttu-id="184fa-174">nevýhody</span><span class="sxs-lookup"><span data-stu-id="184fa-174">regression</span></span>|[<span data-ttu-id="184fa-175">data taxislužby tarifů</span><span class="sxs-lookup"><span data-stu-id="184fa-175">taxi fare data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|<span data-ttu-id="184fa-176">Vozov</span><span class="sxs-lookup"><span data-stu-id="184fa-176">Fare</span></span>|<span data-ttu-id="184fa-177">Doba odezvy, vzdálenost</span><span class="sxs-lookup"><span data-stu-id="184fa-177">Trip time, distance</span></span>|
|<span data-ttu-id="184fa-178">Detekce anomálií</span><span class="sxs-lookup"><span data-stu-id="184fa-178">Anomaly detection</span></span>|<span data-ttu-id="184fa-179">binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="184fa-179">binary classification</span></span>|[<span data-ttu-id="184fa-180">prodejní data produktu</span><span class="sxs-lookup"><span data-stu-id="184fa-180">product sales data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|<span data-ttu-id="184fa-181">Prodej produktu</span><span class="sxs-lookup"><span data-stu-id="184fa-181">Product Sales</span></span>|<span data-ttu-id="184fa-182">Month</span><span class="sxs-lookup"><span data-stu-id="184fa-182">Month</span></span>|
|<span data-ttu-id="184fa-183">Analýza mínění</span><span class="sxs-lookup"><span data-stu-id="184fa-183">Sentiment analysis</span></span>|<span data-ttu-id="184fa-184">binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="184fa-184">binary classification</span></span>|[<span data-ttu-id="184fa-185">data komentáře webu</span><span class="sxs-lookup"><span data-stu-id="184fa-185">website comment data</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|<span data-ttu-id="184fa-186">Popisek (0, pokud je negativní mínění, 1 Při kladném)</span><span class="sxs-lookup"><span data-stu-id="184fa-186">Label (0 when negative sentiment, 1 when positive)</span></span>|<span data-ttu-id="184fa-187">Komentář, rok</span><span class="sxs-lookup"><span data-stu-id="184fa-187">Comment, Year</span></span>|
|<span data-ttu-id="184fa-188">Odhalování podvodů</span><span class="sxs-lookup"><span data-stu-id="184fa-188">Fraud detection</span></span>|<span data-ttu-id="184fa-189">binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="184fa-189">binary classification</span></span>|[<span data-ttu-id="184fa-190">data platebních karet</span><span class="sxs-lookup"><span data-stu-id="184fa-190">credit card data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|<span data-ttu-id="184fa-191">Třída (1, pokud je podvodný, 0 jinak)</span><span class="sxs-lookup"><span data-stu-id="184fa-191">Class (1 when fraudulent, 0 otherwise)</span></span>|<span data-ttu-id="184fa-192">Množství, V1-v28 (funkce Anonyme)</span><span class="sxs-lookup"><span data-stu-id="184fa-192">Amount, V1-V28 (anonymized features)</span></span>|
|<span data-ttu-id="184fa-193">Klasifikace textu</span><span class="sxs-lookup"><span data-stu-id="184fa-193">Text classification</span></span>|<span data-ttu-id="184fa-194">Klasifikace s více třídami</span><span class="sxs-lookup"><span data-stu-id="184fa-194">multiclass classification</span></span>|[<span data-ttu-id="184fa-195">Data o problému na GitHubu</span><span class="sxs-lookup"><span data-stu-id="184fa-195">GitHub issue data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|<span data-ttu-id="184fa-196">Plošný</span><span class="sxs-lookup"><span data-stu-id="184fa-196">Area</span></span>|<span data-ttu-id="184fa-197">Název, popis</span><span class="sxs-lookup"><span data-stu-id="184fa-197">Title, Description</span></span>|
|<span data-ttu-id="184fa-198">Klasifikace obrázků</span><span class="sxs-lookup"><span data-stu-id="184fa-198">Image classification</span></span>|<span data-ttu-id="184fa-199">Klasifikace s více třídami</span><span class="sxs-lookup"><span data-stu-id="184fa-199">multiclass classification</span></span>|[<span data-ttu-id="184fa-200">Obrázky květin</span><span class="sxs-lookup"><span data-stu-id="184fa-200">Flowers images</span></span>](http://download.tensorflow.org/example_images/flower_photos.tgz)|<span data-ttu-id="184fa-201">Typ květu: uzavřené, Dandelion, růže, slunečnice, Tulips</span><span class="sxs-lookup"><span data-stu-id="184fa-201">The type of flower: daisy, dandelion, roses, sunflowers, tulips</span></span>|<span data-ttu-id="184fa-202">Samotná data obrázku</span><span class="sxs-lookup"><span data-stu-id="184fa-202">The image data itself</span></span>|

## <a name="train"></a><span data-ttu-id="184fa-203">Trénování</span><span class="sxs-lookup"><span data-stu-id="184fa-203">Train</span></span>

<span data-ttu-id="184fa-204">Když vyberete svůj scénář, data a popisek, tvůrce modelů navlakuje model.</span><span class="sxs-lookup"><span data-stu-id="184fa-204">Once you select your scenario, data, and label, Model Builder trains the model.</span></span>

### <a name="what-is-training"></a><span data-ttu-id="184fa-205">Co je školení?</span><span class="sxs-lookup"><span data-stu-id="184fa-205">What is training?</span></span>

<span data-ttu-id="184fa-206">Školení je automatický proces, podle kterého tvůrce modelů učí váš model, jak odpovídat na otázky pro váš scénář.</span><span class="sxs-lookup"><span data-stu-id="184fa-206">Training is an automatic process by which Model Builder teaches your model how to answer questions for your scenario.</span></span> <span data-ttu-id="184fa-207">Po vyškolení může váš model předpovědi se vstupními daty, ke kterým se předtím neviděl.</span><span class="sxs-lookup"><span data-stu-id="184fa-207">Once trained, your model can make predictions with input data that it has not seen before.</span></span> <span data-ttu-id="184fa-208">Pokud například předpovídáte ceny za dům a na trhu se nachází nová dům, můžete předpovědět její prodejní cenu.</span><span class="sxs-lookup"><span data-stu-id="184fa-208">For example, if you are predicting house prices and a new house comes on the market, you can predict its sale price.</span></span>

<span data-ttu-id="184fa-209">Vzhledem k tomu, že tvůrce modelů používá automatizované Machine Learning (AutoML), nevyžaduje během školení žádné vstupy nebo ladění.</span><span class="sxs-lookup"><span data-stu-id="184fa-209">Because Model Builder uses automated machine learning (AutoML), it does not require any input or tuning from you during training.</span></span>

### <a name="how-long-should-i-train-for"></a><span data-ttu-id="184fa-210">Jak dlouho mám zaškolit?</span><span class="sxs-lookup"><span data-stu-id="184fa-210">How long should I train for?</span></span>

<span data-ttu-id="184fa-211">Tvůrce modelů používá AutoML k prozkoumání více modelů, abyste si našli nejlepší výkon modelu.</span><span class="sxs-lookup"><span data-stu-id="184fa-211">Model Builder uses AutoML to explore multiple models to find you the best performing model.</span></span>

<span data-ttu-id="184fa-212">Delší školicí období umožňují AutoML prozkoumat více modelů s širší škálou nastavení.</span><span class="sxs-lookup"><span data-stu-id="184fa-212">Longer training periods allow AutoML to explore more models with a wider range of settings.</span></span>

<span data-ttu-id="184fa-213">V následující tabulce najdete průměrnou dobu, jakou trvalo dosažení dobrého výkonu sady ukázkových datových sad na místním počítači.</span><span class="sxs-lookup"><span data-stu-id="184fa-213">The table below summarizes the average time taken to get good performance for a suite of example datasets, on a local machine.</span></span>

|<span data-ttu-id="184fa-214">Velikost datové sady</span><span class="sxs-lookup"><span data-stu-id="184fa-214">Dataset size</span></span>|<span data-ttu-id="184fa-215">Průměrná doba pro vlak</span><span class="sxs-lookup"><span data-stu-id="184fa-215">Average time to train</span></span>|
|------------|---------------------|
|<span data-ttu-id="184fa-216">0-10 MB</span><span class="sxs-lookup"><span data-stu-id="184fa-216">0 - 10 MB</span></span>|<span data-ttu-id="184fa-217">10 sekund</span><span class="sxs-lookup"><span data-stu-id="184fa-217">10 sec</span></span>|
|<span data-ttu-id="184fa-218">10-100 MB</span><span class="sxs-lookup"><span data-stu-id="184fa-218">10 - 100 MB</span></span>|<span data-ttu-id="184fa-219">10 min</span><span class="sxs-lookup"><span data-stu-id="184fa-219">10 min</span></span>|
|<span data-ttu-id="184fa-220">100 – 500 MB</span><span class="sxs-lookup"><span data-stu-id="184fa-220">100 - 500 MB</span></span>|<span data-ttu-id="184fa-221">30 min</span><span class="sxs-lookup"><span data-stu-id="184fa-221">30 min</span></span>|
|<span data-ttu-id="184fa-222">500 – 1 GB</span><span class="sxs-lookup"><span data-stu-id="184fa-222">500 - 1 GB</span></span>|<span data-ttu-id="184fa-223">60 min.</span><span class="sxs-lookup"><span data-stu-id="184fa-223">60 min</span></span>|
|<span data-ttu-id="184fa-224">1 GB +</span><span class="sxs-lookup"><span data-stu-id="184fa-224">1 GB+</span></span>|<span data-ttu-id="184fa-225">3 hodiny</span><span class="sxs-lookup"><span data-stu-id="184fa-225">3+ hours</span></span>|

<span data-ttu-id="184fa-226">Tato čísla jsou jenom orientační.</span><span class="sxs-lookup"><span data-stu-id="184fa-226">These numbers are a guide only.</span></span> <span data-ttu-id="184fa-227">Přesná délka školení závisí na:</span><span class="sxs-lookup"><span data-stu-id="184fa-227">The exact length of training is dependent on:</span></span>

- <span data-ttu-id="184fa-228">počet funkcí (sloupců), které se používají jako vstup do modelu</span><span class="sxs-lookup"><span data-stu-id="184fa-228">the number of features (columns) being used to as input to the model</span></span>
- <span data-ttu-id="184fa-229">typ sloupců</span><span class="sxs-lookup"><span data-stu-id="184fa-229">the type of columns</span></span>
- <span data-ttu-id="184fa-230">úkol ML</span><span class="sxs-lookup"><span data-stu-id="184fa-230">the ML task</span></span>
- <span data-ttu-id="184fa-231">výkon procesoru, disku a paměti počítače, který se používá pro školení</span><span class="sxs-lookup"><span data-stu-id="184fa-231">the CPU, disk and memory performance of the machine used for training</span></span>

## <a name="evaluate"></a><span data-ttu-id="184fa-232">Zhodnocení produktu</span><span class="sxs-lookup"><span data-stu-id="184fa-232">Evaluate</span></span>

<span data-ttu-id="184fa-233">Vyhodnocení je proces měření, jak dobrý je váš model.</span><span class="sxs-lookup"><span data-stu-id="184fa-233">Evaluation is the process of measuring how good your model is.</span></span> <span data-ttu-id="184fa-234">Tvůrce modelů používá trained model k vytváření předpovědi s novými testovacími daty a pak měří, jak dobrá předpovědi.</span><span class="sxs-lookup"><span data-stu-id="184fa-234">Model Builder uses the trained model to make predictions with new test data, and then measures how good the predictions are.</span></span>

<span data-ttu-id="184fa-235">Tvůrce modelů rozdělí školicí data do sady školení a sady testů.</span><span class="sxs-lookup"><span data-stu-id="184fa-235">Model Builder splits the training data into a training set and a test set.</span></span> <span data-ttu-id="184fa-236">Školicí data (80%) se používá ke školení vašeho modelu a testovacích dat (20%) se vrátí k vyhodnocení vašeho modelu.</span><span class="sxs-lookup"><span data-stu-id="184fa-236">The training data (80%) is used to train your model and the test data (20%) is held back to evaluate your model.</span></span> 

### <a name="how-do-i-understand-my-model-performance"></a><span data-ttu-id="184fa-237">Návody porozumět výkonu mého modelu?</span><span class="sxs-lookup"><span data-stu-id="184fa-237">How do I understand my model performance?</span></span>

<span data-ttu-id="184fa-238">Scénář se mapuje na úlohu strojového učení.</span><span class="sxs-lookup"><span data-stu-id="184fa-238">A scenario maps to a machine learning task.</span></span> <span data-ttu-id="184fa-239">Každá úloha ML má svou vlastní sadu metrik vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="184fa-239">Each ML task has its own set of evaluation metrics.</span></span>

#### <a name="regression-for-example-price-prediction"></a><span data-ttu-id="184fa-240">Regrese (například předpověď ceny)</span><span class="sxs-lookup"><span data-stu-id="184fa-240">Regression (for example, Price Prediction)</span></span>

<span data-ttu-id="184fa-241">Výchozí metrika pro regresní problémy je RSquared, hodnota RSquared rozsahů mezi 0 a 1.</span><span class="sxs-lookup"><span data-stu-id="184fa-241">The default metric for regression problems is RSquared, the value of RSquared ranges between 0 and 1.</span></span> <span data-ttu-id="184fa-242">hodnota 1 je nejlepší možnou hodnotou nebo jinými slovy, které přiblíží hodnotu RSquared na 1, lepší váš model.</span><span class="sxs-lookup"><span data-stu-id="184fa-242">1 is the best possible value or in other words the closer the value of RSquared to 1 the better your model is performing.</span></span>

<span data-ttu-id="184fa-243">Další metriky nahlášené jako absolutní ztráta, čtvercová ztráta a ztráta služby RMS jsou další metriky, které lze použít k pochopení toho, jak model pracuje, a jeho porovnání s jinými regresními modely.</span><span class="sxs-lookup"><span data-stu-id="184fa-243">Other metrics reported such as absolute-loss, squared-loss, and RMS loss are additional metrics, which can be used to understand how your model is performing and comparing it against other regression models.</span></span>

#### <a name="binary-classification-for-example-sentiment-analysis"></a><span data-ttu-id="184fa-244">Binární klasifikace (například Analýza mínění)</span><span class="sxs-lookup"><span data-stu-id="184fa-244">Binary Classification (for example, Sentiment Analysis)</span></span>

<span data-ttu-id="184fa-245">Výchozí metrika pro problémy s klasifikací je přesnost.</span><span class="sxs-lookup"><span data-stu-id="184fa-245">The default metric for classification problems is accuracy.</span></span> <span data-ttu-id="184fa-246">Přesnost definuje poměr správných předpovědi, které model provádí přes testovací datovou sadu.</span><span class="sxs-lookup"><span data-stu-id="184fa-246">Accuracy defines the proportion of correct predictions your model is making over the test dataset.</span></span> <span data-ttu-id="184fa-247">Nejblíže k 100% nebo 1,0 tím lépe.</span><span class="sxs-lookup"><span data-stu-id="184fa-247">The closer to 100% or 1.0 the better it is.</span></span>

<span data-ttu-id="184fa-248">Jiné metriky nahlášené jako AUC (oblast pod křivkou), které měří skutečnou kladnou rychlost vs. falešně pozitivní sazba by měla být větší než 0,50, aby bylo možné modely akceptovat.</span><span class="sxs-lookup"><span data-stu-id="184fa-248">Other metrics reported such as AUC (Area under the curve), which measures the true positive rate vs. the false positive rate should be greater than 0.50 for models to be acceptable.</span></span>

<span data-ttu-id="184fa-249">K řízení rovnováhy mezi přesností a odvoláním je možné použít další metriky, jako je například skóre F1.</span><span class="sxs-lookup"><span data-stu-id="184fa-249">Additional metrics like F1 score can be used to control the balance between Precision and Recall.</span></span>

#### <a name="multi-class-classification-for-example-issue-classification-image-classification"></a><span data-ttu-id="184fa-250">Klasifikace více tříd (například klasifikace vydávání, klasifikace obrázků)</span><span class="sxs-lookup"><span data-stu-id="184fa-250">Multi-Class Classification (for example, Issue Classification, Image Classification)</span></span>

<span data-ttu-id="184fa-251">Výchozí metrika pro klasifikaci více tříd je mikropřesnost.</span><span class="sxs-lookup"><span data-stu-id="184fa-251">The default metric for Multi-class classification is Micro Accuracy.</span></span> <span data-ttu-id="184fa-252">Hodnota bližší pro mikropřesnost na 100% nebo 1,0 je lepší.</span><span class="sxs-lookup"><span data-stu-id="184fa-252">The closer the Micro Accuracy to 100% or 1.0 the better it is.</span></span>

<span data-ttu-id="184fa-253">Další důležitou metrikou pro klasifikaci více tříd je přesnost na makro, podobně jako u mikropřesnosti blíž k 1,0. lepší je.</span><span class="sxs-lookup"><span data-stu-id="184fa-253">Another important metric for Multi-class classification is Macro-accuracy, similar to Micro-accuracy the closer to 1.0 the better it is.</span></span> <span data-ttu-id="184fa-254">Dobrým způsobem, jak se domnívat o těchto dvou typech přesnosti, je:</span><span class="sxs-lookup"><span data-stu-id="184fa-254">A good way to think about these two types of accuracy is:</span></span>

- <span data-ttu-id="184fa-255">Mikropřesnost: jak často se příchozí lístek klasifikuje do správného týmu?</span><span class="sxs-lookup"><span data-stu-id="184fa-255">Micro-accuracy: How often does an incoming ticket get classified to the right team?</span></span>
- <span data-ttu-id="184fa-256">Přesnost maker: u průměrných týmů, jak často je příchozí lístek správný pro svůj tým?</span><span class="sxs-lookup"><span data-stu-id="184fa-256">Macro-accuracy: For an average team, how often is an incoming ticket correct for their team?</span></span>

### <a name="more-information-on-evaluation-metrics"></a><span data-ttu-id="184fa-257">Další informace o metrikách vyhodnocení</span><span class="sxs-lookup"><span data-stu-id="184fa-257">More information on evaluation metrics</span></span>

<span data-ttu-id="184fa-258">Další informace najdete v tématu [metriky vyhodnocení modelu](resources/metrics.md).</span><span class="sxs-lookup"><span data-stu-id="184fa-258">For more information, see [model evaluation metrics](resources/metrics.md).</span></span>

## <a name="improve"></a><span data-ttu-id="184fa-259">Zlepšit</span><span class="sxs-lookup"><span data-stu-id="184fa-259">Improve</span></span>

<span data-ttu-id="184fa-260">Pokud vaše skóre výkonu vašeho modelu není tak dobré, jak chcete, můžete:</span><span class="sxs-lookup"><span data-stu-id="184fa-260">If your model performance score is not as good as you want it to be, you can:</span></span>

- <span data-ttu-id="184fa-261">Naučit se delší dobu.</span><span class="sxs-lookup"><span data-stu-id="184fa-261">Train for a longer period of time.</span></span> <span data-ttu-id="184fa-262">Pomocí automatizovaného strojového učení se navíc snaží vyzkoušet více algoritmů a nastavení.</span><span class="sxs-lookup"><span data-stu-id="184fa-262">With more time, the automated machine learning engine to try more algorithms and settings.</span></span>

- <span data-ttu-id="184fa-263">Přidejte další data.</span><span class="sxs-lookup"><span data-stu-id="184fa-263">Add more data.</span></span> <span data-ttu-id="184fa-264">V některých případech se množství dat nestačí pro výuku vysoce kvalitního modelu strojového učení.</span><span class="sxs-lookup"><span data-stu-id="184fa-264">Sometimes the amount of data is not sufficient to train a high-quality machine learning model.</span></span>

- <span data-ttu-id="184fa-265">Vyvážení dat</span><span class="sxs-lookup"><span data-stu-id="184fa-265">Balance your data.</span></span> <span data-ttu-id="184fa-266">Pro úlohy klasifikace se ujistěte, že je sada školení vyrovnávána napříč kategoriemi.</span><span class="sxs-lookup"><span data-stu-id="184fa-266">For classification tasks, make sure that the training set is balanced across the categories.</span></span> <span data-ttu-id="184fa-267">Například pokud máte čtyři třídy pro 100 ukázky a dvě první třídy (značky 1 a značka2) se používají pro 90 záznamů, ale ostatní dvě (značka3 a tag4) se používají jenom u zbývajících 10 záznamů, nedostatek vyvážených dat může způsobit, že váš model bude bojovat do typu korespondenční ectly předpověď značka3 nebo tag4.</span><span class="sxs-lookup"><span data-stu-id="184fa-267">For example, if you have four classes for 100 training examples, and the two first classes (tag1 and tag2) are used for 90 records, but the other two (tag3 and tag4) are only used on the remaining 10 records, the lack of balanced data may cause your model to struggle to correctly predict tag3 or tag4.</span></span>

## <a name="code"></a><span data-ttu-id="184fa-268">Kód</span><span class="sxs-lookup"><span data-stu-id="184fa-268">Code</span></span>

<span data-ttu-id="184fa-269">Po fázi vyhodnocení výstup tvůrce modelů vytvoří soubor modelu a kód, který můžete použít k přidání modelu do aplikace.</span><span class="sxs-lookup"><span data-stu-id="184fa-269">After the evaluation phase, Model Builder outputs a model file, and code that you can use to add the model to your application.</span></span> <span data-ttu-id="184fa-270">Modely ML.NET se ukládají jako soubor zip.</span><span class="sxs-lookup"><span data-stu-id="184fa-270">ML.NET models are saved as a zip file.</span></span> <span data-ttu-id="184fa-271">Kód pro načtení a použití modelu je přidán jako nový projekt ve vašem řešení.</span><span class="sxs-lookup"><span data-stu-id="184fa-271">The code to load and use your model is added as a new project in your solution.</span></span> <span data-ttu-id="184fa-272">Tvůrce modelů také přidá ukázkovou konzolovou aplikaci, kterou můžete spustit pro zobrazení modelu v akci.</span><span class="sxs-lookup"><span data-stu-id="184fa-272">Model Builder also adds a sample console app that you can run to see your model in action.</span></span>

<span data-ttu-id="184fa-273">Kromě toho tvůrce modelů vypíše kód, který model vygeneroval, takže můžete pochopit postup, který se používá ke generování modelu.</span><span class="sxs-lookup"><span data-stu-id="184fa-273">In addition, Model Builder outputs the code that generated the model, so that you can understand the steps used to generate the model.</span></span> <span data-ttu-id="184fa-274">Můžete také použít kód školení modelu k revýuce modelu s novými daty.</span><span class="sxs-lookup"><span data-stu-id="184fa-274">You can also use the model training code to retrain your model with new data.</span></span>

## <a name="whats-next"></a><span data-ttu-id="184fa-275">Co dále?</span><span class="sxs-lookup"><span data-stu-id="184fa-275">What's next?</span></span>

<span data-ttu-id="184fa-276">[Instalace](how-to-guides/install-model-builder.md) rozšíření pro tvůrce modelů sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="184fa-276">[Install](how-to-guides/install-model-builder.md) the Model Builder Visual Studio extension</span></span>

<span data-ttu-id="184fa-277">Vyzkoušejte [cenový odhad nebo jakýkoli scénář regrese](tutorials/predict-prices-with-model-builder.md) .</span><span class="sxs-lookup"><span data-stu-id="184fa-277">Try [price prediction or any regression scenario](tutorials/predict-prices-with-model-builder.md)</span></span>
