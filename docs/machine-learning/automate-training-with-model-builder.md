---
title: Co je tvůrce modelů a jak to funguje?
description: Postup pro automatické učení modelu Machine Learning pomocí Tvůrce modelů ML.NET
author: natke
ms.date: 08/07/2019
ms.custom: overview
ms.openlocfilehash: 77fe56dba3532617ad9fb0c89bfaac7c8e031ce7
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971528"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a><span data-ttu-id="1c8ec-103">Co je tvůrce modelů a jak to funguje?</span><span class="sxs-lookup"><span data-stu-id="1c8ec-103">What is Model Builder and how does it work?</span></span>

<span data-ttu-id="1c8ec-104">ML.NET model Builder je intuitivní grafické rozšíření sady Visual Studio, které slouží k sestavování, výuce a nasazování vlastních modelů strojového učení.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-104">ML.NET Model Builder is an intuitive graphical Visual Studio extension to build, train, and deploy custom machine learning models.</span></span>

<span data-ttu-id="1c8ec-105">Tvůrce modelů pomocí automatizovaného strojového učení (AutoML) zkoumá různé algoritmy a nastavení strojového učení, které vám pomůžou najít ten, který nejlépe vyhovuje vašemu scénáři.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-105">Model Builder uses automated machine learning (AutoML) to explore different machine learning algorithms and settings to help you find the one that best suits your scenario.</span></span>

<span data-ttu-id="1c8ec-106">K používání tvůrce modelů nepotřebujete odborné znalosti strojového učení.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-106">You don't need machine learning expertise to use Model Builder.</span></span> <span data-ttu-id="1c8ec-107">Potřebujete jenom některá data a problém, který je potřeba vyřešit.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-107">All you need is some data, and a problem to solve.</span></span> <span data-ttu-id="1c8ec-108">Tvůrce modelů generuje kód pro přidání modelu do vaší aplikace .NET.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-108">Model Builder generates the code to add the model to your .NET application.</span></span>

