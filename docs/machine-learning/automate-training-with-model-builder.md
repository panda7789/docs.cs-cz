---
title: Co je model builder a jak to funguje?
description: Jak používat ML.NET Model Builder automaticky trénovat model strojového učení
ms.date: 03/25/2020
ms.custom: overview, mlnet-tooling
ms.openlocfilehash: 9cf66455109908ebd9fc10e62cf4f067609b57d9
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344769"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a><span data-ttu-id="be720-103">Co je model builder a jak to funguje?</span><span class="sxs-lookup"><span data-stu-id="be720-103">What is Model Builder and how does it work?</span></span>

<span data-ttu-id="be720-104">ML.NET Model Builder je intuitivní grafické rozšíření Sady Visual Studio pro vytváření, trénování a nasazování vlastních modelů strojového učení.</span><span class="sxs-lookup"><span data-stu-id="be720-104">ML.NET Model Builder is an intuitive graphical Visual Studio extension to build, train, and deploy custom machine learning models.</span></span>

<span data-ttu-id="be720-105">Model Builder používá automatizované strojové učení (AutoML) k prozkoumání různých algoritmů a nastavení strojového učení, které vám pomohou najít ten, který nejlépe vyhovuje vašemu scénáři.</span><span class="sxs-lookup"><span data-stu-id="be720-105">Model Builder uses automated machine learning (AutoML) to explore different machine learning algorithms and settings to help you find the one that best suits your scenario.</span></span>

<span data-ttu-id="be720-106">K používání modelového tvůrce nepotřebujete odborné znalosti strojového učení.</span><span class="sxs-lookup"><span data-stu-id="be720-106">You don't need machine learning expertise to use Model Builder.</span></span> <span data-ttu-id="be720-107">Vše, co potřebujete, jsou nějaká data a problém k vyřešení.</span><span class="sxs-lookup"><span data-stu-id="be720-107">All you need is some data, and a problem to solve.</span></span> <span data-ttu-id="be720-108">Tvůrce modelů generuje kód pro přidání modelu do aplikace .NET.</span><span class="sxs-lookup"><span data-stu-id="be720-108">Model Builder generates the code to add the model to your .NET application.</span></span>

