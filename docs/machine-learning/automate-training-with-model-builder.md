---
title: Co je tvůrce modelů a jak to funguje?
description: Postup pro automatické učení modelu Machine Learning pomocí Tvůrce modelů ML.NET
ms.date: 03/25/2020
ms.custom: overview, mlnet-tooling
ms.openlocfilehash: 4afdbfd1682a30647b09d05d51a5c73c214fe2bd
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616926"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a><span data-ttu-id="e2ab6-103">Co je tvůrce modelů a jak to funguje?</span><span class="sxs-lookup"><span data-stu-id="e2ab6-103">What is Model Builder and how does it work?</span></span>

<span data-ttu-id="e2ab6-104">ML.NET model Builder je intuitivní grafické rozšíření sady Visual Studio, které slouží k sestavování, výuce a nasazování vlastních modelů strojového učení.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-104">ML.NET Model Builder is an intuitive graphical Visual Studio extension to build, train, and deploy custom machine learning models.</span></span>

<span data-ttu-id="e2ab6-105">Tvůrce modelů pomocí automatizovaného strojového učení (AutoML) zkoumá různé algoritmy a nastavení strojového učení, které vám pomůžou najít ten, který nejlépe vyhovuje vašemu scénáři.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-105">Model Builder uses automated machine learning (AutoML) to explore different machine learning algorithms and settings to help you find the one that best suits your scenario.</span></span>

<span data-ttu-id="e2ab6-106">K používání tvůrce modelů nepotřebujete odborné znalosti strojového učení.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-106">You don't need machine learning expertise to use Model Builder.</span></span> <span data-ttu-id="e2ab6-107">Potřebujete jenom některá data a problém, který je potřeba vyřešit.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-107">All you need is some data, and a problem to solve.</span></span> <span data-ttu-id="e2ab6-108">Tvůrce modelů generuje kód pro přidání modelu do vaší aplikace .NET.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-108">Model Builder generates the code to add the model to your .NET application.</span></span>