![Animace uživatelského rozhraní rozšíření tvůrce modelů sady Visual Studio](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> <span data-ttu-id="1c8ec-110">Tvůrce modelů je aktuálně ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-110">Model Builder is currently in Preview.</span></span>

## <a name="scenarios"></a><span data-ttu-id="1c8ec-111">Scénáře</span><span class="sxs-lookup"><span data-stu-id="1c8ec-111">Scenarios</span></span>

<span data-ttu-id="1c8ec-112">Můžete přenášet mnoho různých scénářů do Tvůrce modelů a vygenerovat pro svou aplikaci model strojového učení.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-112">You can bring many different scenarios to Model Builder, to generate a machine learning model for your application.</span></span>

<span data-ttu-id="1c8ec-113">Scénář je popis typu předpovědi, kterou chcete použít pro vaše data.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-113">A scenario is a description of the type of prediction you want to make using your data.</span></span> <span data-ttu-id="1c8ec-114">Příklad:</span><span class="sxs-lookup"><span data-stu-id="1c8ec-114">For example:</span></span>

- <span data-ttu-id="1c8ec-115">Předpověď budoucího objemu prodejů produktů na základě historických dat o prodeji</span><span class="sxs-lookup"><span data-stu-id="1c8ec-115">predict future product sales volume based on historical sales data</span></span>
- <span data-ttu-id="1c8ec-116">klasifikace zabarvení jako kladné nebo záporné na základě revizí zákazníků</span><span class="sxs-lookup"><span data-stu-id="1c8ec-116">classify sentiments as positive or negative based on customer reviews</span></span>
- <span data-ttu-id="1c8ec-117">zjištění, zda je bankovní transakce podvodný</span><span class="sxs-lookup"><span data-stu-id="1c8ec-117">detect whether a banking transaction is fraudulent</span></span>
- <span data-ttu-id="1c8ec-118">směrování problémů s názory zákazníků na správný tým ve vaší společnosti</span><span class="sxs-lookup"><span data-stu-id="1c8ec-118">route customer feedback issues to the correct team in your company</span></span>

## <a name="choose-a-model-type"></a><span data-ttu-id="1c8ec-119">Zvolit typ modelu</span><span class="sxs-lookup"><span data-stu-id="1c8ec-119">Choose a model type</span></span>

<span data-ttu-id="1c8ec-120">V Tvůrci modelů musíte vybrat typ modelu Machine Learning.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-120">In Model Builder, you need to select a machine learning model type.</span></span> <span data-ttu-id="1c8ec-121">Typ modelu závisí na tom, co se chystáte provést.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-121">The type of model depends on what sort of prediction you are trying to make.</span></span>

<span data-ttu-id="1c8ec-122">Pro scénáře, které předpovídá číslo, se typ modelu Machine Learning nazývá `regression`.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-122">For scenarios that predict a number, the machine learning model type is called `regression`.</span></span>

<span data-ttu-id="1c8ec-123">Pro scénáře, které předpovídá kategorii, je typ modelu `classification`.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-123">For scenarios that predict a category, the model type is `classification`.</span></span> <span data-ttu-id="1c8ec-124">Existují dva typy klasifikace:</span><span class="sxs-lookup"><span data-stu-id="1c8ec-124">There are two types of classification:</span></span>

- <span data-ttu-id="1c8ec-125">v případě, že existuje pouze 2 kategorie: `binary classification`.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-125">where there are only 2 categories: `binary classification`.</span></span>
- <span data-ttu-id="1c8ec-126">kde jsou tři nebo více kategorií: `multiclass classification`.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-126">where there are three or more categories: `multiclass classification`.</span></span>

### <a name="which-model-type-is-right-for-me"></a><span data-ttu-id="1c8ec-127">Který typ modelu je pro mě nejvhodnější?</span><span class="sxs-lookup"><span data-stu-id="1c8ec-127">Which model type is right for me?</span></span>

#### <a name="predict-a-category-when-there-are-only-two-categories"></a><span data-ttu-id="1c8ec-128">Předpověď kategorie (pokud jsou k dispozici pouze dvě kategorie)</span><span class="sxs-lookup"><span data-stu-id="1c8ec-128">Predict a category (when there are only two categories)</span></span>

<span data-ttu-id="1c8ec-129">Binární klasifikace se používá ke kategorizaci dat do dvou kategorií (ano/ne; úspěch/chyba; pravda/nepravda; kladné nebo záporné).</span><span class="sxs-lookup"><span data-stu-id="1c8ec-129">Binary classification is used to categorize data into two categories (yes/no; pass/fail; true/false; positive/negative).</span></span>

![Diagram znázorňující příklady binární klasifikace včetně zjišťování podvodů, zmírnění rizik a blokování aplikací](media/binary-classification-examples.png)

<span data-ttu-id="1c8ec-131">Analýza mínění se dá použít k předpovědi kladné nebo záporné míněníí zpětné vazby od zákazníků.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-131">Sentiment analysis can be used to predict positive or negative sentiment of customer feedback.</span></span> <span data-ttu-id="1c8ec-132">Je příkladem binárního typu modelu klasifikace.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-132">It is an example of a binary classification model type.</span></span>

<span data-ttu-id="1c8ec-133">Pokud váš scénář vyžaduje klasifikaci ve dvou kategoriích, můžete použít tuto šablonu s vlastní datovou sadou.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-133">If your scenario requires classification into two categories, you can use this template with your own dataset.</span></span>

#### <a name="predict-a-category-when-there-are-three-or-more-categories"></a><span data-ttu-id="1c8ec-134">Předpověď kategorie (pokud existují tři nebo více kategorií)</span><span class="sxs-lookup"><span data-stu-id="1c8ec-134">Predict a category (when there are three or more categories)</span></span>

<span data-ttu-id="1c8ec-135">Pro kategorizaci dat do tří nebo více tříd lze použít klasifikaci s více třídami.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-135">Multiclass classification can be used to categorize data into three or more classes.</span></span>

![Příklady klasifikace s více třídami včetně klasifikace dokumentů a produktů, směrování lístků podpory a stanovení priorit zákaznických problémů](media/multiclass-classification-examples.png)

<span data-ttu-id="1c8ec-137">Klasifikace problému se dá použít ke kategorizaci vašich názorů zákazníků (například na GitHubu) s použitím názvu a popisu problému.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-137">Issue classification can be used to categorize customer feedback (for example, on GitHub) issues using the issue title and description.</span></span> <span data-ttu-id="1c8ec-138">Je to příklad typu klasifikační model s více třídami.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-138">It is an example of the multi-class classification model type.</span></span>

<span data-ttu-id="1c8ec-139">Šablonu klasifikace problému můžete použít pro váš scénář, pokud chcete rozdělit data do tří nebo více kategorií.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-139">You can use the issue classification template for your scenario if you want to categorize data into three or more categories.</span></span>

#### <a name="predict-a-number"></a><span data-ttu-id="1c8ec-140">Předpovědět číslo</span><span class="sxs-lookup"><span data-stu-id="1c8ec-140">Predict a number</span></span>

<span data-ttu-id="1c8ec-141">Regrese se používá k předpovědi čísel.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-141">Regression is used to predict numbers.</span></span>

![Diagram znázorňující příklady regrese, jako je předpověď ceny, Prognóza prodeje a prediktivní údržba](media/regression-examples.png)

<span data-ttu-id="1c8ec-143">Předpověď cen se dá použít k předvídání cen za domácí ceny pomocí umístění, velikosti a dalších vlastností domu.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-143">Price prediction can be used to predict house prices using location, size, and other characteristics of the house.</span></span> <span data-ttu-id="1c8ec-144">Je příkladem typu regresní model.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-144">It is an example of a regression model type.</span></span>

<span data-ttu-id="1c8ec-145">Šablonu předpovědi cen můžete použít pro váš scénář, pokud chcete předpovědět číselnou hodnotu s vlastní datovou sadou.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-145">You can use the price prediction template for your scenario if you want to predict a numerical value with your own dataset.</span></span>

#### <a name="custom-scenario-choose-your-model-type"></a><span data-ttu-id="1c8ec-146">Vlastní scénář (vyberte typ modelu)</span><span class="sxs-lookup"><span data-stu-id="1c8ec-146">Custom scenario (choose your model type)</span></span>

<span data-ttu-id="1c8ec-147">Vlastní scénář umožňuje ručně zvolit typ modelu.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-147">The custom scenario allows you to manually choose your model type.</span></span>

## <a name="data"></a><span data-ttu-id="1c8ec-148">Data</span><span class="sxs-lookup"><span data-stu-id="1c8ec-148">Data</span></span>

<span data-ttu-id="1c8ec-149">Po zvolení typu modelu bude tvůrce modelů požádán o poskytnutí datové sady.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-149">Once you have chosen your model type, Model Builder asks you to provide a dataset.</span></span> <span data-ttu-id="1c8ec-150">Data se používají ke školení, vyhodnocení a výběru nejlepšího modelu pro váš scénář.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-150">The data is used to train, evaluate, and choose the best model for your scenario.</span></span>

![Diagram znázorňující kroky tvůrce modelů](media/model-builder-steps.png)

### <a name="choose-the-output-to-predict-label"></a><span data-ttu-id="1c8ec-152">Vyberte výstup, který chcete předpovědět (popisek)</span><span class="sxs-lookup"><span data-stu-id="1c8ec-152">Choose the output to predict (label)</span></span>

<span data-ttu-id="1c8ec-153">Datová sada je tabulka řádků příkladů cvičení a sloupce atributů.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-153">A dataset is a table of rows of training examples, and columns of attributes.</span></span> <span data-ttu-id="1c8ec-154">Každý řádek má:</span><span class="sxs-lookup"><span data-stu-id="1c8ec-154">Each row has:</span></span>

- <span data-ttu-id="1c8ec-155">**popisek** (atribut, který chcete předpovědět)</span><span class="sxs-lookup"><span data-stu-id="1c8ec-155">a **label** (the attribute that you want to predict)</span></span>
- <span data-ttu-id="1c8ec-156">**funkce** (atributy, které se používají jako vstupy pro předpověď popisku).</span><span class="sxs-lookup"><span data-stu-id="1c8ec-156">**features** (attributes that are used as inputs to predict the label).</span></span>

<span data-ttu-id="1c8ec-157">Pro scénář předpovědi pro domácí ceny můžou tyto funkce:</span><span class="sxs-lookup"><span data-stu-id="1c8ec-157">For the house-price prediction scenario, the features could be:</span></span>

- <span data-ttu-id="1c8ec-158">čtvercové záběry domu</span><span class="sxs-lookup"><span data-stu-id="1c8ec-158">the square footage of the house</span></span>
- <span data-ttu-id="1c8ec-159">počet ložnicemi a bathrooms</span><span class="sxs-lookup"><span data-stu-id="1c8ec-159">the number of bedrooms and bathrooms</span></span>
- <span data-ttu-id="1c8ec-160">PSČ</span><span class="sxs-lookup"><span data-stu-id="1c8ec-160">the zip code</span></span>

<span data-ttu-id="1c8ec-161">Popisek je cena za cenu na pracovišti pro tento řádek hodnot čtvercového záběru, Bedroom a koupeln a PSČ.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-161">The label is the historical house price for that row of square footage, bedroom, and bathroom values and zip code.</span></span>

![Tabulka znázorňující řádky a sloupce údajů o cenách domu s funkcemi, které se skládají z poštovních místností – PSČ a popisek ceny](media/model-builder-data.png)

### <a name="example-datasets"></a><span data-ttu-id="1c8ec-163">Příklady datových sad</span><span class="sxs-lookup"><span data-stu-id="1c8ec-163">Example datasets</span></span>

<span data-ttu-id="1c8ec-164">Pokud ještě nemáte vlastní data, vyzkoušejte jednu z těchto datových sad:</span><span class="sxs-lookup"><span data-stu-id="1c8ec-164">If you don't have your own data yet, try out one of these datasets:</span></span>

|<span data-ttu-id="1c8ec-165">Scénář</span><span class="sxs-lookup"><span data-stu-id="1c8ec-165">Scenario</span></span>|<span data-ttu-id="1c8ec-166">Typ modelu</span><span class="sxs-lookup"><span data-stu-id="1c8ec-166">Model Type</span></span>|<span data-ttu-id="1c8ec-167">Data</span><span class="sxs-lookup"><span data-stu-id="1c8ec-167">Data</span></span>|<span data-ttu-id="1c8ec-168">Popisek</span><span class="sxs-lookup"><span data-stu-id="1c8ec-168">Label</span></span>|<span data-ttu-id="1c8ec-169">Funkce</span><span class="sxs-lookup"><span data-stu-id="1c8ec-169">Features</span></span>|
|-|-|-|-|-|
|<span data-ttu-id="1c8ec-170">Předpověď ceny</span><span class="sxs-lookup"><span data-stu-id="1c8ec-170">Price prediction</span></span>|<span data-ttu-id="1c8ec-171">Nevýhody</span><span class="sxs-lookup"><span data-stu-id="1c8ec-171">regression</span></span>|[<span data-ttu-id="1c8ec-172">data taxislužby tarifů</span><span class="sxs-lookup"><span data-stu-id="1c8ec-172">taxi fare data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|<span data-ttu-id="1c8ec-173">Vozov</span><span class="sxs-lookup"><span data-stu-id="1c8ec-173">Fare</span></span>|<span data-ttu-id="1c8ec-174">Doba odezvy, vzdálenost</span><span class="sxs-lookup"><span data-stu-id="1c8ec-174">Trip time, distance</span></span>|
|<span data-ttu-id="1c8ec-175">Detekce anomálií</span><span class="sxs-lookup"><span data-stu-id="1c8ec-175">Anomaly detection</span></span>|<span data-ttu-id="1c8ec-176">binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="1c8ec-176">binary classification</span></span>|[<span data-ttu-id="1c8ec-177">prodejní data produktu</span><span class="sxs-lookup"><span data-stu-id="1c8ec-177">product sales data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|<span data-ttu-id="1c8ec-178">Prodej produktu</span><span class="sxs-lookup"><span data-stu-id="1c8ec-178">Product Sales</span></span>|<span data-ttu-id="1c8ec-179">Měsíčně</span><span class="sxs-lookup"><span data-stu-id="1c8ec-179">Month</span></span>|
|<span data-ttu-id="1c8ec-180">Analýza mínění</span><span class="sxs-lookup"><span data-stu-id="1c8ec-180">Sentiment analysis</span></span>|<span data-ttu-id="1c8ec-181">binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="1c8ec-181">binary classification</span></span>|[<span data-ttu-id="1c8ec-182">data komentáře webu</span><span class="sxs-lookup"><span data-stu-id="1c8ec-182">website comment data</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|<span data-ttu-id="1c8ec-183">Popisek (0, pokud je negativní mínění, 1 Při kladném)</span><span class="sxs-lookup"><span data-stu-id="1c8ec-183">Label (0 when negative sentiment, 1 when positive)</span></span>|<span data-ttu-id="1c8ec-184">Komentář, rok</span><span class="sxs-lookup"><span data-stu-id="1c8ec-184">Comment, Year</span></span>|
|<span data-ttu-id="1c8ec-185">Zjišťování podvodů</span><span class="sxs-lookup"><span data-stu-id="1c8ec-185">Fraud detection</span></span>|<span data-ttu-id="1c8ec-186">binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="1c8ec-186">binary classification</span></span>|[<span data-ttu-id="1c8ec-187">data platebních karet</span><span class="sxs-lookup"><span data-stu-id="1c8ec-187">credit card data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|<span data-ttu-id="1c8ec-188">Třída (1, pokud je podvodný, 0 jinak)</span><span class="sxs-lookup"><span data-stu-id="1c8ec-188">Class (1 when fraudulent, 0 otherwise)</span></span>|<span data-ttu-id="1c8ec-189">Množství, V1-v28 (funkce Anonyme)</span><span class="sxs-lookup"><span data-stu-id="1c8ec-189">Amount, V1-V28 (anonymized features)</span></span>|
|<span data-ttu-id="1c8ec-190">Klasifikace textu</span><span class="sxs-lookup"><span data-stu-id="1c8ec-190">Text classification</span></span>|<span data-ttu-id="1c8ec-191">klasifikace s více třídami</span><span class="sxs-lookup"><span data-stu-id="1c8ec-191">multiclass classification</span></span>|[<span data-ttu-id="1c8ec-192">Data o problému na GitHubu</span><span class="sxs-lookup"><span data-stu-id="1c8ec-192">GitHub issue data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|<span data-ttu-id="1c8ec-193">Oblast</span><span class="sxs-lookup"><span data-stu-id="1c8ec-193">Area</span></span>|<span data-ttu-id="1c8ec-194">Název, popis</span><span class="sxs-lookup"><span data-stu-id="1c8ec-194">Title, Description</span></span>|

## <a name="train"></a><span data-ttu-id="1c8ec-195">průřez</span><span class="sxs-lookup"><span data-stu-id="1c8ec-195">Train</span></span>

<span data-ttu-id="1c8ec-196">Když vyberete svůj scénář, data a popisek, tvůrce modelů navlakuje model.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-196">Once you select your scenario, data, and label, Model Builder trains the model.</span></span>

### <a name="what-is-training"></a><span data-ttu-id="1c8ec-197">Co je školení?</span><span class="sxs-lookup"><span data-stu-id="1c8ec-197">What is training?</span></span>

<span data-ttu-id="1c8ec-198">Školení je automatický proces, podle kterého tvůrce modelů učí váš model, jak odpovídat na otázky pro váš scénář.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-198">Training is an automatic process by which Model Builder teaches your model how to answer questions for your scenario.</span></span> <span data-ttu-id="1c8ec-199">Po vyškolení může váš model předpovědi se vstupními daty, ke kterým se předtím neviděl.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-199">Once trained, your model can make predictions with input data that it has not seen before.</span></span> <span data-ttu-id="1c8ec-200">Pokud například předpovídáte ceny za dům a na trhu se nachází nová dům, můžete předpovědět její prodejní cenu.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-200">For example, if you are predicting house prices and a new house comes on the market, you can predict its sale price.</span></span>

<span data-ttu-id="1c8ec-201">Vzhledem k tomu, že tvůrce modelů používá automatizované Machine Learning (AutoML), nevyžaduje během školení žádné vstupy nebo ladění.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-201">Because Model Builder uses automated machine learning (AutoML), it does not require any input or tuning from you during training.</span></span>

## <a name="evaluate"></a><span data-ttu-id="1c8ec-202">Vyhodnotit</span><span class="sxs-lookup"><span data-stu-id="1c8ec-202">Evaluate</span></span>

<span data-ttu-id="1c8ec-203">Vyhodnocení je proces použití výukového modelu k vytvoření předpovědi s novými testovacími daty a k měření toho, jak dobrý je předpovědi.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-203">Evaluation is the process of using the trained model to make predictions with new test data, and then measuring how good the predictions are.</span></span>

<span data-ttu-id="1c8ec-204">Tvůrce modelů rozdělí školicí data do sady školení a sady testů.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-204">Model Builder splits the training data into a training set and a test set.</span></span> <span data-ttu-id="1c8ec-205">Školicí data (80%) se používá ke školení vašeho modelu a testovacích dat (20%) se vrátí k vyhodnocení vašeho modelu.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-205">The training data (80%) is used to train your model and the test data (20%) is held back to evaluate your model.</span></span> <span data-ttu-id="1c8ec-206">Tvůrce modelů používá metriky k měření toho, jak je model dobrý.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-206">Model Builder uses metrics to measure how good the model is.</span></span> <span data-ttu-id="1c8ec-207">Konkrétní použité metriky závisí na typu modelu.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-207">The specific metrics used are dependent on the type of model.</span></span> <span data-ttu-id="1c8ec-208">Další informace najdete v tématu [metriky vyhodnocení modelu](resources/metrics.md).</span><span class="sxs-lookup"><span data-stu-id="1c8ec-208">For more information, see [model evaluation metrics](resources/metrics.md).</span></span>

## <a name="improve"></a><span data-ttu-id="1c8ec-209">Účely</span><span class="sxs-lookup"><span data-stu-id="1c8ec-209">Improve</span></span>

<span data-ttu-id="1c8ec-210">Pokud vaše skóre výkonu vašeho modelu není tak dobré, jak chcete, můžete:</span><span class="sxs-lookup"><span data-stu-id="1c8ec-210">If your model performance score is not as good as you want it to be, you can:</span></span>

- <span data-ttu-id="1c8ec-211">Naučit se delší dobu.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-211">Train for a longer period of time.</span></span> <span data-ttu-id="1c8ec-212">Pomocí automatizovaného strojového učení se navíc snaží vyzkoušet více algoritmů a nastavení.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-212">With more time, the automated machine learning engine to try more algorithms and settings.</span></span>

- <span data-ttu-id="1c8ec-213">Přidejte další data.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-213">Add more data.</span></span> <span data-ttu-id="1c8ec-214">V některých případech se množství dat nestačí pro výuku vysoce kvalitního modelu strojového učení.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-214">Sometimes the amount of data is not sufficient to train a high-quality machine learning model.</span></span>

- <span data-ttu-id="1c8ec-215">Vyvážení dat</span><span class="sxs-lookup"><span data-stu-id="1c8ec-215">Balance your data.</span></span> <span data-ttu-id="1c8ec-216">Pro úlohy klasifikace se ujistěte, že je sada školení vyrovnávána napříč kategoriemi.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-216">For classification tasks, make sure that the training set is balanced across the categories.</span></span> <span data-ttu-id="1c8ec-217">Například pokud máte čtyři třídy pro 100 ukázky a dvě první třídy (značky 1 a značka2) se používají pro 90 záznamů, ale ostatní dvě (značka3 a tag4) se používají jenom u zbývajících 10 záznamů, nedostatek vyvážených dat může způsobit, že váš model bude bojovat do typu korespondenční ectly předpověď značka3 nebo tag4.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-217">For example, if you have four classes for 100 training examples, and the two first classes (tag1 and tag2) are used for 90 records, but the other two (tag3 and tag4) are only used on the remaining 10 records, the lack of balanced data may cause your model to struggle to correctly predict tag3 or tag4.</span></span>

## <a name="code"></a><span data-ttu-id="1c8ec-218">Kód</span><span class="sxs-lookup"><span data-stu-id="1c8ec-218">Code</span></span>

<span data-ttu-id="1c8ec-219">Po fázi vyhodnocení výstup tvůrce modelů vytvoří soubor modelu a kód, který můžete použít k přidání modelu do aplikace.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-219">After the evaluation phase, Model Builder outputs a model file, and code that you can use to add the model to your application.</span></span> <span data-ttu-id="1c8ec-220">Modely ML.NET se ukládají jako soubor zip.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-220">ML.NET models are saved as a zip file.</span></span> <span data-ttu-id="1c8ec-221">Kód pro načtení a použití modelu je přidán jako nový projekt ve vašem řešení.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-221">The code to load and use your model is added as a new project in your solution.</span></span> <span data-ttu-id="1c8ec-222">Tvůrce modelů také přidá ukázkovou konzolovou aplikaci, kterou můžete spustit pro zobrazení modelu v akci.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-222">Model Builder also adds a sample console app that you can run to see your model in action.</span></span>

<span data-ttu-id="1c8ec-223">Kromě toho tvůrce modelů vypíše kód, který model vygeneroval, takže můžete pochopit postup, který se používá ke generování modelu.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-223">In addition, Model Builder outputs the code that generated the model, so that you can understand the steps used to generate the model.</span></span> <span data-ttu-id="1c8ec-224">Můžete také použít kód školení modelu k revýuce modelu s novými daty.</span><span class="sxs-lookup"><span data-stu-id="1c8ec-224">You can also use the model training code to retrain your model with new data.</span></span>

## <a name="whats-next"></a><span data-ttu-id="1c8ec-225">Co dál?</span><span class="sxs-lookup"><span data-stu-id="1c8ec-225">What's next?</span></span>

<span data-ttu-id="1c8ec-226">[Instalace](how-to-guides/install-model-builder.md) rozšíření pro tvůrce modelů sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1c8ec-226">[Install](how-to-guides/install-model-builder.md) the Model Builder Visual Studio extension</span></span>

<span data-ttu-id="1c8ec-227">Vyzkoušejte [cenový odhad nebo jakýkoli scénář regrese](tutorials/predict-prices-with-model-builder.md) .</span><span class="sxs-lookup"><span data-stu-id="1c8ec-227">Try [price prediction or any regression scenario](tutorials/predict-prices-with-model-builder.md)</span></span>
