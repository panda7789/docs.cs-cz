---
title: Načíst data školení pro tvůrce modelů
description: Naučte se, jak načíst školicí data z SQL Server databáze nebo souboru pro použití v jednom ze scénářů tvůrce modelů pro ML.NET.
ms.date: 10/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 47dd32d18d00c33bcf51aa0ea3be8b22494ebc5f
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73041273"
---
# <a name="load-training-data-into-model-builder"></a><span data-ttu-id="c9afa-103">Načtení dat školení do Tvůrce modelů</span><span class="sxs-lookup"><span data-stu-id="c9afa-103">Load training data into Model Builder</span></span>

<span data-ttu-id="c9afa-104">Naučte se, jak načíst datové sady pro školení ze souboru nebo databáze SQL Server pro použití v jednom ze scénářů tvůrce modelů pro ML.NET.</span><span class="sxs-lookup"><span data-stu-id="c9afa-104">Learn how to load your training datasets from a file or a SQL Server database for use in one of the Model Builder scenarios for ML.NET.</span></span> <span data-ttu-id="c9afa-105">Scénáře tvůrce modelů můžou jako školicí data používat databáze SQL Server, soubory obrázků a formáty souborů CSV nebo TSV.</span><span class="sxs-lookup"><span data-stu-id="c9afa-105">Model Builder scenarios can use SQL Server databases, image files, and CSV or TSV file formats as training data.</span></span>

## <a name="training-dataset-limitations-in-model-builder"></a><span data-ttu-id="c9afa-106">Omezení datové sady školení v Tvůrci modelů</span><span class="sxs-lookup"><span data-stu-id="c9afa-106">Training dataset limitations in Model Builder</span></span>

<span data-ttu-id="c9afa-107">Tvůrce modelů omezuje množství a typ dat, která můžete použít pro školicí modely:</span><span class="sxs-lookup"><span data-stu-id="c9afa-107">Model Builder limits the amount and type of data you can use for training models:</span></span>

- <span data-ttu-id="c9afa-108">SQL Server data: 100 000 řádků</span><span class="sxs-lookup"><span data-stu-id="c9afa-108">SQL Server data: 100,000 rows</span></span> 
- <span data-ttu-id="c9afa-109">Soubory CSV a TSV: bez omezení velikosti</span><span class="sxs-lookup"><span data-stu-id="c9afa-109">CSV and TSV files: No size limit</span></span>
- <span data-ttu-id="c9afa-110">Obrázky: pouze PNG a JPG.</span><span class="sxs-lookup"><span data-stu-id="c9afa-110">Images: PNG and JPG only.</span></span>

## <a name="model-builder-scenarios"></a><span data-ttu-id="c9afa-111">Scénáře tvůrce modelů</span><span class="sxs-lookup"><span data-stu-id="c9afa-111">Model Builder scenarios</span></span> 

<span data-ttu-id="c9afa-112">Tvůrce modelů vám pomůže vytvořit modely pro následující scénáře strojového učení:</span><span class="sxs-lookup"><span data-stu-id="c9afa-112">Model Builder helps you create models for the following machine learning scenarios:</span></span>

- <span data-ttu-id="c9afa-113">Analýza mínění (binární klasifikace): klasifikace textových dat do dvou kategorií.</span><span class="sxs-lookup"><span data-stu-id="c9afa-113">Sentiment analysis (binary classification): Classify textual data into two categories.</span></span>
- <span data-ttu-id="c9afa-114">Klasifikace problému (klasifikace více tříd): klasifikace textových dat do 3 nebo více kategorií.</span><span class="sxs-lookup"><span data-stu-id="c9afa-114">Issue classification (multiclass classification): Classify textual data into 3 or more categories.</span></span>
- <span data-ttu-id="c9afa-115">Předpověď ceny (regrese): předpověď číselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c9afa-115">Price prediction (regression): Predict a numeric value.</span></span>
- <span data-ttu-id="c9afa-116">Klasifikace obrázků (obsáhlý Learning): kategorizace imagí podle vlastností.</span><span class="sxs-lookup"><span data-stu-id="c9afa-116">Image classification (deep learning): Categorize images based on characteristics.</span></span>
- <span data-ttu-id="c9afa-117">Vlastní scénář: Sestavujte vlastní scénáře z vašich dat pomocí regresí, klasifikace a dalších úkolů.</span><span class="sxs-lookup"><span data-stu-id="c9afa-117">Custom scenario: Build custom scenarios from your data using regression, classification, and other tasks.</span></span>