![Animace uživatelského rozhraní rozšíření tvůrce modelů sady Visual Studio](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> <span data-ttu-id="e2ab6-110">Tvůrce modelů je aktuálně ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-110">Model Builder is currently in Preview.</span></span>

## <a name="scenario"></a><span data-ttu-id="e2ab6-111">Scénář</span><span class="sxs-lookup"><span data-stu-id="e2ab6-111">Scenario</span></span>

<span data-ttu-id="e2ab6-112">Můžete přenášet mnoho různých scénářů do Tvůrce modelů a vygenerovat pro svou aplikaci model strojového učení.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-112">You can bring many different scenarios to Model Builder, to generate a machine learning model for your application.</span></span>

<span data-ttu-id="e2ab6-113">Scénář je popis typu předpovědi, kterou chcete použít pro vaše data.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-113">A scenario is a description of the type of prediction you want to make using your data.</span></span> <span data-ttu-id="e2ab6-114">Například:</span><span class="sxs-lookup"><span data-stu-id="e2ab6-114">For example:</span></span>

- <span data-ttu-id="e2ab6-115">Předpověď budoucího objemu prodejů produktů na základě historických dat o prodeji</span><span class="sxs-lookup"><span data-stu-id="e2ab6-115">predict future product sales volume based on historical sales data</span></span>
- <span data-ttu-id="e2ab6-116">klasifikace zabarvení jako kladné nebo záporné na základě revizí zákazníků</span><span class="sxs-lookup"><span data-stu-id="e2ab6-116">classify sentiments as positive or negative based on customer reviews</span></span>
- <span data-ttu-id="e2ab6-117">zjištění, zda je bankovní transakce podvodný</span><span class="sxs-lookup"><span data-stu-id="e2ab6-117">detect whether a banking transaction is fraudulent</span></span>
- <span data-ttu-id="e2ab6-118">směrování problémů s názory zákazníků na správný tým ve vaší společnosti</span><span class="sxs-lookup"><span data-stu-id="e2ab6-118">route customer feedback issues to the correct team in your company</span></span>

### <a name="which-machine-learning-scenario-is-right-for-me"></a><span data-ttu-id="e2ab6-119">Který scénář strojového učení je pro mě nejvhodnější?</span><span class="sxs-lookup"><span data-stu-id="e2ab6-119">Which machine learning scenario is right for me?</span></span>

<span data-ttu-id="e2ab6-120">V Tvůrci modelů je nutné vybrat scénář.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-120">In Model Builder, you need to select a scenario.</span></span> <span data-ttu-id="e2ab6-121">Typ scénáře závisí na typu předpovědi, kterou se pokoušíte provést.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-121">The type of scenario depends on what type of prediction you are trying to make.</span></span>

#### <a name="text-classification"></a><span data-ttu-id="e2ab6-122">Klasifikace textu</span><span class="sxs-lookup"><span data-stu-id="e2ab6-122">Text classification</span></span>

<span data-ttu-id="e2ab6-123">Klasifikace se používá ke kategorizaci dat do kategorií.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-123">Classification is used to categorize data into categories.</span></span>

![Diagram znázorňující příklady binární klasifikace včetně zjišťování podvodů, zmírnění rizik a blokování aplikací](media/binary-classification-examples.png)

![Příklady klasifikace s více třídami včetně klasifikace dokumentů a produktů, směrování lístků podpory a stanovení priorit zákaznických problémů](media/multiclass-classification-examples.png)

#### <a name="value-prediction"></a><span data-ttu-id="e2ab6-126">Předpověď hodnoty</span><span class="sxs-lookup"><span data-stu-id="e2ab6-126">Value prediction</span></span>

<span data-ttu-id="e2ab6-127">Regrese se používá k předpovědi čísel.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-127">Regression is used to predict numbers.</span></span>

![Diagram znázorňující příklady regrese, jako je předpověď ceny, Prognóza prodeje a prediktivní údržba](media/regression-examples.png)

#### <a name="image-classification"></a><span data-ttu-id="e2ab6-129">Klasifikace obrázků</span><span class="sxs-lookup"><span data-stu-id="e2ab6-129">Image classification</span></span>

<span data-ttu-id="e2ab6-130">Klasifikaci obrázku lze použít k identifikaci obrázků různých kategorií.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-130">Image classification can be used to identify images of different categories.</span></span> <span data-ttu-id="e2ab6-131">Například různé typy terénu nebo zvířat nebo výrobní vady.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-131">For example, different types of terrain or animals or manufacturing defects.</span></span>

<span data-ttu-id="e2ab6-132">Můžete použít scénář klasifikace obrázku, pokud máte sadu imagí a chcete klasifikace imagí do různých kategorií.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-132">You can use the image classification scenario if you have a set of images, and you want to classify the images into different categories.</span></span>

#### <a name="recommendation"></a><span data-ttu-id="e2ab6-133">Doporučení</span><span class="sxs-lookup"><span data-stu-id="e2ab6-133">Recommendation</span></span>

<span data-ttu-id="e2ab6-134">Scénář doporučení předpovídá seznam navrhovaných položek pro konkrétního uživatele, a to na základě toho, jak se podobá a jako nelíbí jiným uživatelům.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-134">The recommendation scenario predicts a list of suggested items for a particular user, based on how similar their likes and dislikes are to other users'.</span></span>

<span data-ttu-id="e2ab6-135">Scénář doporučení můžete použít, pokud máte sadu uživatelů a sadu "produktů", například položky k nákupu, filmů, knihám nebo TELEVIZNÍm pořadům, spolu se sadou hodnocení těchto produktů pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-135">You can use the recommendation scenario when you have a set of users and a set of "products", such as items to purchase, movies, books, or TV shows, along with a set of users' "ratings" of those products.</span></span>

## <a name="environment"></a><span data-ttu-id="e2ab6-136">Prostředí</span><span class="sxs-lookup"><span data-stu-id="e2ab6-136">Environment</span></span>

<span data-ttu-id="e2ab6-137">Svůj model strojového učení můžete na svém počítači nebo v cloudu v Azure vyškolit místně.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-137">You can train your machine learning model locally on your machine or in the cloud on Azure.</span></span>

<span data-ttu-id="e2ab6-138">Při psaní v místním prostředí pracujete s omezeními prostředků počítače (CPU, paměť a disk).</span><span class="sxs-lookup"><span data-stu-id="e2ab6-138">When you train locally, you work within the constraints of your computer resources (CPU, memory, and disk).</span></span> <span data-ttu-id="e2ab6-139">Když vytváříte výuku v cloudu, můžete škálovat prostředky tak, aby splňovaly požadavky vašeho scénáře, zejména pro velké datové sady.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-139">When you train in the cloud, you can scale up your resources to meet the demands of your scenario, especially for large datasets.</span></span>

<span data-ttu-id="e2ab6-140">Místní školení je podporováno pro všechny scénáře.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-140">Local training is supported for all scenarios.</span></span>

<span data-ttu-id="e2ab6-141">Pro klasifikaci imagí se podporuje školení Azure.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-141">Azure training is supported for Image Classification.</span></span>

## <a name="data"></a><span data-ttu-id="e2ab6-142">Data</span><span class="sxs-lookup"><span data-stu-id="e2ab6-142">Data</span></span>

<span data-ttu-id="e2ab6-143">Jakmile vyberete svůj scénář, tvůrce modelů vás vyzve k zadání datové sady.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-143">Once you have chosen your scenario, Model Builder asks you to provide a dataset.</span></span> <span data-ttu-id="e2ab6-144">Data se používají ke školení, vyhodnocení a výběru nejlepšího modelu pro váš scénář.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-144">The data is used to train, evaluate, and choose the best model for your scenario.</span></span>

![Diagram znázorňující kroky tvůrce modelů](media/model-builder-steps.png)

<span data-ttu-id="e2ab6-146">Tvůrce modelů podporuje datové sady ve formátech. TSV,. csv,. txt a také ve formátu SQL Database.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-146">Model Builder supports datasets in .tsv, .csv, .txt formats, as well as SQL database format.</span></span> <span data-ttu-id="e2ab6-147">Pokud máte soubor. txt, sloupce by měly být oddělené pomocí `,` `;` nebo `/t` a soubor musí obsahovat řádek záhlaví.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-147">If you have a .txt file, columns should be separated with `,`, `;` or `/t` and the file must have a header row.</span></span>

<span data-ttu-id="e2ab6-148">Pokud je datová sada tvořena obrázky, podporované typy souborů jsou `.jpg` a `.png` .</span><span class="sxs-lookup"><span data-stu-id="e2ab6-148">If the dataset is made up of images, the supported file types are `.jpg` and `.png`.</span></span>

<span data-ttu-id="e2ab6-149">Další informace najdete v tématu [načtení dat o školení do Tvůrce modelů](how-to-guides/load-data-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="e2ab6-149">For more information, see [Load training data into Model Builder](how-to-guides/load-data-model-builder.md).</span></span>

### <a name="choose-the-output-to-predict-label"></a><span data-ttu-id="e2ab6-150">Vyberte výstup, který chcete předpovědět (popisek)</span><span class="sxs-lookup"><span data-stu-id="e2ab6-150">Choose the output to predict (label)</span></span>

<span data-ttu-id="e2ab6-151">Datová sada je tabulka řádků příkladů cvičení a sloupce atributů.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-151">A dataset is a table of rows of training examples, and columns of attributes.</span></span> <span data-ttu-id="e2ab6-152">Každý řádek má:</span><span class="sxs-lookup"><span data-stu-id="e2ab6-152">Each row has:</span></span>

- <span data-ttu-id="e2ab6-153">**popisek** (atribut, který chcete předpovědět)</span><span class="sxs-lookup"><span data-stu-id="e2ab6-153">a **label** (the attribute that you want to predict)</span></span>
- <span data-ttu-id="e2ab6-154">**funkce** (atributy, které se používají jako vstupy pro předpověď popisku).</span><span class="sxs-lookup"><span data-stu-id="e2ab6-154">**features** (attributes that are used as inputs to predict the label).</span></span>

<span data-ttu-id="e2ab6-155">Pro scénář předpovědi pro domácí ceny můžou tyto funkce:</span><span class="sxs-lookup"><span data-stu-id="e2ab6-155">For the house-price prediction scenario, the features could be:</span></span>

- <span data-ttu-id="e2ab6-156">čtvercové záběry domu</span><span class="sxs-lookup"><span data-stu-id="e2ab6-156">the square footage of the house</span></span>
- <span data-ttu-id="e2ab6-157">počet ložnicemi a bathrooms</span><span class="sxs-lookup"><span data-stu-id="e2ab6-157">the number of bedrooms and bathrooms</span></span>
- <span data-ttu-id="e2ab6-158">PSČ</span><span class="sxs-lookup"><span data-stu-id="e2ab6-158">the zip code</span></span>

<span data-ttu-id="e2ab6-159">Popisek je cena za cenu na pracovišti pro tento řádek hodnot čtvercového záběru, Bedroom a koupeln a PSČ.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-159">The label is the historical house price for that row of square footage, bedroom, and bathroom values and zip code.</span></span>

![Tabulka znázorňující řádky a sloupce údajů o cenách domu s funkcemi, které se skládají z poštovních místností – PSČ a popisek ceny](media/model-builder-data.png)

### <a name="example-datasets"></a><span data-ttu-id="e2ab6-161">Příklady datových sad</span><span class="sxs-lookup"><span data-stu-id="e2ab6-161">Example datasets</span></span>

<span data-ttu-id="e2ab6-162">Pokud ještě nemáte vlastní data, vyzkoušejte jednu z těchto datových sad:</span><span class="sxs-lookup"><span data-stu-id="e2ab6-162">If you don't have your own data yet, try out one of these datasets:</span></span>

|<span data-ttu-id="e2ab6-163">Scénář</span><span class="sxs-lookup"><span data-stu-id="e2ab6-163">Scenario</span></span>|<span data-ttu-id="e2ab6-164">Příklad</span><span class="sxs-lookup"><span data-stu-id="e2ab6-164">Example</span></span>|<span data-ttu-id="e2ab6-165">Data</span><span class="sxs-lookup"><span data-stu-id="e2ab6-165">Data</span></span>|<span data-ttu-id="e2ab6-166">Popisek</span><span class="sxs-lookup"><span data-stu-id="e2ab6-166">Label</span></span>|<span data-ttu-id="e2ab6-167">Funkce</span><span class="sxs-lookup"><span data-stu-id="e2ab6-167">Features</span></span>|
|-|-|-|-|-|
|<span data-ttu-id="e2ab6-168">Classification</span><span class="sxs-lookup"><span data-stu-id="e2ab6-168">Classification</span></span>|<span data-ttu-id="e2ab6-169">Předpověď anomálií prodeje</span><span class="sxs-lookup"><span data-stu-id="e2ab6-169">Predict sales anomalies</span></span>|[<span data-ttu-id="e2ab6-170">prodejní data produktu</span><span class="sxs-lookup"><span data-stu-id="e2ab6-170">product sales data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|<span data-ttu-id="e2ab6-171">Prodej produktu</span><span class="sxs-lookup"><span data-stu-id="e2ab6-171">Product Sales</span></span>|<span data-ttu-id="e2ab6-172">Month</span><span class="sxs-lookup"><span data-stu-id="e2ab6-172">Month</span></span>|
||<span data-ttu-id="e2ab6-173">Předpověď mínění komentářů k webu</span><span class="sxs-lookup"><span data-stu-id="e2ab6-173">Predict sentiment of website comments</span></span>|[<span data-ttu-id="e2ab6-174">data komentáře webu</span><span class="sxs-lookup"><span data-stu-id="e2ab6-174">website comment data</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|<span data-ttu-id="e2ab6-175">Popisek (0, pokud je negativní mínění, 1 Při kladném)</span><span class="sxs-lookup"><span data-stu-id="e2ab6-175">Label (0 when negative sentiment, 1 when positive)</span></span>|<span data-ttu-id="e2ab6-176">Komentář, rok</span><span class="sxs-lookup"><span data-stu-id="e2ab6-176">Comment, Year</span></span>|
||<span data-ttu-id="e2ab6-177">Předpověď falešných transakcí platebních karet</span><span class="sxs-lookup"><span data-stu-id="e2ab6-177">Predict fraudulent credit card transactions</span></span>|[<span data-ttu-id="e2ab6-178">data platebních karet</span><span class="sxs-lookup"><span data-stu-id="e2ab6-178">credit card data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|<span data-ttu-id="e2ab6-179">Třída (1, pokud je podvodný, 0 jinak)</span><span class="sxs-lookup"><span data-stu-id="e2ab6-179">Class (1 when fraudulent, 0 otherwise)</span></span>|<span data-ttu-id="e2ab6-180">Množství, V1-v28 (funkce Anonyme)</span><span class="sxs-lookup"><span data-stu-id="e2ab6-180">Amount, V1-V28 (anonymized features)</span></span>|
||<span data-ttu-id="e2ab6-181">Předpověď typu problému v úložišti GitHubu</span><span class="sxs-lookup"><span data-stu-id="e2ab6-181">Predict the type of issue in a GitHub repository</span></span>|[<span data-ttu-id="e2ab6-182">Data o problému na GitHubu</span><span class="sxs-lookup"><span data-stu-id="e2ab6-182">GitHub issue data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|<span data-ttu-id="e2ab6-183">Oblast</span><span class="sxs-lookup"><span data-stu-id="e2ab6-183">Area</span></span>|<span data-ttu-id="e2ab6-184">Název, popis</span><span class="sxs-lookup"><span data-stu-id="e2ab6-184">Title, Description</span></span>|
|<span data-ttu-id="e2ab6-185">Předpověď hodnoty</span><span class="sxs-lookup"><span data-stu-id="e2ab6-185">Value prediction</span></span>|<span data-ttu-id="e2ab6-186">Předpověď ceny za taxislužby jízdné</span><span class="sxs-lookup"><span data-stu-id="e2ab6-186">Predict taxi fare price</span></span>|[<span data-ttu-id="e2ab6-187">data taxislužby tarifů</span><span class="sxs-lookup"><span data-stu-id="e2ab6-187">taxi fare data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|<span data-ttu-id="e2ab6-188">Vozov</span><span class="sxs-lookup"><span data-stu-id="e2ab6-188">Fare</span></span>|<span data-ttu-id="e2ab6-189">Doba odezvy, vzdálenost</span><span class="sxs-lookup"><span data-stu-id="e2ab6-189">Trip time, distance</span></span>|
|<span data-ttu-id="e2ab6-190">Klasifikace obrázků</span><span class="sxs-lookup"><span data-stu-id="e2ab6-190">Image classification</span></span>|<span data-ttu-id="e2ab6-191">Předpověď kategorie květu</span><span class="sxs-lookup"><span data-stu-id="e2ab6-191">Predict the category of a flower</span></span> |[<span data-ttu-id="e2ab6-192">obrázky květin</span><span class="sxs-lookup"><span data-stu-id="e2ab6-192">flower images</span></span>](http://download.tensorflow.org/example_images/flower_photos.tgz)|<span data-ttu-id="e2ab6-193">Typ květu: uzavřené, Dandelion, růže, slunečnice, Tulips</span><span class="sxs-lookup"><span data-stu-id="e2ab6-193">The type of flower: daisy, dandelion, roses, sunflowers, tulips</span></span>|<span data-ttu-id="e2ab6-194">Samotná data obrázku</span><span class="sxs-lookup"><span data-stu-id="e2ab6-194">The image data itself</span></span>|
|<span data-ttu-id="e2ab6-195">Doporučení</span><span class="sxs-lookup"><span data-stu-id="e2ab6-195">Recommendation</span></span>|<span data-ttu-id="e2ab6-196">Předpověď filmů, které někdo bude chtít</span><span class="sxs-lookup"><span data-stu-id="e2ab6-196">Predict movies that someone will like</span></span>|[<span data-ttu-id="e2ab6-197">Hodnocení filmů</span><span class="sxs-lookup"><span data-stu-id="e2ab6-197">movie ratings</span></span>](http://files.grouplens.org/datasets/movielens/ml-latest-small.zip)|<span data-ttu-id="e2ab6-198">Uživatelé, filmy</span><span class="sxs-lookup"><span data-stu-id="e2ab6-198">Users, Movies</span></span>|<span data-ttu-id="e2ab6-199">Ratings</span><span class="sxs-lookup"><span data-stu-id="e2ab6-199">Ratings</span></span>|

## <a name="train"></a><span data-ttu-id="e2ab6-200">Trénování</span><span class="sxs-lookup"><span data-stu-id="e2ab6-200">Train</span></span>

<span data-ttu-id="e2ab6-201">Když vyberete svůj scénář, data a popisek, tvůrce modelů navlakuje model.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-201">Once you select your scenario, data, and label, Model Builder trains the model.</span></span>

### <a name="what-is-training"></a><span data-ttu-id="e2ab6-202">Co je školení?</span><span class="sxs-lookup"><span data-stu-id="e2ab6-202">What is training?</span></span>

<span data-ttu-id="e2ab6-203">Školení je automatický proces, podle kterého tvůrce modelů učí váš model, jak odpovídat na otázky pro váš scénář.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-203">Training is an automatic process by which Model Builder teaches your model how to answer questions for your scenario.</span></span> <span data-ttu-id="e2ab6-204">Po vyškolení může váš model předpovědi se vstupními daty, ke kterým se předtím neviděl.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-204">Once trained, your model can make predictions with input data that it has not seen before.</span></span> <span data-ttu-id="e2ab6-205">Pokud například předpovídáte ceny za dům a na trhu se nachází nová dům, můžete předpovědět její prodejní cenu.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-205">For example, if you are predicting house prices and a new house comes on the market, you can predict its sale price.</span></span>

<span data-ttu-id="e2ab6-206">Vzhledem k tomu, že tvůrce modelů používá automatizované Machine Learning (AutoML), nevyžaduje během školení žádné vstupy nebo ladění.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-206">Because Model Builder uses automated machine learning (AutoML), it does not require any input or tuning from you during training.</span></span>

### <a name="how-long-should-i-train-for"></a><span data-ttu-id="e2ab6-207">Jak dlouho mám zaškolit?</span><span class="sxs-lookup"><span data-stu-id="e2ab6-207">How long should I train for?</span></span>

<span data-ttu-id="e2ab6-208">Tvůrce modelů používá AutoML k prozkoumání více modelů, abyste si našli nejlepší výkon modelu.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-208">Model Builder uses AutoML to explore multiple models to find you the best performing model.</span></span>

<span data-ttu-id="e2ab6-209">Delší školicí období umožňují AutoML prozkoumat více modelů s širší škálou nastavení.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-209">Longer training periods allow AutoML to explore more models with a wider range of settings.</span></span>

<span data-ttu-id="e2ab6-210">V následující tabulce najdete průměrnou dobu, jakou trvalo dosažení dobrého výkonu sady ukázkových datových sad na místním počítači.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-210">The table below summarizes the average time taken to get good performance for a suite of example datasets, on a local machine.</span></span>

|<span data-ttu-id="e2ab6-211">Velikost datové sady</span><span class="sxs-lookup"><span data-stu-id="e2ab6-211">Dataset size</span></span>|<span data-ttu-id="e2ab6-212">Průměrná doba pro vlak</span><span class="sxs-lookup"><span data-stu-id="e2ab6-212">Average time to train</span></span>|
|------------|---------------------|
|<span data-ttu-id="e2ab6-213">0-10 MB</span><span class="sxs-lookup"><span data-stu-id="e2ab6-213">0 - 10 MB</span></span>|<span data-ttu-id="e2ab6-214">10 sekund</span><span class="sxs-lookup"><span data-stu-id="e2ab6-214">10 sec</span></span>|
|<span data-ttu-id="e2ab6-215">10-100 MB</span><span class="sxs-lookup"><span data-stu-id="e2ab6-215">10 - 100 MB</span></span>|<span data-ttu-id="e2ab6-216">10 min</span><span class="sxs-lookup"><span data-stu-id="e2ab6-216">10 min</span></span>|
|<span data-ttu-id="e2ab6-217">100 – 500 MB</span><span class="sxs-lookup"><span data-stu-id="e2ab6-217">100 - 500 MB</span></span>|<span data-ttu-id="e2ab6-218">30 min</span><span class="sxs-lookup"><span data-stu-id="e2ab6-218">30 min</span></span>|
|<span data-ttu-id="e2ab6-219">500 – 1 GB</span><span class="sxs-lookup"><span data-stu-id="e2ab6-219">500 - 1 GB</span></span>|<span data-ttu-id="e2ab6-220">60 min.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-220">60 min</span></span>|
|<span data-ttu-id="e2ab6-221">1 GB +</span><span class="sxs-lookup"><span data-stu-id="e2ab6-221">1 GB+</span></span>|<span data-ttu-id="e2ab6-222">3 hodiny</span><span class="sxs-lookup"><span data-stu-id="e2ab6-222">3+ hours</span></span>|

<span data-ttu-id="e2ab6-223">Tato čísla jsou jenom orientační.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-223">These numbers are a guide only.</span></span> <span data-ttu-id="e2ab6-224">Přesná délka školení závisí na:</span><span class="sxs-lookup"><span data-stu-id="e2ab6-224">The exact length of training is dependent on:</span></span>

- <span data-ttu-id="e2ab6-225">počet funkcí (sloupců), které se používají jako vstup do modelu</span><span class="sxs-lookup"><span data-stu-id="e2ab6-225">the number of features (columns) being used to as input to the model</span></span>
- <span data-ttu-id="e2ab6-226">typ sloupců</span><span class="sxs-lookup"><span data-stu-id="e2ab6-226">the type of columns</span></span>
- <span data-ttu-id="e2ab6-227">úkol ML</span><span class="sxs-lookup"><span data-stu-id="e2ab6-227">the ML task</span></span>
- <span data-ttu-id="e2ab6-228">výkon procesoru, disku a paměti počítače, který se používá pro školení</span><span class="sxs-lookup"><span data-stu-id="e2ab6-228">the CPU, disk, and memory performance of the machine used for training</span></span>

## <a name="evaluate"></a><span data-ttu-id="e2ab6-229">Vyhodnotit</span><span class="sxs-lookup"><span data-stu-id="e2ab6-229">Evaluate</span></span>

<span data-ttu-id="e2ab6-230">Vyhodnocení je proces měření, jak dobrý je váš model.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-230">Evaluation is the process of measuring how good your model is.</span></span> <span data-ttu-id="e2ab6-231">Tvůrce modelů používá trained model k vytváření předpovědi s novými testovacími daty a pak měří, jak dobrá předpovědi.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-231">Model Builder uses the trained model to make predictions with new test data, and then measures how good the predictions are.</span></span>

<span data-ttu-id="e2ab6-232">Tvůrce modelů rozdělí školicí data do sady školení a sady testů.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-232">Model Builder splits the training data into a training set and a test set.</span></span> <span data-ttu-id="e2ab6-233">Školicí data (80%) se používá ke školení vašeho modelu a testovacích dat (20%) se vrátí k vyhodnocení vašeho modelu.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-233">The training data (80%) is used to train your model and the test data (20%) is held back to evaluate your model.</span></span>

### <a name="how-do-i-understand-my-model-performance"></a><span data-ttu-id="e2ab6-234">Návody porozumět výkonu mého modelu?</span><span class="sxs-lookup"><span data-stu-id="e2ab6-234">How do I understand my model performance?</span></span>

<span data-ttu-id="e2ab6-235">Scénář se mapuje na úlohu strojového učení.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-235">A scenario maps to a machine learning task.</span></span> <span data-ttu-id="e2ab6-236">Každá úloha ML má svou vlastní sadu metrik vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-236">Each ML task has its own set of evaluation metrics.</span></span>

#### <a name="value-prediction"></a><span data-ttu-id="e2ab6-237">Předpověď hodnoty</span><span class="sxs-lookup"><span data-stu-id="e2ab6-237">Value prediction</span></span>

<span data-ttu-id="e2ab6-238">Výchozí metrika pro problémy předpovědi hodnot je RSquared, hodnota RSquared rozsahů mezi 0 a 1.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-238">The default metric for value prediction problems is RSquared, the value of RSquared ranges between 0 and 1.</span></span> <span data-ttu-id="e2ab6-239">hodnota 1 je nejlepší možnou hodnotou nebo jinými slovy, které přiblíží hodnotu RSquared na 1, lepší váš model.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-239">1 is the best possible value or in other words the closer the value of RSquared to 1 the better your model is performing.</span></span>

<span data-ttu-id="e2ab6-240">Další metriky nahlášené jako absolutní ztráta, čtvercová ztráta a ztráta služby RMS jsou další metriky, které lze použít k pochopení toho, jak model probíhá, a jeho porovnání s jinými modely předpovědi hodnot.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-240">Other metrics reported such as absolute-loss, squared-loss, and RMS loss are additional metrics, which can be used to understand how your model is performing and comparing it against other value prediction models.</span></span>

#### <a name="classification-2-categories"></a><span data-ttu-id="e2ab6-241">Klasifikace (2 kategorie)</span><span class="sxs-lookup"><span data-stu-id="e2ab6-241">Classification (2 categories)</span></span>

<span data-ttu-id="e2ab6-242">Výchozí metrika pro problémy s klasifikací je přesnost.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-242">The default metric for classification problems is accuracy.</span></span> <span data-ttu-id="e2ab6-243">Přesnost definuje poměr správných předpovědi, které model provádí přes testovací datovou sadu.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-243">Accuracy defines the proportion of correct predictions your model is making over the test dataset.</span></span> <span data-ttu-id="e2ab6-244">Nejblíže k 100% nebo 1,0 tím lépe.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-244">The closer to 100% or 1.0 the better it is.</span></span>

<span data-ttu-id="e2ab6-245">Jiné metriky nahlášené jako AUC (oblast pod křivkou), které měří skutečnou kladnou rychlost vs. falešně pozitivní sazba by měla být větší než 0,50, aby bylo možné modely akceptovat.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-245">Other metrics reported such as AUC (Area under the curve), which measures the true positive rate vs. the false positive rate should be greater than 0.50 for models to be acceptable.</span></span>

<span data-ttu-id="e2ab6-246">K řízení rovnováhy mezi přesností a odvoláním je možné použít další metriky, jako je například skóre F1.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-246">Additional metrics like F1 score can be used to control the balance between Precision and Recall.</span></span>

#### <a name="classification-3-categories"></a><span data-ttu-id="e2ab6-247">Klasifikace (3 + kategorie)</span><span class="sxs-lookup"><span data-stu-id="e2ab6-247">Classification (3+ categories)</span></span>

<span data-ttu-id="e2ab6-248">Výchozí metrika pro klasifikaci více tříd je mikropřesnost.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-248">The default metric for Multi-class classification is Micro Accuracy.</span></span> <span data-ttu-id="e2ab6-249">Hodnota bližší pro mikropřesnost na 100% nebo 1,0 je lepší.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-249">The closer the Micro Accuracy to 100% or 1.0 the better it is.</span></span>

<span data-ttu-id="e2ab6-250">Další důležitou metrikou pro klasifikaci více tříd je přesnost na makro, podobně jako u mikropřesnosti blíž k 1,0. lepší je.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-250">Another important metric for Multi-class classification is Macro-accuracy, similar to Micro-accuracy the closer to 1.0 the better it is.</span></span> <span data-ttu-id="e2ab6-251">Dobrým způsobem, jak se domnívat o těchto dvou typech přesnosti, je:</span><span class="sxs-lookup"><span data-stu-id="e2ab6-251">A good way to think about these two types of accuracy is:</span></span>

- <span data-ttu-id="e2ab6-252">Mikropřesnost: jak často se příchozí lístek klasifikuje do správného týmu?</span><span class="sxs-lookup"><span data-stu-id="e2ab6-252">Micro-accuracy: How often does an incoming ticket get classified to the right team?</span></span>
- <span data-ttu-id="e2ab6-253">Přesnost maker: u průměrných týmů, jak často je příchozí lístek správný pro svůj tým?</span><span class="sxs-lookup"><span data-stu-id="e2ab6-253">Macro-accuracy: For an average team, how often is an incoming ticket correct for their team?</span></span>

### <a name="more-information-on-evaluation-metrics"></a><span data-ttu-id="e2ab6-254">Další informace o metrikách vyhodnocení</span><span class="sxs-lookup"><span data-stu-id="e2ab6-254">More information on evaluation metrics</span></span>

<span data-ttu-id="e2ab6-255">Další informace najdete v tématu [metriky vyhodnocení modelu](resources/metrics.md).</span><span class="sxs-lookup"><span data-stu-id="e2ab6-255">For more information, see [model evaluation metrics](resources/metrics.md).</span></span>

## <a name="improve"></a><span data-ttu-id="e2ab6-256">Účely</span><span class="sxs-lookup"><span data-stu-id="e2ab6-256">Improve</span></span>

<span data-ttu-id="e2ab6-257">Pokud vaše skóre výkonu vašeho modelu není tak dobré, jak chcete, můžete:</span><span class="sxs-lookup"><span data-stu-id="e2ab6-257">If your model performance score is not as good as you want it to be, you can:</span></span>

- <span data-ttu-id="e2ab6-258">Naučit se delší dobu.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-258">Train for a longer period of time.</span></span> <span data-ttu-id="e2ab6-259">Pomocí automatizovaného strojového strojového učení s větším využitím algoritmů a nastavení se s víc časem experimentuje.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-259">With more time, the automated machine learning engine experiments with more algorithms and settings.</span></span>

- <span data-ttu-id="e2ab6-260">Přidejte další data.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-260">Add more data.</span></span> <span data-ttu-id="e2ab6-261">V některých případech se množství dat nestačí pro výuku vysoce kvalitního modelu strojového učení.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-261">Sometimes the amount of data is not sufficient to train a high-quality machine learning model.</span></span>

- <span data-ttu-id="e2ab6-262">Vyvážení dat</span><span class="sxs-lookup"><span data-stu-id="e2ab6-262">Balance your data.</span></span> <span data-ttu-id="e2ab6-263">Pro úlohy klasifikace se ujistěte, že je sada školení vyrovnávána napříč kategoriemi.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-263">For classification tasks, make sure that the training set is balanced across the categories.</span></span> <span data-ttu-id="e2ab6-264">Například pokud máte čtyři třídy pro 100 příkladů a dvě první třídy (značky 1 a značka2) se používají pro 90 záznamů, ale ostatní dvě (značka3 a tag4) se používají jenom u zbývajících 10 záznamů, nedostatek vyvážených dat může způsobit, že váš model bude bojovat správně předpovědět značka3 nebo tag4.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-264">For example, if you have four classes for 100 training examples, and the two first classes (tag1 and tag2) are used for 90 records, but the other two (tag3 and tag4) are only used on the remaining 10 records, the lack of balanced data may cause your model to struggle to correctly predict tag3 or tag4.</span></span>

## <a name="code"></a><span data-ttu-id="e2ab6-265">Kód</span><span class="sxs-lookup"><span data-stu-id="e2ab6-265">Code</span></span>

<span data-ttu-id="e2ab6-266">Po fázi vyhodnocení výstup tvůrce modelů vytvoří soubor modelu a kód, který můžete použít k přidání modelu do aplikace.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-266">After the evaluation phase, Model Builder outputs a model file, and code that you can use to add the model to your application.</span></span> <span data-ttu-id="e2ab6-267">Modely ML.NET se ukládají jako soubor zip.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-267">ML.NET models are saved as a zip file.</span></span> <span data-ttu-id="e2ab6-268">Kód pro načtení a použití modelu je přidán jako nový projekt ve vašem řešení.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-268">The code to load and use your model is added as a new project in your solution.</span></span> <span data-ttu-id="e2ab6-269">Tvůrce modelů také přidá ukázkovou konzolovou aplikaci, kterou můžete spustit pro zobrazení modelu v akci.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-269">Model Builder also adds a sample console app that you can run to see your model in action.</span></span>

<span data-ttu-id="e2ab6-270">Kromě toho tvůrce modelů vypíše kód, který model vygeneroval, takže můžete pochopit postup, který se používá ke generování modelu.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-270">In addition, Model Builder outputs the code that generated the model, so that you can understand the steps used to generate the model.</span></span> <span data-ttu-id="e2ab6-271">Můžete také použít kód školení modelu k revýuce modelu s novými daty.</span><span class="sxs-lookup"><span data-stu-id="e2ab6-271">You can also use the model training code to retrain your model with new data.</span></span>

## <a name="whats-next"></a><span data-ttu-id="e2ab6-272">Co dále?</span><span class="sxs-lookup"><span data-stu-id="e2ab6-272">What's next?</span></span>

<span data-ttu-id="e2ab6-273">[Instalace](how-to-guides/install-model-builder.md) rozšíření pro tvůrce modelů sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e2ab6-273">[Install](how-to-guides/install-model-builder.md) the Model Builder Visual Studio extension</span></span>

<span data-ttu-id="e2ab6-274">Vyzkoušejte [cenový odhad nebo jakýkoli scénář regrese](tutorials/predict-prices-with-model-builder.md) .</span><span class="sxs-lookup"><span data-stu-id="e2ab6-274">Try [price prediction or any regression scenario](tutorials/predict-prices-with-model-builder.md)</span></span>