![Animace uživatelského rozhraní rozšíření Visual Studio tvůrce modelů](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> <span data-ttu-id="be720-110">Tvůrce modelů je momentálně ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="be720-110">Model Builder is currently in Preview.</span></span>

## <a name="scenario"></a><span data-ttu-id="be720-111">Scénář</span><span class="sxs-lookup"><span data-stu-id="be720-111">Scenario</span></span>

<span data-ttu-id="be720-112">Můžete přinést mnoho různých scénářů model builder, generovat model strojového učení pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="be720-112">You can bring many different scenarios to Model Builder, to generate a machine learning model for your application.</span></span>

<span data-ttu-id="be720-113">Scénář je popis typu předpověď, kterou chcete provést pomocí dat.</span><span class="sxs-lookup"><span data-stu-id="be720-113">A scenario is a description of the type of prediction you want to make using your data.</span></span> <span data-ttu-id="be720-114">Například:</span><span class="sxs-lookup"><span data-stu-id="be720-114">For example:</span></span>

- <span data-ttu-id="be720-115">předpovědět budoucí objem prodeje produktů na základě historických údajů o prodeji</span><span class="sxs-lookup"><span data-stu-id="be720-115">predict future product sales volume based on historical sales data</span></span>
- <span data-ttu-id="be720-116">klasifikovaly názory jako pozitivní nebo negativní na základě recenzí zákazníků</span><span class="sxs-lookup"><span data-stu-id="be720-116">classify sentiments as positive or negative based on customer reviews</span></span>
- <span data-ttu-id="be720-117">zjistit, zda je bankovní transakce podvodná</span><span class="sxs-lookup"><span data-stu-id="be720-117">detect whether a banking transaction is fraudulent</span></span>
- <span data-ttu-id="be720-118">směrovat problémy se zpětnou vazbou od zákazníků ke správnému týmu ve vaší společnosti</span><span class="sxs-lookup"><span data-stu-id="be720-118">route customer feedback issues to the correct team in your company</span></span>

### <a name="which-machine-learning-scenario-is-right-for-me"></a><span data-ttu-id="be720-119">Který scénář strojového učení je pro mě ten pravý?</span><span class="sxs-lookup"><span data-stu-id="be720-119">Which machine learning scenario is right for me?</span></span>

<span data-ttu-id="be720-120">V Tvůrce modelů je třeba vybrat scénář.</span><span class="sxs-lookup"><span data-stu-id="be720-120">In Model Builder, you need to select a scenario.</span></span> <span data-ttu-id="be720-121">Typ scénáře závisí na typu předpověď, kterou se pokoušíte provést.</span><span class="sxs-lookup"><span data-stu-id="be720-121">The type of scenario depends on what type of prediction you are trying to make.</span></span>

#### <a name="text-classification"></a><span data-ttu-id="be720-122">Klasifikace textu</span><span class="sxs-lookup"><span data-stu-id="be720-122">Text classification</span></span>

<span data-ttu-id="be720-123">Klasifikace se používá ke kategorizaci dat do kategorií.</span><span class="sxs-lookup"><span data-stu-id="be720-123">Classification is used to categorize data into categories.</span></span>

![Diagram znázorňující příklady binární klasifikace včetně detekce podvodů, zmírnění rizika a screeningu aplikací](media/binary-classification-examples.png)

![Příklady klasifikace více tříd, včetně klasifikace dokumentů a produktů, směrování lístků podpory a stanovení priorit problémů zákazníků](media/multiclass-classification-examples.png)

#### <a name="value-prediction"></a><span data-ttu-id="be720-126">Predikce hodnoty</span><span class="sxs-lookup"><span data-stu-id="be720-126">Value prediction</span></span>

<span data-ttu-id="be720-127">Regrese se používá k předvídání čísel.</span><span class="sxs-lookup"><span data-stu-id="be720-127">Regression is used to predict numbers.</span></span>

![Diagram znázorňující příklady regresní ceny, jako je predikce cen, prognóza prodeje a prediktivní údržba](media/regression-examples.png)

#### <a name="image-classification"></a><span data-ttu-id="be720-129">Klasifikace obrázků</span><span class="sxs-lookup"><span data-stu-id="be720-129">Image classification</span></span>

<span data-ttu-id="be720-130">Klasifikace obrázků lze použít k identifikaci obrázků různých kategorií.</span><span class="sxs-lookup"><span data-stu-id="be720-130">Image classification can be used to identify images of different categories.</span></span> <span data-ttu-id="be720-131">Například různé typy terénu nebo zvířat nebo výrobní vady.</span><span class="sxs-lookup"><span data-stu-id="be720-131">For example, different types of terrain or animals or manufacturing defects.</span></span>

<span data-ttu-id="be720-132">Scénář klasifikace obrázků můžete použít, pokud máte sadu obrázků a chcete je klasifikovat do různých kategorií.</span><span class="sxs-lookup"><span data-stu-id="be720-132">You can use the image classification scenario if you have a set of images, and you want to classify the images into different categories.</span></span>

#### <a name="recommendation"></a><span data-ttu-id="be720-133">Doporučení</span><span class="sxs-lookup"><span data-stu-id="be720-133">Recommendation</span></span>

<span data-ttu-id="be720-134">Scénář doporučení předpovídá seznam navržených položek pro konkrétního uživatele na základě toho, jak podobné jsou jejich to se mi líbí a nelíbí ostatním uživatelům.</span><span class="sxs-lookup"><span data-stu-id="be720-134">The recommendation scenario predicts a list of suggested items for a particular user, based on how similar their likes and dislikes are to other users'.</span></span>

<span data-ttu-id="be720-135">Scénář doporučení můžete použít, pokud máte sadu uživatelů a sadu "produktů", jako jsou položky k nákupu, filmy, knihy nebo televizní pořady, spolu se sadou "hodnocení" uživatelů těchto produktů.</span><span class="sxs-lookup"><span data-stu-id="be720-135">You can use the recommendation scenario when you have a set of users and a set of "products", such as items to purchase, movies, books, or TV shows, along with a set of users' "ratings" of those products.</span></span>

## <a name="environment"></a><span data-ttu-id="be720-136">Prostředí</span><span class="sxs-lookup"><span data-stu-id="be720-136">Environment</span></span>

<span data-ttu-id="be720-137">Model strojového učení můžete trénovat místně na počítači nebo v cloudu v Azure.</span><span class="sxs-lookup"><span data-stu-id="be720-137">You can train your machine learning model locally on your machine or in the cloud on Azure.</span></span>

<span data-ttu-id="be720-138">Při místním trénování pracujete v rámci omezení prostředků počítače (procesor, paměť a disk).</span><span class="sxs-lookup"><span data-stu-id="be720-138">When you train locally, you work within the constraints of your computer resources (CPU, memory, and disk).</span></span> <span data-ttu-id="be720-139">Když trénujete v cloudu, můžete vertikálně navýšit kapacitu prostředků tak, aby splňovaly požadavky vašeho scénáře, zejména pro velké datové sady.</span><span class="sxs-lookup"><span data-stu-id="be720-139">When you train in the cloud, you can scale up your resources to meet the demands of your scenario, especially for large datasets.</span></span>

<span data-ttu-id="be720-140">Místní školení je podporováno pro všechny scénáře.</span><span class="sxs-lookup"><span data-stu-id="be720-140">Local training is supported for all scenarios.</span></span>

<span data-ttu-id="be720-141">Azure školení je podporována pro klasifikaci obrázků.</span><span class="sxs-lookup"><span data-stu-id="be720-141">Azure training is supported for Image Classification.</span></span>

## <a name="data"></a><span data-ttu-id="be720-142">Data</span><span class="sxs-lookup"><span data-stu-id="be720-142">Data</span></span>

<span data-ttu-id="be720-143">Jakmile jste si vybrali scénář, Tvůrce modelů vás požádá o poskytnutí datové sady.</span><span class="sxs-lookup"><span data-stu-id="be720-143">Once you have chosen your scenario, Model Builder asks you to provide a dataset.</span></span> <span data-ttu-id="be720-144">Data se používají k trénování, vyhodnocení a výběru nejlepšího modelu pro váš scénář.</span><span class="sxs-lookup"><span data-stu-id="be720-144">The data is used to train, evaluate, and choose the best model for your scenario.</span></span>

![Diagram znázorňující kroky tvůrce modelů](media/model-builder-steps.png)

<span data-ttu-id="be720-146">Tvůrce modelů podporuje datové sady ve formátech TSV, .csv, .txt a také ve formátu databáze SQL.</span><span class="sxs-lookup"><span data-stu-id="be720-146">Model Builder supports datasets in .tsv, .csv, .txt formats, as well as SQL database format.</span></span> <span data-ttu-id="be720-147">Pokud máte soubor TXT, sloupce by `,`měly být odděleny pomocí aplikace nebo `;` a `/t` soubor musí mít řádek záhlaví.</span><span class="sxs-lookup"><span data-stu-id="be720-147">If you have a .txt file, columns should be separated with `,`, `;` or `/t` and the file must have a header row.</span></span>

<span data-ttu-id="be720-148">Pokud je datová sada tvořena obrázky, `.jpg` `.png`jsou podporované typy souborů a .</span><span class="sxs-lookup"><span data-stu-id="be720-148">If the dataset is made up of images, the supported file types are `.jpg` and `.png`.</span></span>

<span data-ttu-id="be720-149">Další informace naleznete v [tématu Načítání dat školení do Tvůrce modelů](how-to-guides/load-data-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="be720-149">For more information, see [Load training data into Model Builder](how-to-guides/load-data-model-builder.md).</span></span>

### <a name="choose-the-output-to-predict-label"></a><span data-ttu-id="be720-150">Zvolte výstup, který chcete předpovědět (popisek)</span><span class="sxs-lookup"><span data-stu-id="be720-150">Choose the output to predict (label)</span></span>

<span data-ttu-id="be720-151">Datová sada je tabulka řádků příkladů školení a sloupců atributů.</span><span class="sxs-lookup"><span data-stu-id="be720-151">A dataset is a table of rows of training examples, and columns of attributes.</span></span> <span data-ttu-id="be720-152">Každý řádek má:</span><span class="sxs-lookup"><span data-stu-id="be720-152">Each row has:</span></span>

- <span data-ttu-id="be720-153">**popisek** (atribut, který chcete předpovědět)</span><span class="sxs-lookup"><span data-stu-id="be720-153">a **label** (the attribute that you want to predict)</span></span>
- <span data-ttu-id="be720-154">**(atributy,** které se používají jako vstupy k předvídání popisku).</span><span class="sxs-lookup"><span data-stu-id="be720-154">**features** (attributes that are used as inputs to predict the label).</span></span>

<span data-ttu-id="be720-155">Pro scénář předpověď ceny domu by funkce mohly být:</span><span class="sxs-lookup"><span data-stu-id="be720-155">For the house-price prediction scenario, the features could be:</span></span>

- <span data-ttu-id="be720-156">čtvercový záběr domu</span><span class="sxs-lookup"><span data-stu-id="be720-156">the square footage of the house</span></span>
- <span data-ttu-id="be720-157">počet ložnic a koupelen</span><span class="sxs-lookup"><span data-stu-id="be720-157">the number of bedrooms and bathrooms</span></span>
- <span data-ttu-id="be720-158">PSČ</span><span class="sxs-lookup"><span data-stu-id="be720-158">the zip code</span></span>

<span data-ttu-id="be720-159">Štítek je historická cena domu pro tuto řadu čtverečních záběrů, ložnice a koupelna hodnoty a PSČ.</span><span class="sxs-lookup"><span data-stu-id="be720-159">The label is the historical house price for that row of square footage, bedroom, and bathroom values and zip code.</span></span>

![Tabulka zobrazující řádky a sloupce údajů o cenách domu s funkcemi skládajícími se z velikostních místností PSČ a cenový štítek](media/model-builder-data.png)

### <a name="example-datasets"></a><span data-ttu-id="be720-161">Ukázkové datové sady</span><span class="sxs-lookup"><span data-stu-id="be720-161">Example datasets</span></span>

<span data-ttu-id="be720-162">Pokud ještě nemáte vlastní data, vyzkoušejte jednu z těchto datových sad:</span><span class="sxs-lookup"><span data-stu-id="be720-162">If you don't have your own data yet, try out one of these datasets:</span></span>

|<span data-ttu-id="be720-163">Scénář</span><span class="sxs-lookup"><span data-stu-id="be720-163">Scenario</span></span>|<span data-ttu-id="be720-164">Příklad</span><span class="sxs-lookup"><span data-stu-id="be720-164">Example</span></span>|<span data-ttu-id="be720-165">Data</span><span class="sxs-lookup"><span data-stu-id="be720-165">Data</span></span>|<span data-ttu-id="be720-166">Popisek</span><span class="sxs-lookup"><span data-stu-id="be720-166">Label</span></span>|<span data-ttu-id="be720-167">Funkce</span><span class="sxs-lookup"><span data-stu-id="be720-167">Features</span></span>|
|-|-|-|-|-|
|<span data-ttu-id="be720-168">Classification</span><span class="sxs-lookup"><span data-stu-id="be720-168">Classification</span></span>|<span data-ttu-id="be720-169">Předvídání prodejních anomálií</span><span class="sxs-lookup"><span data-stu-id="be720-169">Predict sales anomalies</span></span>|[<span data-ttu-id="be720-170">údaje o prodeji produktů</span><span class="sxs-lookup"><span data-stu-id="be720-170">product sales data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|<span data-ttu-id="be720-171">Prodej produktů</span><span class="sxs-lookup"><span data-stu-id="be720-171">Product Sales</span></span>|<span data-ttu-id="be720-172">Month</span><span class="sxs-lookup"><span data-stu-id="be720-172">Month</span></span>|
||<span data-ttu-id="be720-173">Předpovědět mínění o komentářích k webovým stránkám</span><span class="sxs-lookup"><span data-stu-id="be720-173">Predict sentiment of website comments</span></span>|[<span data-ttu-id="be720-174">údaje o komentářích k webovým stránkám</span><span class="sxs-lookup"><span data-stu-id="be720-174">website comment data</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|<span data-ttu-id="be720-175">Popisek (0 při negativním sentimentu, 1 pozitivní)</span><span class="sxs-lookup"><span data-stu-id="be720-175">Label (0 when negative sentiment, 1 when positive)</span></span>|<span data-ttu-id="be720-176">Komentář, rok</span><span class="sxs-lookup"><span data-stu-id="be720-176">Comment, Year</span></span>|
||<span data-ttu-id="be720-177">Předpovídat podvodné transakce kreditní kartou</span><span class="sxs-lookup"><span data-stu-id="be720-177">Predict fraudulent credit card transactions</span></span>|[<span data-ttu-id="be720-178">Údaje o kreditní kartě</span><span class="sxs-lookup"><span data-stu-id="be720-178">credit card data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|<span data-ttu-id="be720-179">Třída (1 v případě podvodného, 0 jinak)</span><span class="sxs-lookup"><span data-stu-id="be720-179">Class (1 when fraudulent, 0 otherwise)</span></span>|<span data-ttu-id="be720-180">Částka, V1-V28 (anonymizované funkce)</span><span class="sxs-lookup"><span data-stu-id="be720-180">Amount, V1-V28 (anonymized features)</span></span>|
||<span data-ttu-id="be720-181">Předvídejte typ problému v úložišti GitHub</span><span class="sxs-lookup"><span data-stu-id="be720-181">Predict the type of issue in a GitHub repository</span></span>|[<span data-ttu-id="be720-182">Data problému GitHubu</span><span class="sxs-lookup"><span data-stu-id="be720-182">GitHub issue data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|<span data-ttu-id="be720-183">Oblast</span><span class="sxs-lookup"><span data-stu-id="be720-183">Area</span></span>|<span data-ttu-id="be720-184">Název, popis</span><span class="sxs-lookup"><span data-stu-id="be720-184">Title, Description</span></span>|
|<span data-ttu-id="be720-185">Predikce hodnoty</span><span class="sxs-lookup"><span data-stu-id="be720-185">Value prediction</span></span>|<span data-ttu-id="be720-186">Předpovědět cenu jízdného taxi</span><span class="sxs-lookup"><span data-stu-id="be720-186">Predict taxi fare price</span></span>|[<span data-ttu-id="be720-187">údaje o jízdném taxislužby</span><span class="sxs-lookup"><span data-stu-id="be720-187">taxi fare data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|<span data-ttu-id="be720-188">Jízdné</span><span class="sxs-lookup"><span data-stu-id="be720-188">Fare</span></span>|<span data-ttu-id="be720-189">Doba jízdy, vzdálenost</span><span class="sxs-lookup"><span data-stu-id="be720-189">Trip time, distance</span></span>|
|<span data-ttu-id="be720-190">Klasifikace obrázků</span><span class="sxs-lookup"><span data-stu-id="be720-190">Image classification</span></span>|<span data-ttu-id="be720-191">Předpovědět kategorii problému</span><span class="sxs-lookup"><span data-stu-id="be720-191">Predict the category of an issue</span></span>|[<span data-ttu-id="be720-192">obrázky květin</span><span class="sxs-lookup"><span data-stu-id="be720-192">flower images</span></span>](http://download.tensorflow.org/example_images/flower_photos.tgz)|<span data-ttu-id="be720-193">Typ květiny: sedmikráska, pampeliška, růže, slunečnice, tulipány</span><span class="sxs-lookup"><span data-stu-id="be720-193">The type of flower: daisy, dandelion, roses, sunflowers, tulips</span></span>|<span data-ttu-id="be720-194">Samotná obrazová data</span><span class="sxs-lookup"><span data-stu-id="be720-194">The image data itself</span></span>|
|<span data-ttu-id="be720-195">Doporučení</span><span class="sxs-lookup"><span data-stu-id="be720-195">Recommendation</span></span>|<span data-ttu-id="be720-196">Předvídejte filmy, které se někomu budou líbit</span><span class="sxs-lookup"><span data-stu-id="be720-196">Predict movies that someone will like</span></span>|[<span data-ttu-id="be720-197">hodnocení filmů</span><span class="sxs-lookup"><span data-stu-id="be720-197">movie ratings</span></span>](http://files.grouplens.org/datasets/movielens/ml-latest-small.zip)|<span data-ttu-id="be720-198">Uživatelé, Filmy</span><span class="sxs-lookup"><span data-stu-id="be720-198">Users, Movies</span></span>|<span data-ttu-id="be720-199">Ratings</span><span class="sxs-lookup"><span data-stu-id="be720-199">Ratings</span></span>|

## <a name="train"></a><span data-ttu-id="be720-200">Trénování</span><span class="sxs-lookup"><span data-stu-id="be720-200">Train</span></span>

<span data-ttu-id="be720-201">Jakmile vyberete scénář, data a popisek, Tvůrce modelů trénuje model.</span><span class="sxs-lookup"><span data-stu-id="be720-201">Once you select your scenario, data, and label, Model Builder trains the model.</span></span>

### <a name="what-is-training"></a><span data-ttu-id="be720-202">Co je trénink?</span><span class="sxs-lookup"><span data-stu-id="be720-202">What is training?</span></span>

<span data-ttu-id="be720-203">Školení je automatický proces, pomocí kterého Tvůrce modelů učí váš model, jak odpovídat na otázky pro váš scénář.</span><span class="sxs-lookup"><span data-stu-id="be720-203">Training is an automatic process by which Model Builder teaches your model how to answer questions for your scenario.</span></span> <span data-ttu-id="be720-204">Po tréninu, váš model můžete předpovědět se vstupními daty, které dosud neviděl.</span><span class="sxs-lookup"><span data-stu-id="be720-204">Once trained, your model can make predictions with input data that it has not seen before.</span></span> <span data-ttu-id="be720-205">Například, pokud jste předpovídají ceny domů a nový dům přichází na trh, můžete předpovědět jeho prodejní cenu.</span><span class="sxs-lookup"><span data-stu-id="be720-205">For example, if you are predicting house prices and a new house comes on the market, you can predict its sale price.</span></span>

<span data-ttu-id="be720-206">Vzhledem k tomu, že Model Builder používá automatizované strojové učení (AutoML), nevyžaduje žádný vstup nebo ladění od vás během školení.</span><span class="sxs-lookup"><span data-stu-id="be720-206">Because Model Builder uses automated machine learning (AutoML), it does not require any input or tuning from you during training.</span></span>

### <a name="how-long-should-i-train-for"></a><span data-ttu-id="be720-207">Na jak dlouho mám trénovat?</span><span class="sxs-lookup"><span data-stu-id="be720-207">How long should I train for?</span></span>

<span data-ttu-id="be720-208">Tvůrce modelů používá AutoML k prozkoumání více modelů a vyhledá vám nejvýkonnější model.</span><span class="sxs-lookup"><span data-stu-id="be720-208">Model Builder uses AutoML to explore multiple models to find you the best performing model.</span></span>

<span data-ttu-id="be720-209">Delší tréninkové období umožňují automatické kontrole prozkoumat další modely s širším rozsahem nastavení.</span><span class="sxs-lookup"><span data-stu-id="be720-209">Longer training periods allow AutoML to explore more models with a wider range of settings.</span></span>

<span data-ttu-id="be720-210">Níže uvedená tabulka shrnuje průměrnou dobu, kterou je třeba získat dobrý výkon pro sadu ukázkových datových sad v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="be720-210">The table below summarizes the average time taken to get good performance for a suite of example datasets, on a local machine.</span></span>

|<span data-ttu-id="be720-211">Velikost datové sady</span><span class="sxs-lookup"><span data-stu-id="be720-211">Dataset size</span></span>|<span data-ttu-id="be720-212">Průměrná doba tréninku</span><span class="sxs-lookup"><span data-stu-id="be720-212">Average time to train</span></span>|
|------------|---------------------|
|<span data-ttu-id="be720-213">0 - 10 MB</span><span class="sxs-lookup"><span data-stu-id="be720-213">0 - 10 MB</span></span>|<span data-ttu-id="be720-214">10 s</span><span class="sxs-lookup"><span data-stu-id="be720-214">10 sec</span></span>|
|<span data-ttu-id="be720-215">10 - 100 MB</span><span class="sxs-lookup"><span data-stu-id="be720-215">10 - 100 MB</span></span>|<span data-ttu-id="be720-216">10 min</span><span class="sxs-lookup"><span data-stu-id="be720-216">10 min</span></span>|
|<span data-ttu-id="be720-217">100 - 500 MB</span><span class="sxs-lookup"><span data-stu-id="be720-217">100 - 500 MB</span></span>|<span data-ttu-id="be720-218">30 min</span><span class="sxs-lookup"><span data-stu-id="be720-218">30 min</span></span>|
|<span data-ttu-id="be720-219">500 - 1 GB</span><span class="sxs-lookup"><span data-stu-id="be720-219">500 - 1 GB</span></span>|<span data-ttu-id="be720-220">60 min</span><span class="sxs-lookup"><span data-stu-id="be720-220">60 min</span></span>|
|<span data-ttu-id="be720-221">1 GB+</span><span class="sxs-lookup"><span data-stu-id="be720-221">1 GB+</span></span>|<span data-ttu-id="be720-222">3+ hodiny</span><span class="sxs-lookup"><span data-stu-id="be720-222">3+ hours</span></span>|

<span data-ttu-id="be720-223">Tato čísla jsou pouze vodítkem.</span><span class="sxs-lookup"><span data-stu-id="be720-223">These numbers are a guide only.</span></span> <span data-ttu-id="be720-224">Přesná délka tréninku závisí na:</span><span class="sxs-lookup"><span data-stu-id="be720-224">The exact length of training is dependent on:</span></span>

- <span data-ttu-id="be720-225">počet prvků (sloupců), které se používají jako vstup do modelu</span><span class="sxs-lookup"><span data-stu-id="be720-225">the number of features (columns) being used to as input to the model</span></span>
- <span data-ttu-id="be720-226">typ sloupců</span><span class="sxs-lookup"><span data-stu-id="be720-226">the type of columns</span></span>
- <span data-ttu-id="be720-227">úloha ML</span><span class="sxs-lookup"><span data-stu-id="be720-227">the ML task</span></span>
- <span data-ttu-id="be720-228">výkon procesoru, disku a paměti počítače používaného pro trénování</span><span class="sxs-lookup"><span data-stu-id="be720-228">the CPU, disk, and memory performance of the machine used for training</span></span>

## <a name="evaluate"></a><span data-ttu-id="be720-229">Vyhodnotit</span><span class="sxs-lookup"><span data-stu-id="be720-229">Evaluate</span></span>

<span data-ttu-id="be720-230">Hodnocení je proces měření toho, jak dobrý je váš model.</span><span class="sxs-lookup"><span data-stu-id="be720-230">Evaluation is the process of measuring how good your model is.</span></span> <span data-ttu-id="be720-231">Tvůrce modelů používá trénovaný model k předpovědi s nová testovací data a pak měří, jak dobré předpovědi jsou.</span><span class="sxs-lookup"><span data-stu-id="be720-231">Model Builder uses the trained model to make predictions with new test data, and then measures how good the predictions are.</span></span>

<span data-ttu-id="be720-232">Tvůrce modelů rozdělí trénovací data do trénovací sady a testovací sady.</span><span class="sxs-lookup"><span data-stu-id="be720-232">Model Builder splits the training data into a training set and a test set.</span></span> <span data-ttu-id="be720-233">Údaje o školení (80 %) se používá k trénování modelu a testovacích dat (20 %) je držen zpět k vyhodnocení modelu.</span><span class="sxs-lookup"><span data-stu-id="be720-233">The training data (80%) is used to train your model and the test data (20%) is held back to evaluate your model.</span></span>

### <a name="how-do-i-understand-my-model-performance"></a><span data-ttu-id="be720-234">Jak rozumím výkonu modelu?</span><span class="sxs-lookup"><span data-stu-id="be720-234">How do I understand my model performance?</span></span>

<span data-ttu-id="be720-235">Scénář se mapuje na úlohu strojového učení.</span><span class="sxs-lookup"><span data-stu-id="be720-235">A scenario maps to a machine learning task.</span></span> <span data-ttu-id="be720-236">Každý úkol ML má vlastní sadu metrik hodnocení.</span><span class="sxs-lookup"><span data-stu-id="be720-236">Each ML task has its own set of evaluation metrics.</span></span>

#### <a name="value-prediction"></a><span data-ttu-id="be720-237">Predikce hodnoty</span><span class="sxs-lookup"><span data-stu-id="be720-237">Value prediction</span></span>

<span data-ttu-id="be720-238">Výchozí metrika pro problémy s předpovědí hodnot je RSquared, hodnota RSquared rozsahy mezi 0 a 1.</span><span class="sxs-lookup"><span data-stu-id="be720-238">The default metric for value prediction problems is RSquared, the value of RSquared ranges between 0 and 1.</span></span> <span data-ttu-id="be720-239">1 je nejlepší možná hodnota, nebo jinými slovy, čím blíže hodnota RSquared na 1, tím lépe váš model je výkon.</span><span class="sxs-lookup"><span data-stu-id="be720-239">1 is the best possible value or in other words the closer the value of RSquared to 1 the better your model is performing.</span></span>

<span data-ttu-id="be720-240">Další metriky hlášené, jako je absolutní ztráta, kvasitová ztráta a ztráta RMS jsou další metriky, které lze použít k pochopení toho, jak si model vede, a jeho porovnání s jinými modely předpovědi hodnot.</span><span class="sxs-lookup"><span data-stu-id="be720-240">Other metrics reported such as absolute-loss, squared-loss, and RMS loss are additional metrics, which can be used to understand how your model is performing and comparing it against other value prediction models.</span></span>

#### <a name="classification-2-categories"></a><span data-ttu-id="be720-241">Klasifikace (2 kategorie)</span><span class="sxs-lookup"><span data-stu-id="be720-241">Classification (2 categories)</span></span>

<span data-ttu-id="be720-242">Výchozí metrika pro problémy s klasifikací je přesnost.</span><span class="sxs-lookup"><span data-stu-id="be720-242">The default metric for classification problems is accuracy.</span></span> <span data-ttu-id="be720-243">Přesnost definuje podíl správné předpovědi modelu je dělat přes testovací datové sady.</span><span class="sxs-lookup"><span data-stu-id="be720-243">Accuracy defines the proportion of correct predictions your model is making over the test dataset.</span></span> <span data-ttu-id="be720-244">Čím blíže k 100% nebo 1,0, tím lépe.</span><span class="sxs-lookup"><span data-stu-id="be720-244">The closer to 100% or 1.0 the better it is.</span></span>

<span data-ttu-id="be720-245">Další hlášené metriky, například AUC (Plocha pod křivkou), která měří skutečně pozitivní míru vs. míra falešně pozitivních hodnot by měla být vyšší než 0,50, aby byly modely přijatelné.</span><span class="sxs-lookup"><span data-stu-id="be720-245">Other metrics reported such as AUC (Area under the curve), which measures the true positive rate vs. the false positive rate should be greater than 0.50 for models to be acceptable.</span></span>

<span data-ttu-id="be720-246">Další metriky, jako je skóre F1, lze použít k řízení rovnováhy mezi přesností a odvoláním.</span><span class="sxs-lookup"><span data-stu-id="be720-246">Additional metrics like F1 score can be used to control the balance between Precision and Recall.</span></span>

#### <a name="classification-3-categories"></a><span data-ttu-id="be720-247">Klasifikace (3+ kategorie)</span><span class="sxs-lookup"><span data-stu-id="be720-247">Classification (3+ categories)</span></span>

<span data-ttu-id="be720-248">Výchozí metrika pro klasifikaci více tříd je Mikro přesnost.</span><span class="sxs-lookup"><span data-stu-id="be720-248">The default metric for Multi-class classification is Micro Accuracy.</span></span> <span data-ttu-id="be720-249">Čím blíže je mikropřesnost na 100% nebo 1,0, tím lepší je.</span><span class="sxs-lookup"><span data-stu-id="be720-249">The closer the Micro Accuracy to 100% or 1.0 the better it is.</span></span>

<span data-ttu-id="be720-250">Další důležitou metrikou pro klasifikaci více tříd je makropřesnost, podobná mikropřesnosti, čím blíže k 1.0, tím lépe.</span><span class="sxs-lookup"><span data-stu-id="be720-250">Another important metric for Multi-class classification is Macro-accuracy, similar to Micro-accuracy the closer to 1.0 the better it is.</span></span> <span data-ttu-id="be720-251">Dobrý způsob, jak přemýšlet o těchto dvou typech přesnosti je:</span><span class="sxs-lookup"><span data-stu-id="be720-251">A good way to think about these two types of accuracy is:</span></span>

- <span data-ttu-id="be720-252">Mikropřesnost: Jak často se příchozí jízdenka klasifikuje do správného týmu?</span><span class="sxs-lookup"><span data-stu-id="be720-252">Micro-accuracy: How often does an incoming ticket get classified to the right team?</span></span>
- <span data-ttu-id="be720-253">Makropřesnost: Jak často je pro průměrný tým příchozí lístek pro jejich tým správný?</span><span class="sxs-lookup"><span data-stu-id="be720-253">Macro-accuracy: For an average team, how often is an incoming ticket correct for their team?</span></span>

### <a name="more-information-on-evaluation-metrics"></a><span data-ttu-id="be720-254">Další informace o hodnotících metrikách</span><span class="sxs-lookup"><span data-stu-id="be720-254">More information on evaluation metrics</span></span>

<span data-ttu-id="be720-255">Další informace naleznete v tématu [metriky vyhodnocení modelu](resources/metrics.md).</span><span class="sxs-lookup"><span data-stu-id="be720-255">For more information, see [model evaluation metrics](resources/metrics.md).</span></span>

## <a name="improve"></a><span data-ttu-id="be720-256">Zlepšit</span><span class="sxs-lookup"><span data-stu-id="be720-256">Improve</span></span>

<span data-ttu-id="be720-257">Pokud skóre výkonu modelu není tak dobré, jak chcete, můžete:</span><span class="sxs-lookup"><span data-stu-id="be720-257">If your model performance score is not as good as you want it to be, you can:</span></span>

- <span data-ttu-id="be720-258">Trénujte delší dobu.</span><span class="sxs-lookup"><span data-stu-id="be720-258">Train for a longer period of time.</span></span> <span data-ttu-id="be720-259">S více času, automatizované strojové učení motor experimenty s více algoritmy a nastavení.</span><span class="sxs-lookup"><span data-stu-id="be720-259">With more time, the automated machine learning engine experiments with more algorithms and settings.</span></span>

- <span data-ttu-id="be720-260">Přidejte další data.</span><span class="sxs-lookup"><span data-stu-id="be720-260">Add more data.</span></span> <span data-ttu-id="be720-261">Někdy množství dat není dostatečná pro trénování vysoce kvalitní model strojového učení.</span><span class="sxs-lookup"><span data-stu-id="be720-261">Sometimes the amount of data is not sufficient to train a high-quality machine learning model.</span></span>

- <span data-ttu-id="be720-262">Vyvažte svá data.</span><span class="sxs-lookup"><span data-stu-id="be720-262">Balance your data.</span></span> <span data-ttu-id="be720-263">Pro úkoly klasifikace, ujistěte se, že sada školení je vyvážená mezi kategoriemi.</span><span class="sxs-lookup"><span data-stu-id="be720-263">For classification tasks, make sure that the training set is balanced across the categories.</span></span> <span data-ttu-id="be720-264">Například pokud máte čtyři třídy pro 100 příklady školení a dvě první třídy (tag1 a tag2) se používají pro 90 záznamů, ale další dva (tag3 a tag4) se používají pouze na zbývajících 10 záznamů, nedostatek vyvážených dat může způsobit, že váš model bojovat správně předpovědět tag3 nebo tag4.</span><span class="sxs-lookup"><span data-stu-id="be720-264">For example, if you have four classes for 100 training examples, and the two first classes (tag1 and tag2) are used for 90 records, but the other two (tag3 and tag4) are only used on the remaining 10 records, the lack of balanced data may cause your model to struggle to correctly predict tag3 or tag4.</span></span>

## <a name="code"></a><span data-ttu-id="be720-265">kód</span><span class="sxs-lookup"><span data-stu-id="be720-265">Code</span></span>

<span data-ttu-id="be720-266">Po fázi vyhodnocení Tvůrce modelů vydělá soubor modelu a kód, který můžete použít k přidání modelu do aplikace.</span><span class="sxs-lookup"><span data-stu-id="be720-266">After the evaluation phase, Model Builder outputs a model file, and code that you can use to add the model to your application.</span></span> <span data-ttu-id="be720-267">ML.NET modely jsou uloženy jako soubor zip.</span><span class="sxs-lookup"><span data-stu-id="be720-267">ML.NET models are saved as a zip file.</span></span> <span data-ttu-id="be720-268">Kód pro načtení a použití modelu je přidán jako nový projekt ve vašem řešení.</span><span class="sxs-lookup"><span data-stu-id="be720-268">The code to load and use your model is added as a new project in your solution.</span></span> <span data-ttu-id="be720-269">Tvůrce modelů také přidá ukázkovou konzolovou aplikaci, kterou můžete spustit, abyste viděli model v akci.</span><span class="sxs-lookup"><span data-stu-id="be720-269">Model Builder also adds a sample console app that you can run to see your model in action.</span></span>

<span data-ttu-id="be720-270">Kromě toho Tvůrce modelů vygeneruje kód, který vygeneroval model, takže můžete pochopit kroky použité ke generování modelu.</span><span class="sxs-lookup"><span data-stu-id="be720-270">In addition, Model Builder outputs the code that generated the model, so that you can understand the steps used to generate the model.</span></span> <span data-ttu-id="be720-271">Můžete také použít model trénovací kód pro přeškolit model s novými daty.</span><span class="sxs-lookup"><span data-stu-id="be720-271">You can also use the model training code to retrain your model with new data.</span></span>

## <a name="whats-next"></a><span data-ttu-id="be720-272">Co dále?</span><span class="sxs-lookup"><span data-stu-id="be720-272">What's next?</span></span>

<span data-ttu-id="be720-273">[Instalace](how-to-guides/install-model-builder.md) rozšíření Visual Studio tvůrce modelů</span><span class="sxs-lookup"><span data-stu-id="be720-273">[Install](how-to-guides/install-model-builder.md) the Model Builder Visual Studio extension</span></span>

<span data-ttu-id="be720-274">Vyzkoušejte [predikci ceny nebo jakýkoli regresní scénář](tutorials/predict-prices-with-model-builder.md)</span><span class="sxs-lookup"><span data-stu-id="be720-274">Try [price prediction or any regression scenario](tutorials/predict-prices-with-model-builder.md)</span></span>