<span data-ttu-id="c9afa-118">Tento článek popisuje scénáře klasifikace a regrese s textovými nebo numerickými daty a scénáři klasifikace obrázků.</span><span class="sxs-lookup"><span data-stu-id="c9afa-118">This article covers classification and regression scenarios with textual or numerical data, and image classification scenarios.</span></span> 

## <a name="load-text-or-numeric-data-from-a-file"></a><span data-ttu-id="c9afa-119">Načtení textu nebo číselných dat ze souboru</span><span class="sxs-lookup"><span data-stu-id="c9afa-119">Load text or numeric data from a file</span></span>  

<span data-ttu-id="c9afa-120">Do Tvůrce modelů můžete načíst text nebo číselná data ze souboru.</span><span class="sxs-lookup"><span data-stu-id="c9afa-120">You can load text or numeric data from a file into Model Builder.</span></span> <span data-ttu-id="c9afa-121">Přijímá formáty souborů ve formátu CSV nebo oddělených tabulátory (TSV).</span><span class="sxs-lookup"><span data-stu-id="c9afa-121">It accepts comma-delimited (CSV) or tab-delimited (TSV) file formats.</span></span> 

1. <span data-ttu-id="c9afa-122">V části datový krok tvůrce modelů vyberte v rozevíracím seznamu zdroj dat možnost **soubor** .</span><span class="sxs-lookup"><span data-stu-id="c9afa-122">In the data step of Model Builder, select **File** from the data source dropdown.</span></span>
2. <span data-ttu-id="c9afa-123">Vyberte tlačítko vedle textového pole **Vybrat soubor** a pomocí Průzkumníka souborů Procházejte a vyberte datový soubor.</span><span class="sxs-lookup"><span data-stu-id="c9afa-123">Select the button next to the **Select a file** text box, and use File Explorer to browse and select the data file.</span></span>
3. <span data-ttu-id="c9afa-124">Vyberte kategorii v rozevíracím seznamu **sloupec pro předpověď (popisek)** .</span><span class="sxs-lookup"><span data-stu-id="c9afa-124">Choose a category in the **Column to Predict (Label)** dropdown.</span></span>
4. <span data-ttu-id="c9afa-125">V rozevíracím seznamu **vstupní sloupce (funkce)** potvrďte, že jsou zaškrtnuté sloupce dat, které chcete zahrnout.</span><span class="sxs-lookup"><span data-stu-id="c9afa-125">From the **Input Columns (Features)** dropdown, confirm the data columns you want to include are checked.</span></span>

<span data-ttu-id="c9afa-126">Pro tvůrce modelů jste dokončili nastavení souboru zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="c9afa-126">You're done setting up your data source file for Model Builder.</span></span> <span data-ttu-id="c9afa-127">Vyberte odkaz **výuka** , který se přesune k dalšímu kroku v Tvůrci modelů.</span><span class="sxs-lookup"><span data-stu-id="c9afa-127">Select the **Train** link to move to the next step in Model Builder.</span></span>

## <a name="load-data-from-a-sql-server-database"></a><span data-ttu-id="c9afa-128">Načtení dat z databáze SQL Server</span><span class="sxs-lookup"><span data-stu-id="c9afa-128">Load data from a SQL Server database</span></span>

<span data-ttu-id="c9afa-129">Tvůrce modelů podporuje načítání dat z místních a vzdálených SQL Serverch databází.</span><span class="sxs-lookup"><span data-stu-id="c9afa-129">Model Builder supports loading data from local and remote SQL Server databases.</span></span>

