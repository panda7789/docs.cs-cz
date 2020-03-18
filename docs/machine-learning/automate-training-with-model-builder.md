---
title: Co je model builder a jak to funguje?
description: Jak používat ML.NET Model Builder automaticky trénovat model strojového učení
ms.date: 01/07/2020
ms.custom: overview, mlnet-tooling
ms.openlocfilehash: cff4601843ec9ca7201ea7dbdbfbcfa18f50e46e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399222"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a><span data-ttu-id="e684c-103">Co je model builder a jak to funguje?</span><span class="sxs-lookup"><span data-stu-id="e684c-103">What is Model Builder and how does it work?</span></span>

<span data-ttu-id="e684c-104">ML.NET Model Builder je intuitivní grafické rozšíření Sady Visual Studio pro vytváření, trénování a nasazování vlastních modelů strojového učení.</span><span class="sxs-lookup"><span data-stu-id="e684c-104">ML.NET Model Builder is an intuitive graphical Visual Studio extension to build, train, and deploy custom machine learning models.</span></span>

<span data-ttu-id="e684c-105">Model Builder používá automatizované strojové učení (AutoML) k prozkoumání různých algoritmů a nastavení strojového učení, které vám pomohou najít ten, který nejlépe vyhovuje vašemu scénáři.</span><span class="sxs-lookup"><span data-stu-id="e684c-105">Model Builder uses automated machine learning (AutoML) to explore different machine learning algorithms and settings to help you find the one that best suits your scenario.</span></span>

<span data-ttu-id="e684c-106">K používání modelového tvůrce nepotřebujete odborné znalosti strojového učení.</span><span class="sxs-lookup"><span data-stu-id="e684c-106">You don't need machine learning expertise to use Model Builder.</span></span> <span data-ttu-id="e684c-107">Vše, co potřebujete, jsou nějaká data a problém k vyřešení.</span><span class="sxs-lookup"><span data-stu-id="e684c-107">All you need is some data, and a problem to solve.</span></span> <span data-ttu-id="e684c-108">Tvůrce modelů generuje kód pro přidání modelu do aplikace .NET.</span><span class="sxs-lookup"><span data-stu-id="e684c-108">Model Builder generates the code to add the model to your .NET application.</span></span>