<span data-ttu-id="c9afa-130">Načtení dat z databáze SQL Server do Tvůrce modulů:</span><span class="sxs-lookup"><span data-stu-id="c9afa-130">To load data from a SQL Server database into Module Builder:</span></span>

1. <span data-ttu-id="c9afa-131">V části datový krok tvůrce modelů vyberte v rozevíracím seznamu zdroj dat možnost **SQL Server** .</span><span class="sxs-lookup"><span data-stu-id="c9afa-131">In the data step of Model Builder, select **SQL Server** from the data source dropdown.</span></span>
1. <span data-ttu-id="c9afa-132">Vyberte tlačítko vedle textového pole **připojit k SQL Server databázi** .</span><span class="sxs-lookup"><span data-stu-id="c9afa-132">Select the button next to the **Connect to SQL Server database** text box.</span></span>
    1. <span data-ttu-id="c9afa-133">V dialogovém okně **Vybrat data** vyberte **Microsoft SQL Server databázový soubor**.</span><span class="sxs-lookup"><span data-stu-id="c9afa-133">In the **Choose Data** dialog, select **Microsoft SQL Server Database File**.</span></span> 
    1. <span data-ttu-id="c9afa-134">Zrušte zaškrtnutí políčka **vždy použít tento výběr** a vyberte **pokračovat** .</span><span class="sxs-lookup"><span data-stu-id="c9afa-134">Uncheck the **Always use this selection** checkbox and select **Continue**</span></span>
    1. <span data-ttu-id="c9afa-135">V dialogovém okně **Vlastnosti připojení** vyberte **Procházet** a vyberte stažený. Soubor MDF.</span><span class="sxs-lookup"><span data-stu-id="c9afa-135">In the **Connection Properties** dialog, select **Browse** and select the downloaded .MDF file.</span></span>
    1. <span data-ttu-id="c9afa-136">Vybrat **OK**</span><span class="sxs-lookup"><span data-stu-id="c9afa-136">Select **OK**</span></span>
1. <span data-ttu-id="c9afa-137">Z rozevíracího seznamu **název tabulky** vyberte název datové sady.</span><span class="sxs-lookup"><span data-stu-id="c9afa-137">Choose the dataset name from the **Table Name** dropdown.</span></span>
1. <span data-ttu-id="c9afa-138">V rozevíracím seznamu **sloupec pro předpověď (popisek)** vyberte kategorii dat, na které chcete vytvořit předpověď.</span><span class="sxs-lookup"><span data-stu-id="c9afa-138">From the **Column to Predict (Label)** dropdown, choose the data category on which you want to make a prediction.</span></span>
1. <span data-ttu-id="c9afa-139">V rozevíracím seznamu **vstupní sloupce (funkce)** potvrďte zaškrtnutí sloupců, které chcete zahrnout.</span><span class="sxs-lookup"><span data-stu-id="c9afa-139">From the **Input Columns (Features)** dropdown, confirm the columns you want to include are checked.</span></span> 

<span data-ttu-id="c9afa-140">Pro tvůrce modelů jste dokončili nastavení souboru zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="c9afa-140">You're done setting up your data source file for Model Builder.</span></span> <span data-ttu-id="c9afa-141">Vyberte odkaz **výuka** , který se přesune k dalšímu kroku v Tvůrci modelů.</span><span class="sxs-lookup"><span data-stu-id="c9afa-141">Select the **Train** link to move to the next step in Model Builder.</span></span>

## <a name="set-up-image-data-files"></a><span data-ttu-id="c9afa-142">Nastavení datových souborů obrázků</span><span class="sxs-lookup"><span data-stu-id="c9afa-142">Set up image data files</span></span>

<span data-ttu-id="c9afa-143">Tvůrce modelů očekává, že obrazová data budou mít soubory JPG nebo PNG uspořádané ve složkách, které odpovídají kategoriím klasifikace.</span><span class="sxs-lookup"><span data-stu-id="c9afa-143">Model Builder expects image data to be JPG or PNG files organized in folders that correspond to the categories of the classification.</span></span> 