![Animace uživatelského rozhraní rozšíření Visual Studio tvůrce modelů](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> <span data-ttu-id="e684c-110">Tvůrce modelů je momentálně ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="e684c-110">Model Builder is currently in Preview.</span></span>

## <a name="scenarios"></a><span data-ttu-id="e684c-111">Scénáře</span><span class="sxs-lookup"><span data-stu-id="e684c-111">Scenarios</span></span>

<span data-ttu-id="e684c-112">Můžete přinést mnoho různých scénářů model builder, generovat model strojového učení pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e684c-112">You can bring many different scenarios to Model Builder, to generate a machine learning model for your application.</span></span>

<span data-ttu-id="e684c-113">Scénář je popis typu předpověď, kterou chcete provést pomocí dat.</span><span class="sxs-lookup"><span data-stu-id="e684c-113">A scenario is a description of the type of prediction you want to make using your data.</span></span> <span data-ttu-id="e684c-114">Například:</span><span class="sxs-lookup"><span data-stu-id="e684c-114">For example:</span></span>

- <span data-ttu-id="e684c-115">předpovědět budoucí objem prodeje produktů na základě historických údajů o prodeji</span><span class="sxs-lookup"><span data-stu-id="e684c-115">predict future product sales volume based on historical sales data</span></span>
- <span data-ttu-id="e684c-116">klasifikovaly názory jako pozitivní nebo negativní na základě recenzí zákazníků</span><span class="sxs-lookup"><span data-stu-id="e684c-116">classify sentiments as positive or negative based on customer reviews</span></span>
- <span data-ttu-id="e684c-117">zjistit, zda je bankovní transakce podvodná</span><span class="sxs-lookup"><span data-stu-id="e684c-117">detect whether a banking transaction is fraudulent</span></span>
- <span data-ttu-id="e684c-118">směrovat problémy se zpětnou vazbou od zákazníků ke správnému týmu ve vaší společnosti</span><span class="sxs-lookup"><span data-stu-id="e684c-118">route customer feedback issues to the correct team in your company</span></span>

### <a name="which-machine-learning-scenario-is-right-for-me"></a><span data-ttu-id="e684c-119">Který scénář strojového učení je pro mě ten pravý?</span><span class="sxs-lookup"><span data-stu-id="e684c-119">Which machine learning scenario is right for me?</span></span>

<span data-ttu-id="e684c-120">V Tvůrce modelů je třeba vybrat scénář.</span><span class="sxs-lookup"><span data-stu-id="e684c-120">In Model Builder, you need to select a scenario.</span></span> <span data-ttu-id="e684c-121">Typ scénáře závisí na typu předpověď, kterou se pokoušíte provést.</span><span class="sxs-lookup"><span data-stu-id="e684c-121">The type of scenario depends on what type of prediction you are trying to make.</span></span>

#### <a name="predict-a-category-when-there-are-only-two-categories"></a><span data-ttu-id="e684c-122">Předpovědět kategorii (pokud existují pouze dvě kategorie)</span><span class="sxs-lookup"><span data-stu-id="e684c-122">Predict a category (when there are only two categories)</span></span>

<span data-ttu-id="e684c-123">Binární klasifikace se používá ke kategorizaci dat do dvou kategorií (ano/ne, pass/fail; true/false; positive/negative).</span><span class="sxs-lookup"><span data-stu-id="e684c-123">Binary classification is used to categorize data into two categories (yes/no; pass/fail; true/false; positive/negative).</span></span>

![Diagram znázorňující příklady binární klasifikace včetně detekce podvodů, zmírnění rizika a screeningu aplikací](media/binary-classification-examples.png)

<span data-ttu-id="e684c-125">Analýzu mínění lze použít k předvídání pozitivního nebo negativního mínění zpětné vazby od zákazníků.</span><span class="sxs-lookup"><span data-stu-id="e684c-125">Sentiment analysis can be used to predict positive or negative sentiment of customer feedback.</span></span> <span data-ttu-id="e684c-126">Je to příklad úlohy binární klasifikace strojového učení.</span><span class="sxs-lookup"><span data-stu-id="e684c-126">It is an example of the binary classification machine learning task.</span></span>

<span data-ttu-id="e684c-127">Pokud váš scénář vyžaduje klasifikaci do dvou kategorií, můžete použít tuto šablonu s vlastní datovou sadou.</span><span class="sxs-lookup"><span data-stu-id="e684c-127">If your scenario requires classification into two categories, you can use this template with your own dataset.</span></span>

#### <a name="predict-a-category-when-there-are-three-or-more-categories"></a><span data-ttu-id="e684c-128">Předvídání kategorie (pokud existují tři nebo více kategorií)</span><span class="sxs-lookup"><span data-stu-id="e684c-128">Predict a category (when there are three or more categories)</span></span>

<span data-ttu-id="e684c-129">Klasifikace více tříd lze kategorizovat data do tří nebo více tříd.</span><span class="sxs-lookup"><span data-stu-id="e684c-129">Multiclass classification can be used to categorize data into three or more classes.</span></span>

![Příklady klasifikace více tříd, včetně klasifikace dokumentů a produktů, směrování lístků podpory a stanovení priorit problémů zákazníků](media/multiclass-classification-examples.png)

<span data-ttu-id="e684c-131">Klasifikace problémů slouží ke kategorizaci zpětné vazby od zákazníků (například na GitHubu) pomocí názvu a popisu problému.</span><span class="sxs-lookup"><span data-stu-id="e684c-131">Issue classification can be used to categorize customer feedback (for example, on GitHub) issues using the issue title and description.</span></span> <span data-ttu-id="e684c-132">Je to příklad vícetřídní klasifikace úlohy strojového učení.</span><span class="sxs-lookup"><span data-stu-id="e684c-132">It is an example of the multi-class classification machine learning task.</span></span>

<span data-ttu-id="e684c-133">Pokud chcete data zařadit do kategorií do tří nebo více kategorií, můžete použít šablonu klasifikace problémů pro váš scénář.</span><span class="sxs-lookup"><span data-stu-id="e684c-133">You can use the issue classification template for your scenario if you want to categorize data into three or more categories.</span></span>

#### <a name="predict-a-number"></a><span data-ttu-id="e684c-134">Předpovědět číslo</span><span class="sxs-lookup"><span data-stu-id="e684c-134">Predict a number</span></span>

<span data-ttu-id="e684c-135">Regrese se používá k předvídání čísel.</span><span class="sxs-lookup"><span data-stu-id="e684c-135">Regression is used to predict numbers.</span></span>

![Diagram znázorňující příklady regresní ceny, jako je predikce cen, prognóza prodeje a prediktivní údržba](media/regression-examples.png)

<span data-ttu-id="e684c-137">Cenová předpověď může být použita k předvídání cen domů pomocí umístění, velikosti a dalších charakteristik domu.</span><span class="sxs-lookup"><span data-stu-id="e684c-137">Price prediction can be used to predict house prices using location, size, and other characteristics of the house.</span></span> <span data-ttu-id="e684c-138">Je to příklad úlohy regrese strojového učení.</span><span class="sxs-lookup"><span data-stu-id="e684c-138">It is an example of the regression machine learning task.</span></span>

<span data-ttu-id="e684c-139">Šablonu předpovědi ceny můžete použít pro váš scénář, pokud chcete předpovědět číselnou hodnotu s vlastní datovou sadou.</span><span class="sxs-lookup"><span data-stu-id="e684c-139">You can use the price prediction template for your scenario if you want to predict a numerical value with your own dataset.</span></span>

#### <a name="classify-images-into-categories"></a><span data-ttu-id="e684c-140">Klasifikace obrázků do kategorií</span><span class="sxs-lookup"><span data-stu-id="e684c-140">Classify images into categories</span></span>

<span data-ttu-id="e684c-141">Tento scénář je zvláštní případ klasifikace více tříd, kde vstupní data, která mají být kategorizována, je sada bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="e684c-141">This scenario is a special case of multiclass classification, where the input data to be categorized is a set of images.</span></span>

<span data-ttu-id="e684c-142">Klasifikace obrázků lze použít k identifikaci obrázků různých kategorií.</span><span class="sxs-lookup"><span data-stu-id="e684c-142">Image classification can be used to identify images of different categories.</span></span> <span data-ttu-id="e684c-143">Například různé typy terénu nebo zvířat nebo výrobní vady.</span><span class="sxs-lookup"><span data-stu-id="e684c-143">For example, different types of terrain or animals or manufacturing defects.</span></span>

<span data-ttu-id="e684c-144">Šablonu klasifikace obrázků můžete použít pro váš scénář, pokud máte sadu obrázků a chcete je klasifikovat do různých kategorií.</span><span class="sxs-lookup"><span data-stu-id="e684c-144">You can use the image classification template for your scenario if you have a set of images, and you want to classify the images into different categories.</span></span>

#### <a name="custom-scenario"></a><span data-ttu-id="e684c-145">Vlastní scénář</span><span class="sxs-lookup"><span data-stu-id="e684c-145">Custom scenario</span></span>

<span data-ttu-id="e684c-146">Vlastní scénář umožňuje ručně zvolit scénář.</span><span class="sxs-lookup"><span data-stu-id="e684c-146">The custom scenario allows you to manually choose your scenario.</span></span>

## <a name="data"></a><span data-ttu-id="e684c-147">Data</span><span class="sxs-lookup"><span data-stu-id="e684c-147">Data</span></span>

<span data-ttu-id="e684c-148">Jakmile jste si vybrali scénář, Tvůrce modelů vás požádá o poskytnutí datové sady.</span><span class="sxs-lookup"><span data-stu-id="e684c-148">Once you have chosen your scenario, Model Builder asks you to provide a dataset.</span></span> <span data-ttu-id="e684c-149">Data se používají k trénování, vyhodnocení a výběru nejlepšího modelu pro váš scénář.</span><span class="sxs-lookup"><span data-stu-id="e684c-149">The data is used to train, evaluate, and choose the best model for your scenario.</span></span>

![Diagram znázorňující kroky tvůrce modelů](media/model-builder-steps.png)

<span data-ttu-id="e684c-151">Tvůrce modelů podporuje datové sady ve formátech TSV, .csv, .txt a také ve formátu databáze SQL.</span><span class="sxs-lookup"><span data-stu-id="e684c-151">Model Builder supports datasets in .tsv, .csv, .txt formats, as well as SQL database format.</span></span> <span data-ttu-id="e684c-152">Pokud máte soubor TXT, sloupce by `,`měly být odděleny pomocí aplikace nebo `;` a `/t` soubor musí mít řádek záhlaví.</span><span class="sxs-lookup"><span data-stu-id="e684c-152">If you have a .txt file, columns should be separated with `,`, `;` or `/t` and the file must have a header row.</span></span>

<span data-ttu-id="e684c-153">Pokud je datová sada tvořena obrázky, `.jpg` `.png`jsou podporované typy souborů a .</span><span class="sxs-lookup"><span data-stu-id="e684c-153">If the dataset is made up of images, the supported file types are `.jpg` and `.png`.</span></span>

<span data-ttu-id="e684c-154">Další informace naleznete v [tématu Načítání dat školení do Tvůrce modelů](how-to-guides/load-data-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="e684c-154">For more information, see [Load training data into Model Builder](how-to-guides/load-data-model-builder.md).</span></span>

### <a name="choose-the-output-to-predict-label"></a><span data-ttu-id="e684c-155">Zvolte výstup, který chcete předpovědět (popisek)</span><span class="sxs-lookup"><span data-stu-id="e684c-155">Choose the output to predict (label)</span></span>

<span data-ttu-id="e684c-156">Datová sada je tabulka řádků příkladů školení a sloupců atributů.</span><span class="sxs-lookup"><span data-stu-id="e684c-156">A dataset is a table of rows of training examples, and columns of attributes.</span></span> <span data-ttu-id="e684c-157">Každý řádek má:</span><span class="sxs-lookup"><span data-stu-id="e684c-157">Each row has:</span></span>

- <span data-ttu-id="e684c-158">**popisek** (atribut, který chcete předpovědět)</span><span class="sxs-lookup"><span data-stu-id="e684c-158">a **label** (the attribute that you want to predict)</span></span>
- <span data-ttu-id="e684c-159">**(atributy,** které se používají jako vstupy k předvídání popisku).</span><span class="sxs-lookup"><span data-stu-id="e684c-159">**features** (attributes that are used as inputs to predict the label).</span></span>

<span data-ttu-id="e684c-160">Pro scénář předpověď ceny domu by funkce mohly být:</span><span class="sxs-lookup"><span data-stu-id="e684c-160">For the house-price prediction scenario, the features could be:</span></span>

- <span data-ttu-id="e684c-161">čtvercový záběr domu</span><span class="sxs-lookup"><span data-stu-id="e684c-161">the square footage of the house</span></span>
- <span data-ttu-id="e684c-162">počet ložnic a koupelen</span><span class="sxs-lookup"><span data-stu-id="e684c-162">the number of bedrooms and bathrooms</span></span>
- <span data-ttu-id="e684c-163">PSČ</span><span class="sxs-lookup"><span data-stu-id="e684c-163">the zip code</span></span>

<span data-ttu-id="e684c-164">Štítek je historická cena domu pro tuto řadu čtverečních záběrů, ložnice a koupelna hodnoty a PSČ.</span><span class="sxs-lookup"><span data-stu-id="e684c-164">The label is the historical house price for that row of square footage, bedroom, and bathroom values and zip code.</span></span>

![Tabulka zobrazující řádky a sloupce údajů o cenách domu s funkcemi skládajícími se z velikostních místností PSČ a cenový štítek](media/model-builder-data.png)

### <a name="example-datasets"></a><span data-ttu-id="e684c-166">Ukázkové datové sady</span><span class="sxs-lookup"><span data-stu-id="e684c-166">Example datasets</span></span>

<span data-ttu-id="e684c-167">Pokud ještě nemáte vlastní data, vyzkoušejte jednu z těchto datových sad:</span><span class="sxs-lookup"><span data-stu-id="e684c-167">If you don't have your own data yet, try out one of these datasets:</span></span>

|<span data-ttu-id="e684c-168">Scénář</span><span class="sxs-lookup"><span data-stu-id="e684c-168">Scenario</span></span>|<span data-ttu-id="e684c-169">Úloha ML</span><span class="sxs-lookup"><span data-stu-id="e684c-169">ML task</span></span>|<span data-ttu-id="e684c-170">Data</span><span class="sxs-lookup"><span data-stu-id="e684c-170">Data</span></span>|<span data-ttu-id="e684c-171">Popisek</span><span class="sxs-lookup"><span data-stu-id="e684c-171">Label</span></span>|<span data-ttu-id="e684c-172">Funkce</span><span class="sxs-lookup"><span data-stu-id="e684c-172">Features</span></span>|
|-|-|-|-|-|
|<span data-ttu-id="e684c-173">Predikce cen</span><span class="sxs-lookup"><span data-stu-id="e684c-173">Price prediction</span></span>|<span data-ttu-id="e684c-174">Regrese</span><span class="sxs-lookup"><span data-stu-id="e684c-174">regression</span></span>|[<span data-ttu-id="e684c-175">údaje o jízdném taxislužby</span><span class="sxs-lookup"><span data-stu-id="e684c-175">taxi fare data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|<span data-ttu-id="e684c-176">Jízdné</span><span class="sxs-lookup"><span data-stu-id="e684c-176">Fare</span></span>|<span data-ttu-id="e684c-177">Doba jízdy, vzdálenost</span><span class="sxs-lookup"><span data-stu-id="e684c-177">Trip time, distance</span></span>|
|<span data-ttu-id="e684c-178">Detekce anomálií</span><span class="sxs-lookup"><span data-stu-id="e684c-178">Anomaly detection</span></span>|<span data-ttu-id="e684c-179">binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="e684c-179">binary classification</span></span>|[<span data-ttu-id="e684c-180">údaje o prodeji produktů</span><span class="sxs-lookup"><span data-stu-id="e684c-180">product sales data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|<span data-ttu-id="e684c-181">Prodej produktů</span><span class="sxs-lookup"><span data-stu-id="e684c-181">Product Sales</span></span>|<span data-ttu-id="e684c-182">Month</span><span class="sxs-lookup"><span data-stu-id="e684c-182">Month</span></span>|
|<span data-ttu-id="e684c-183">Analýza mínění</span><span class="sxs-lookup"><span data-stu-id="e684c-183">Sentiment analysis</span></span>|<span data-ttu-id="e684c-184">binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="e684c-184">binary classification</span></span>|[<span data-ttu-id="e684c-185">údaje o komentářích k webovým stránkám</span><span class="sxs-lookup"><span data-stu-id="e684c-185">website comment data</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|<span data-ttu-id="e684c-186">Popisek (0 při negativním sentimentu, 1 pozitivní)</span><span class="sxs-lookup"><span data-stu-id="e684c-186">Label (0 when negative sentiment, 1 when positive)</span></span>|<span data-ttu-id="e684c-187">Komentář, rok</span><span class="sxs-lookup"><span data-stu-id="e684c-187">Comment, Year</span></span>|
|<span data-ttu-id="e684c-188">Odhalování podvodů</span><span class="sxs-lookup"><span data-stu-id="e684c-188">Fraud detection</span></span>|<span data-ttu-id="e684c-189">binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="e684c-189">binary classification</span></span>|[<span data-ttu-id="e684c-190">Údaje o kreditní kartě</span><span class="sxs-lookup"><span data-stu-id="e684c-190">credit card data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|<span data-ttu-id="e684c-191">Třída (1 v případě podvodného, 0 jinak)</span><span class="sxs-lookup"><span data-stu-id="e684c-191">Class (1 when fraudulent, 0 otherwise)</span></span>|<span data-ttu-id="e684c-192">Částka, V1-V28 (anonymizované funkce)</span><span class="sxs-lookup"><span data-stu-id="e684c-192">Amount, V1-V28 (anonymized features)</span></span>|
|<span data-ttu-id="e684c-193">Klasifikace textu</span><span class="sxs-lookup"><span data-stu-id="e684c-193">Text classification</span></span>|<span data-ttu-id="e684c-194">klasifikace více tříd</span><span class="sxs-lookup"><span data-stu-id="e684c-194">multiclass classification</span></span>|[<span data-ttu-id="e684c-195">Data problému GitHubu</span><span class="sxs-lookup"><span data-stu-id="e684c-195">GitHub issue data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|<span data-ttu-id="e684c-196">Oblast</span><span class="sxs-lookup"><span data-stu-id="e684c-196">Area</span></span>|<span data-ttu-id="e684c-197">Název, popis</span><span class="sxs-lookup"><span data-stu-id="e684c-197">Title, Description</span></span>|
|<span data-ttu-id="e684c-198">Klasifikace obrázků</span><span class="sxs-lookup"><span data-stu-id="e684c-198">Image classification</span></span>|<span data-ttu-id="e684c-199">klasifikace více tříd</span><span class="sxs-lookup"><span data-stu-id="e684c-199">multiclass classification</span></span>|[<span data-ttu-id="e684c-200">Květiny obrázky</span><span class="sxs-lookup"><span data-stu-id="e684c-200">Flowers images</span></span>](http://download.tensorflow.org/example_images/flower_photos.tgz)|<span data-ttu-id="e684c-201">Typ květiny: sedmikráska, pampeliška, růže, slunečnice, tulipány</span><span class="sxs-lookup"><span data-stu-id="e684c-201">The type of flower: daisy, dandelion, roses, sunflowers, tulips</span></span>|<span data-ttu-id="e684c-202">Samotná obrazová data</span><span class="sxs-lookup"><span data-stu-id="e684c-202">The image data itself</span></span>|

## <a name="train"></a><span data-ttu-id="e684c-203">Trénování</span><span class="sxs-lookup"><span data-stu-id="e684c-203">Train</span></span>

<span data-ttu-id="e684c-204">Jakmile vyberete scénář, data a popisek, Tvůrce modelů trénuje model.</span><span class="sxs-lookup"><span data-stu-id="e684c-204">Once you select your scenario, data, and label, Model Builder trains the model.</span></span>

### <a name="what-is-training"></a><span data-ttu-id="e684c-205">Co je trénink?</span><span class="sxs-lookup"><span data-stu-id="e684c-205">What is training?</span></span>

<span data-ttu-id="e684c-206">Školení je automatický proces, pomocí kterého Tvůrce modelů učí váš model, jak odpovídat na otázky pro váš scénář.</span><span class="sxs-lookup"><span data-stu-id="e684c-206">Training is an automatic process by which Model Builder teaches your model how to answer questions for your scenario.</span></span> <span data-ttu-id="e684c-207">Po tréninu, váš model můžete předpovědět se vstupními daty, které dosud neviděl.</span><span class="sxs-lookup"><span data-stu-id="e684c-207">Once trained, your model can make predictions with input data that it has not seen before.</span></span> <span data-ttu-id="e684c-208">Například, pokud jste předpovídají ceny domů a nový dům přichází na trh, můžete předpovědět jeho prodejní cenu.</span><span class="sxs-lookup"><span data-stu-id="e684c-208">For example, if you are predicting house prices and a new house comes on the market, you can predict its sale price.</span></span>

<span data-ttu-id="e684c-209">Vzhledem k tomu, že Model Builder používá automatizované strojové učení (AutoML), nevyžaduje žádný vstup nebo ladění od vás během školení.</span><span class="sxs-lookup"><span data-stu-id="e684c-209">Because Model Builder uses automated machine learning (AutoML), it does not require any input or tuning from you during training.</span></span>

### <a name="how-long-should-i-train-for"></a><span data-ttu-id="e684c-210">Na jak dlouho mám trénovat?</span><span class="sxs-lookup"><span data-stu-id="e684c-210">How long should I train for?</span></span>

<span data-ttu-id="e684c-211">Tvůrce modelů používá AutoML k prozkoumání více modelů a vyhledá vám nejvýkonnější model.</span><span class="sxs-lookup"><span data-stu-id="e684c-211">Model Builder uses AutoML to explore multiple models to find you the best performing model.</span></span>

<span data-ttu-id="e684c-212">Delší tréninkové období umožňují automatické kontrole prozkoumat další modely s širším rozsahem nastavení.</span><span class="sxs-lookup"><span data-stu-id="e684c-212">Longer training periods allow AutoML to explore more models with a wider range of settings.</span></span>

<span data-ttu-id="e684c-213">Níže uvedená tabulka shrnuje průměrnou dobu, kterou je třeba získat dobrý výkon pro sadu ukázkových datových sad v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="e684c-213">The table below summarizes the average time taken to get good performance for a suite of example datasets, on a local machine.</span></span>

|<span data-ttu-id="e684c-214">Velikost datové sady</span><span class="sxs-lookup"><span data-stu-id="e684c-214">Dataset size</span></span>|<span data-ttu-id="e684c-215">Průměrná doba tréninku</span><span class="sxs-lookup"><span data-stu-id="e684c-215">Average time to train</span></span>|
|------------|---------------------|
|<span data-ttu-id="e684c-216">0 - 10 MB</span><span class="sxs-lookup"><span data-stu-id="e684c-216">0 - 10 MB</span></span>|<span data-ttu-id="e684c-217">10 s</span><span class="sxs-lookup"><span data-stu-id="e684c-217">10 sec</span></span>|
|<span data-ttu-id="e684c-218">10 - 100 MB</span><span class="sxs-lookup"><span data-stu-id="e684c-218">10 - 100 MB</span></span>|<span data-ttu-id="e684c-219">10 min</span><span class="sxs-lookup"><span data-stu-id="e684c-219">10 min</span></span>|
|<span data-ttu-id="e684c-220">100 - 500 MB</span><span class="sxs-lookup"><span data-stu-id="e684c-220">100 - 500 MB</span></span>|<span data-ttu-id="e684c-221">30 min</span><span class="sxs-lookup"><span data-stu-id="e684c-221">30 min</span></span>|
|<span data-ttu-id="e684c-222">500 - 1 GB</span><span class="sxs-lookup"><span data-stu-id="e684c-222">500 - 1 GB</span></span>|<span data-ttu-id="e684c-223">60 min</span><span class="sxs-lookup"><span data-stu-id="e684c-223">60 min</span></span>|
|<span data-ttu-id="e684c-224">1 GB+</span><span class="sxs-lookup"><span data-stu-id="e684c-224">1 GB+</span></span>|<span data-ttu-id="e684c-225">3+ hodiny</span><span class="sxs-lookup"><span data-stu-id="e684c-225">3+ hours</span></span>|

<span data-ttu-id="e684c-226">Tato čísla jsou pouze vodítkem.</span><span class="sxs-lookup"><span data-stu-id="e684c-226">These numbers are a guide only.</span></span> <span data-ttu-id="e684c-227">Přesná délka tréninku závisí na:</span><span class="sxs-lookup"><span data-stu-id="e684c-227">The exact length of training is dependent on:</span></span>

- <span data-ttu-id="e684c-228">počet prvků (sloupců), které se používají jako vstup do modelu</span><span class="sxs-lookup"><span data-stu-id="e684c-228">the number of features (columns) being used to as input to the model</span></span>
- <span data-ttu-id="e684c-229">typ sloupců</span><span class="sxs-lookup"><span data-stu-id="e684c-229">the type of columns</span></span>
- <span data-ttu-id="e684c-230">úloha ML</span><span class="sxs-lookup"><span data-stu-id="e684c-230">the ML task</span></span>
- <span data-ttu-id="e684c-231">výkon procesoru, disku a paměti stroje používaného pro trénování</span><span class="sxs-lookup"><span data-stu-id="e684c-231">the CPU, disk and memory performance of the machine used for training</span></span>

## <a name="evaluate"></a><span data-ttu-id="e684c-232">Vyhodnotit</span><span class="sxs-lookup"><span data-stu-id="e684c-232">Evaluate</span></span>

<span data-ttu-id="e684c-233">Hodnocení je proces měření toho, jak dobrý je váš model.</span><span class="sxs-lookup"><span data-stu-id="e684c-233">Evaluation is the process of measuring how good your model is.</span></span> <span data-ttu-id="e684c-234">Tvůrce modelů používá trénovaný model k předpovědi s nová testovací data a pak měří, jak dobré předpovědi jsou.</span><span class="sxs-lookup"><span data-stu-id="e684c-234">Model Builder uses the trained model to make predictions with new test data, and then measures how good the predictions are.</span></span>

<span data-ttu-id="e684c-235">Tvůrce modelů rozdělí trénovací data do trénovací sady a testovací sady.</span><span class="sxs-lookup"><span data-stu-id="e684c-235">Model Builder splits the training data into a training set and a test set.</span></span> <span data-ttu-id="e684c-236">Údaje o školení (80 %) se používá k trénování modelu a testovacích dat (20 %) je držen zpět k vyhodnocení modelu.</span><span class="sxs-lookup"><span data-stu-id="e684c-236">The training data (80%) is used to train your model and the test data (20%) is held back to evaluate your model.</span></span>

### <a name="how-do-i-understand-my-model-performance"></a><span data-ttu-id="e684c-237">Jak rozumím výkonu modelu?</span><span class="sxs-lookup"><span data-stu-id="e684c-237">How do I understand my model performance?</span></span>

<span data-ttu-id="e684c-238">Scénář se mapuje na úlohu strojového učení.</span><span class="sxs-lookup"><span data-stu-id="e684c-238">A scenario maps to a machine learning task.</span></span> <span data-ttu-id="e684c-239">Každý úkol ML má vlastní sadu metrik hodnocení.</span><span class="sxs-lookup"><span data-stu-id="e684c-239">Each ML task has its own set of evaluation metrics.</span></span>

#### <a name="regression-for-example-price-prediction"></a><span data-ttu-id="e684c-240">Regrese (například Cenová předpověď)</span><span class="sxs-lookup"><span data-stu-id="e684c-240">Regression (for example, Price Prediction)</span></span>

<span data-ttu-id="e684c-241">Výchozí metrika pro regresní problémy je RSquared, hodnota RSquared rozsahy mezi 0 a 1.</span><span class="sxs-lookup"><span data-stu-id="e684c-241">The default metric for regression problems is RSquared, the value of RSquared ranges between 0 and 1.</span></span> <span data-ttu-id="e684c-242">1 je nejlepší možná hodnota, nebo jinými slovy, čím blíže hodnota RSquared na 1, tím lépe váš model je výkon.</span><span class="sxs-lookup"><span data-stu-id="e684c-242">1 is the best possible value or in other words the closer the value of RSquared to 1 the better your model is performing.</span></span>

<span data-ttu-id="e684c-243">Další metriky hlášené, jako je absolutní ztráta, kvadratická ztráta a ztráta RMS, jsou další metriky, které lze použít k pochopení toho, jak si váš model vede, a k jeho porovnání s jinými regresními modely.</span><span class="sxs-lookup"><span data-stu-id="e684c-243">Other metrics reported such as absolute-loss, squared-loss, and RMS loss are additional metrics, which can be used to understand how your model is performing and comparing it against other regression models.</span></span>

#### <a name="binary-classification-for-example-sentiment-analysis"></a><span data-ttu-id="e684c-244">Binární klasifikace (například analýza mínění)</span><span class="sxs-lookup"><span data-stu-id="e684c-244">Binary Classification (for example, Sentiment Analysis)</span></span>

<span data-ttu-id="e684c-245">Výchozí metrika pro problémy s klasifikací je přesnost.</span><span class="sxs-lookup"><span data-stu-id="e684c-245">The default metric for classification problems is accuracy.</span></span> <span data-ttu-id="e684c-246">Přesnost definuje podíl správné předpovědi modelu je dělat přes testovací datové sady.</span><span class="sxs-lookup"><span data-stu-id="e684c-246">Accuracy defines the proportion of correct predictions your model is making over the test dataset.</span></span> <span data-ttu-id="e684c-247">Čím blíže k 100% nebo 1,0, tím lépe.</span><span class="sxs-lookup"><span data-stu-id="e684c-247">The closer to 100% or 1.0 the better it is.</span></span>

<span data-ttu-id="e684c-248">Další hlášené metriky, například AUC (Plocha pod křivkou), která měří skutečně pozitivní míru vs. míra falešně pozitivních hodnot by měla být vyšší než 0,50, aby byly modely přijatelné.</span><span class="sxs-lookup"><span data-stu-id="e684c-248">Other metrics reported such as AUC (Area under the curve), which measures the true positive rate vs. the false positive rate should be greater than 0.50 for models to be acceptable.</span></span>

<span data-ttu-id="e684c-249">Další metriky, jako je skóre F1, lze použít k řízení rovnováhy mezi přesností a odvoláním.</span><span class="sxs-lookup"><span data-stu-id="e684c-249">Additional metrics like F1 score can be used to control the balance between Precision and Recall.</span></span>

#### <a name="multi-class-classification-for-example-issue-classification-image-classification"></a><span data-ttu-id="e684c-250">Klasifikace více tříd (například klasifikace vydání, klasifikace obrázků)</span><span class="sxs-lookup"><span data-stu-id="e684c-250">Multi-Class Classification (for example, Issue Classification, Image Classification)</span></span>

<span data-ttu-id="e684c-251">Výchozí metrika pro klasifikaci více tříd je Mikro přesnost.</span><span class="sxs-lookup"><span data-stu-id="e684c-251">The default metric for Multi-class classification is Micro Accuracy.</span></span> <span data-ttu-id="e684c-252">Čím blíže je mikropřesnost na 100% nebo 1,0, tím lepší je.</span><span class="sxs-lookup"><span data-stu-id="e684c-252">The closer the Micro Accuracy to 100% or 1.0 the better it is.</span></span>

<span data-ttu-id="e684c-253">Další důležitou metrikou pro klasifikaci více tříd je makropřesnost, podobná mikropřesnosti, čím blíže k 1.0, tím lépe.</span><span class="sxs-lookup"><span data-stu-id="e684c-253">Another important metric for Multi-class classification is Macro-accuracy, similar to Micro-accuracy the closer to 1.0 the better it is.</span></span> <span data-ttu-id="e684c-254">Dobrý způsob, jak přemýšlet o těchto dvou typech přesnosti je:</span><span class="sxs-lookup"><span data-stu-id="e684c-254">A good way to think about these two types of accuracy is:</span></span>

- <span data-ttu-id="e684c-255">Mikropřesnost: Jak často se příchozí jízdenka klasifikuje do správného týmu?</span><span class="sxs-lookup"><span data-stu-id="e684c-255">Micro-accuracy: How often does an incoming ticket get classified to the right team?</span></span>
- <span data-ttu-id="e684c-256">Makropřesnost: Jak často je pro průměrný tým příchozí lístek pro jejich tým správný?</span><span class="sxs-lookup"><span data-stu-id="e684c-256">Macro-accuracy: For an average team, how often is an incoming ticket correct for their team?</span></span>

### <a name="more-information-on-evaluation-metrics"></a><span data-ttu-id="e684c-257">Další informace o hodnotících metrikách</span><span class="sxs-lookup"><span data-stu-id="e684c-257">More information on evaluation metrics</span></span>

<span data-ttu-id="e684c-258">Další informace naleznete v tématu [metriky vyhodnocení modelu](resources/metrics.md).</span><span class="sxs-lookup"><span data-stu-id="e684c-258">For more information, see [model evaluation metrics](resources/metrics.md).</span></span>

## <a name="improve"></a><span data-ttu-id="e684c-259">Zlepšit</span><span class="sxs-lookup"><span data-stu-id="e684c-259">Improve</span></span>

<span data-ttu-id="e684c-260">Pokud skóre výkonu modelu není tak dobré, jak chcete, můžete:</span><span class="sxs-lookup"><span data-stu-id="e684c-260">If your model performance score is not as good as you want it to be, you can:</span></span>

- <span data-ttu-id="e684c-261">Trénujte delší dobu.</span><span class="sxs-lookup"><span data-stu-id="e684c-261">Train for a longer period of time.</span></span> <span data-ttu-id="e684c-262">S více času, automatizovaný strojové učení motor vyzkoušet další algoritmy a nastavení.</span><span class="sxs-lookup"><span data-stu-id="e684c-262">With more time, the automated machine learning engine to try more algorithms and settings.</span></span>

- <span data-ttu-id="e684c-263">Přidejte další data.</span><span class="sxs-lookup"><span data-stu-id="e684c-263">Add more data.</span></span> <span data-ttu-id="e684c-264">Někdy množství dat není dostatečná pro trénování vysoce kvalitní model strojového učení.</span><span class="sxs-lookup"><span data-stu-id="e684c-264">Sometimes the amount of data is not sufficient to train a high-quality machine learning model.</span></span>

- <span data-ttu-id="e684c-265">Vyvažte svá data.</span><span class="sxs-lookup"><span data-stu-id="e684c-265">Balance your data.</span></span> <span data-ttu-id="e684c-266">Pro úkoly klasifikace, ujistěte se, že sada školení je vyvážená mezi kategoriemi.</span><span class="sxs-lookup"><span data-stu-id="e684c-266">For classification tasks, make sure that the training set is balanced across the categories.</span></span> <span data-ttu-id="e684c-267">Například pokud máte čtyři třídy pro 100 příklady školení a dvě první třídy (tag1 a tag2) se používají pro 90 záznamů, ale další dva (tag3 a tag4) se používají pouze na zbývajících 10 záznamů, nedostatek vyvážených dat může způsobit, že váš model bojovat správně předpovědět tag3 nebo tag4.</span><span class="sxs-lookup"><span data-stu-id="e684c-267">For example, if you have four classes for 100 training examples, and the two first classes (tag1 and tag2) are used for 90 records, but the other two (tag3 and tag4) are only used on the remaining 10 records, the lack of balanced data may cause your model to struggle to correctly predict tag3 or tag4.</span></span>

## <a name="code"></a><span data-ttu-id="e684c-268">kód</span><span class="sxs-lookup"><span data-stu-id="e684c-268">Code</span></span>

<span data-ttu-id="e684c-269">Po fázi vyhodnocení Tvůrce modelů vydělá soubor modelu a kód, který můžete použít k přidání modelu do aplikace.</span><span class="sxs-lookup"><span data-stu-id="e684c-269">After the evaluation phase, Model Builder outputs a model file, and code that you can use to add the model to your application.</span></span> <span data-ttu-id="e684c-270">ML.NET modely jsou uloženy jako soubor zip.</span><span class="sxs-lookup"><span data-stu-id="e684c-270">ML.NET models are saved as a zip file.</span></span> <span data-ttu-id="e684c-271">Kód pro načtení a použití modelu je přidán jako nový projekt ve vašem řešení.</span><span class="sxs-lookup"><span data-stu-id="e684c-271">The code to load and use your model is added as a new project in your solution.</span></span> <span data-ttu-id="e684c-272">Tvůrce modelů také přidá ukázkovou konzolovou aplikaci, kterou můžete spustit, abyste viděli model v akci.</span><span class="sxs-lookup"><span data-stu-id="e684c-272">Model Builder also adds a sample console app that you can run to see your model in action.</span></span>

<span data-ttu-id="e684c-273">Kromě toho Tvůrce modelů vygeneruje kód, který vygeneroval model, takže můžete pochopit kroky použité ke generování modelu.</span><span class="sxs-lookup"><span data-stu-id="e684c-273">In addition, Model Builder outputs the code that generated the model, so that you can understand the steps used to generate the model.</span></span> <span data-ttu-id="e684c-274">Můžete také použít model trénovací kód pro přeškolit model s novými daty.</span><span class="sxs-lookup"><span data-stu-id="e684c-274">You can also use the model training code to retrain your model with new data.</span></span>

## <a name="whats-next"></a><span data-ttu-id="e684c-275">Co dále?</span><span class="sxs-lookup"><span data-stu-id="e684c-275">What's next?</span></span>

<span data-ttu-id="e684c-276">[Instalace](how-to-guides/install-model-builder.md) rozšíření Visual Studio tvůrce modelů</span><span class="sxs-lookup"><span data-stu-id="e684c-276">[Install](how-to-guides/install-model-builder.md) the Model Builder Visual Studio extension</span></span>

<span data-ttu-id="e684c-277">Vyzkoušejte [predikci ceny nebo jakýkoli regresní scénář](tutorials/predict-prices-with-model-builder.md)</span><span class="sxs-lookup"><span data-stu-id="e684c-277">Try [price prediction or any regression scenario](tutorials/predict-prices-with-model-builder.md)</span></span>