<span data-ttu-id="c9afa-144">Pokud chcete načíst obrázky do Tvůrce modelů, zadejte cestu k jednomu adresáři nejvyšší úrovně:</span><span class="sxs-lookup"><span data-stu-id="c9afa-144">To load images into Model Builder, provide the path to a single top-level directory:</span></span>

- <span data-ttu-id="c9afa-145">Tento adresář nejvyšší úrovně obsahuje jednu podsložku pro každou kategorii, kterou chcete předpovědět.</span><span class="sxs-lookup"><span data-stu-id="c9afa-145">This top-level directory contains one subfolder for each of the categories to predict.</span></span> 
- <span data-ttu-id="c9afa-146">Každá podsložka obsahuje soubory obrázků patřící do příslušné kategorie.</span><span class="sxs-lookup"><span data-stu-id="c9afa-146">Each subfolder contains the image files belonging to its category.</span></span> 
 
<span data-ttu-id="c9afa-147">Ve struktuře složek, která je znázorněna níže, je adresář nejvyšší úrovně *flower_photos*.</span><span class="sxs-lookup"><span data-stu-id="c9afa-147">In the folder structure illustrated below, the top-level directory is *flower_photos*.</span></span> <span data-ttu-id="c9afa-148">Existuje pět podadresářů odpovídajících kategoriím, které chcete předpovědět: uzavřené, Dandelion, růže, slunečnice a Tulips.</span><span class="sxs-lookup"><span data-stu-id="c9afa-148">There are five subdirectories corresponding to the categories you want to predict: daisy, dandelion, roses, sunflowers, and tulips.</span></span> <span data-ttu-id="c9afa-149">Každý z těchto podadresářů obsahuje obrázky, které patří do příslušné kategorie.</span><span class="sxs-lookup"><span data-stu-id="c9afa-149">Each of these subdirectories contains images belonging to its respective category.</span></span> 

```text
\---flower_photos
    +---daisy
    |       100080576_f52e8ee070_n.jpg
    |       102841525_bd6628ae3c.jpg
    |       105806915_a9c13e2106_n.jpg
    |       
    +---dandelion
    |       10443973_aeb97513fc_m.jpg
    |       10683189_bd6e371b97.jpg
    |       10919961_0af657c4e8.jpg
    |       
    +---roses
    |       102501987_3cdb8e5394_n.jpg
    |       110472418_87b6a3aa98_m.jpg
    |       118974357_0faa23cce9_n.jpg
    |       
    +---sunflowers
    |       127192624_afa3d9cb84.jpg
    |       145303599_2627e23815_n.jpg
    |       147804446_ef9244c8ce_m.jpg
    |       
    \---tulips
            100930342_92e8746431_n.jpg
            107693873_86021ac4ea_n.jpg
            10791227_7168491604.jpg  
```

## <a name="next-steps"></a><span data-ttu-id="c9afa-150">Další kroky</span><span class="sxs-lookup"><span data-stu-id="c9afa-150">Next steps</span></span>
<span data-ttu-id="c9afa-151">Pomocí těchto kurzů sestavíte aplikace Machine Learning pomocí Tvůrce modelů:</span><span class="sxs-lookup"><span data-stu-id="c9afa-151">Follow these tutorials to build machine learning apps with Model Builder:</span></span>

- [<span data-ttu-id="c9afa-152">Předpověď cen pomocí regrese</span><span class="sxs-lookup"><span data-stu-id="c9afa-152">Predict prices using regression</span></span>](../tutorials/predict-prices-with-model-builder.md)
- [<span data-ttu-id="c9afa-153">Analýza mínění ve webové aplikaci pomocí binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="c9afa-153">Analyze sentiment in a web application using binary classification</span></span>](../tutorials/sentiment-analysis-model-builder.md )

<span data-ttu-id="c9afa-154">Pokud model sledujete pomocí kódu, [Naučte se načíst data pomocí rozhraní ml.NET API](load-data-ml-net.md).</span><span class="sxs-lookup"><span data-stu-id="c9afa-154">If you're training a model using code, [learn how to load data using the ML.NET API](load-data-ml-net.md).</span></span>
