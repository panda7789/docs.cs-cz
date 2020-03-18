---
title: Načtení trénovacích dat pro tvůrce modelů
description: Zjistěte, jak načíst trénovací data z databáze serveru SQL Server nebo souboru pro použití v jednom ze scénářů Tvůrce modelů pro ML.NET.
ms.date: 10/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, mlnet-tooling
ms.openlocfilehash: 23de2d06090f4c1eaa2c79178ba4c346698d45e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78849156"
---
# <a name="load-training-data-into-model-builder"></a><span data-ttu-id="9c4cb-103">Načtení dat školení do tvůrce modelů</span><span class="sxs-lookup"><span data-stu-id="9c4cb-103">Load training data into Model Builder</span></span>

<span data-ttu-id="9c4cb-104">Zjistěte, jak načíst trénovací datové sady ze souboru nebo databáze serveru SQL Server pro použití v jednom ze scénářů Tvůrce modelů pro ML.NET.</span><span class="sxs-lookup"><span data-stu-id="9c4cb-104">Learn how to load your training datasets from a file or a SQL Server database for use in one of the Model Builder scenarios for ML.NET.</span></span> <span data-ttu-id="9c4cb-105">Scénáře tvůrce modelů můžete použít SQL Server databáze, obrazové soubory a CSV nebo TSV formáty souborů jako trénovací data.</span><span class="sxs-lookup"><span data-stu-id="9c4cb-105">Model Builder scenarios can use SQL Server databases, image files, and CSV or TSV file formats as training data.</span></span>

## <a name="training-dataset-limitations-in-model-builder"></a><span data-ttu-id="9c4cb-106">Trénování omezení datové sady v Tvůrce modelů</span><span class="sxs-lookup"><span data-stu-id="9c4cb-106">Training dataset limitations in Model Builder</span></span>

<span data-ttu-id="9c4cb-107">Tvůrce modelů omezuje množství a typ dat, které můžete použít pro trénovací modely:</span><span class="sxs-lookup"><span data-stu-id="9c4cb-107">Model Builder limits the amount and type of data you can use for training models:</span></span>

- <span data-ttu-id="9c4cb-108">Data serveru SQL Server: 100 000 řádků</span><span class="sxs-lookup"><span data-stu-id="9c4cb-108">SQL Server data: 100,000 rows</span></span>
- <span data-ttu-id="9c4cb-109">Soubory CSV a TSV: Bez omezení velikosti</span><span class="sxs-lookup"><span data-stu-id="9c4cb-109">CSV and TSV files: No size limit</span></span>
- <span data-ttu-id="9c4cb-110">Obrázky: Pouze PNG a JPG.</span><span class="sxs-lookup"><span data-stu-id="9c4cb-110">Images: PNG and JPG only.</span></span>

## <a name="model-builder-scenarios"></a><span data-ttu-id="9c4cb-111">Scénáře tvůrce modelů</span><span class="sxs-lookup"><span data-stu-id="9c4cb-111">Model Builder scenarios</span></span>

<span data-ttu-id="9c4cb-112">Tvůrce modelů vám pomůže vytvořit modely pro následující scénáře strojového učení:</span><span class="sxs-lookup"><span data-stu-id="9c4cb-112">Model Builder helps you create models for the following machine learning scenarios:</span></span>

- <span data-ttu-id="9c4cb-113">Analýza mínění (binární klasifikace): Klasifikovat textová data do dvou kategorií.</span><span class="sxs-lookup"><span data-stu-id="9c4cb-113">Sentiment analysis (binary classification): Classify textual data into two categories.</span></span>
- <span data-ttu-id="9c4cb-114">Klasifikace problémů (klasifikace více tříd): Klasifikovat textová data do 3 nebo více kategorií.</span><span class="sxs-lookup"><span data-stu-id="9c4cb-114">Issue classification (multiclass classification): Classify textual data into 3 or more categories.</span></span>
- <span data-ttu-id="9c4cb-115">Předpověď cen (regrese): Předpovědět číselnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9c4cb-115">Price prediction (regression): Predict a numeric value.</span></span>
- <span data-ttu-id="9c4cb-116">Klasifikace obrázků (hluboké učení): Kategorizovat obrázky na základě charakteristik.</span><span class="sxs-lookup"><span data-stu-id="9c4cb-116">Image classification (deep learning): Categorize images based on characteristics.</span></span>
- <span data-ttu-id="9c4cb-117">Vlastní scénář: Vytvořte vlastní scénáře z dat pomocí regrese, klasifikace a dalších úkolů.</span><span class="sxs-lookup"><span data-stu-id="9c4cb-117">Custom scenario: Build custom scenarios from your data using regression, classification, and other tasks.</span></span>

<span data-ttu-id="9c4cb-118">Tento článek popisuje scénáře klasifikace a regrese s textovými nebo číselnými daty a scénáře klasifikace obrázků.</span><span class="sxs-lookup"><span data-stu-id="9c4cb-118">This article covers classification and regression scenarios with textual or numerical data, and image classification scenarios.</span></span>

## <a name="load-text-or-numeric-data-from-a-file"></a><span data-ttu-id="9c4cb-119">Načtení textových nebo číselných dat ze souboru</span><span class="sxs-lookup"><span data-stu-id="9c4cb-119">Load text or numeric data from a file</span></span>

<span data-ttu-id="9c4cb-120">Do tvůrce modelů můžete načíst textová nebo číselná data ze souboru.</span><span class="sxs-lookup"><span data-stu-id="9c4cb-120">You can load text or numeric data from a file into Model Builder.</span></span> <span data-ttu-id="9c4cb-121">Přijímá formáty souborů csv (oddělené čárkami) nebo tabulátory (TSV).</span><span class="sxs-lookup"><span data-stu-id="9c4cb-121">It accepts comma-delimited (CSV) or tab-delimited (TSV) file formats.</span></span>

1. <span data-ttu-id="9c4cb-122">V datovém kroku Tvůrce modelů vyberte **Soubor** z rozevíracího souboru zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="9c4cb-122">In the data step of Model Builder, select **File** from the data source dropdown.</span></span>
2. <span data-ttu-id="9c4cb-123">Vyberte tlačítko vedle textového pole **Vybrat soubor** a pomocí Průzkumníka souborů procházejte a vyberte datový soubor.</span><span class="sxs-lookup"><span data-stu-id="9c4cb-123">Select the button next to the **Select a file** text box, and use File Explorer to browse and select the data file.</span></span>
3. <span data-ttu-id="9c4cb-124">V rozevíracím seznamu **Sloupec k předvídání (Popisek)** zvolte kategorii.</span><span class="sxs-lookup"><span data-stu-id="9c4cb-124">Choose a category in the **Column to Predict (Label)** dropdown.</span></span>
4. <span data-ttu-id="9c4cb-125">V rozevíracím seznamu **Vstupní sloupce (Funkce)** zkontrolujte, zda jsou zaškrtnuty datové sloupce, které chcete zahrnout.</span><span class="sxs-lookup"><span data-stu-id="9c4cb-125">From the **Input Columns (Features)** dropdown, confirm the data columns you want to include are checked.</span></span>

<span data-ttu-id="9c4cb-126">Dokončení nastavení souboru zdroje dat pro Tvůrce modelů.</span><span class="sxs-lookup"><span data-stu-id="9c4cb-126">You're done setting up your data source file for Model Builder.</span></span> <span data-ttu-id="9c4cb-127">Vyberte **vlak** odkaz přejít na další krok v Builder.</span><span class="sxs-lookup"><span data-stu-id="9c4cb-127">Select the **Train** link to move to the next step in Model Builder.</span></span>

## <a name="load-data-from-a-sql-server-database"></a><span data-ttu-id="9c4cb-128">Načtení dat z databáze serveru SQL Server</span><span class="sxs-lookup"><span data-stu-id="9c4cb-128">Load data from a SQL Server database</span></span>

<span data-ttu-id="9c4cb-129">Tvůrce modelů podporuje načítání dat z místních a vzdálených databází SERVERU SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9c4cb-129">Model Builder supports loading data from local and remote SQL Server databases.</span></span>

<span data-ttu-id="9c4cb-130">Chcete-li načíst data z databáze serveru SQL Server do tvůrce modulů:</span><span class="sxs-lookup"><span data-stu-id="9c4cb-130">To load data from a SQL Server database into Module Builder:</span></span>

1. <span data-ttu-id="9c4cb-131">V datovém kroku Tvůrce modelů vyberte **SQL Server** z rozevíracího souboru zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="9c4cb-131">In the data step of Model Builder, select **SQL Server** from the data source dropdown.</span></span>
1. <span data-ttu-id="9c4cb-132">Vyberte tlačítko vedle textového pole **Připojit k databázi serveru SQL Server.**</span><span class="sxs-lookup"><span data-stu-id="9c4cb-132">Select the button next to the **Connect to SQL Server database** text box.</span></span>
    1. <span data-ttu-id="9c4cb-133">V dialogovém okně **Zvolit data** vyberte **položku Microsoft SQL Server Database File**.</span><span class="sxs-lookup"><span data-stu-id="9c4cb-133">In the **Choose Data** dialog, select **Microsoft SQL Server Database File**.</span></span>
    1. <span data-ttu-id="9c4cb-134">Zrušte zaškrtnutí políčka **Vždy použít tento výběr** a vyberte **Pokračovat.**</span><span class="sxs-lookup"><span data-stu-id="9c4cb-134">Uncheck the **Always use this selection** checkbox and select **Continue**</span></span>
    1. <span data-ttu-id="9c4cb-135">V dialogovém okně **Vlastnosti připojení** vyberte **Procházet** a vyberte stažený . MDF.</span><span class="sxs-lookup"><span data-stu-id="9c4cb-135">In the **Connection Properties** dialog, select **Browse** and select the downloaded .MDF file.</span></span>
    1. <span data-ttu-id="9c4cb-136">Vybrat **OK**</span><span class="sxs-lookup"><span data-stu-id="9c4cb-136">Select **OK**</span></span>
1. <span data-ttu-id="9c4cb-137">Zvolte název datové sady z rozevíracího souboru **Název tabulky.**</span><span class="sxs-lookup"><span data-stu-id="9c4cb-137">Choose the dataset name from the **Table Name** dropdown.</span></span>
1. <span data-ttu-id="9c4cb-138">V rozevíracím seznamu **Sloupec k předvídání (Popisek)** zvolte kategorii dat, ve které chcete provést předpověď.</span><span class="sxs-lookup"><span data-stu-id="9c4cb-138">From the **Column to Predict (Label)** dropdown, choose the data category on which you want to make a prediction.</span></span>
1. <span data-ttu-id="9c4cb-139">V rozevíracím seznamu **Vstupní sloupce (Funkce)** zkontrolujte, zda jsou zaškrtnuté sloupce, které chcete zahrnout.</span><span class="sxs-lookup"><span data-stu-id="9c4cb-139">From the **Input Columns (Features)** dropdown, confirm the columns you want to include are checked.</span></span>

<span data-ttu-id="9c4cb-140">Dokončení nastavení souboru zdroje dat pro Tvůrce modelů.</span><span class="sxs-lookup"><span data-stu-id="9c4cb-140">You're done setting up your data source file for Model Builder.</span></span> <span data-ttu-id="9c4cb-141">Vyberte **vlak** odkaz přejít na další krok v Builder.</span><span class="sxs-lookup"><span data-stu-id="9c4cb-141">Select the **Train** link to move to the next step in Model Builder.</span></span>

## <a name="set-up-image-data-files"></a><span data-ttu-id="9c4cb-142">Nastavení datových souborů obrázků</span><span class="sxs-lookup"><span data-stu-id="9c4cb-142">Set up image data files</span></span>

<span data-ttu-id="9c4cb-143">Model Builder očekává, že obrazová data budou soubory JPG nebo PNG uspořádané do složek, které odpovídají kategoriím klasifikace.</span><span class="sxs-lookup"><span data-stu-id="9c4cb-143">Model Builder expects image data to be JPG or PNG files organized in folders that correspond to the categories of the classification.</span></span>

<span data-ttu-id="9c4cb-144">Chcete-li načíst obrázky do tvůrce modelů, zadejte cestu k jednomu adresáři nejvyšší úrovně:</span><span class="sxs-lookup"><span data-stu-id="9c4cb-144">To load images into Model Builder, provide the path to a single top-level directory:</span></span>

- <span data-ttu-id="9c4cb-145">Tento adresář nejvyšší úrovně obsahuje jednu podsložku pro každou z kategorií předpovědět.</span><span class="sxs-lookup"><span data-stu-id="9c4cb-145">This top-level directory contains one subfolder for each of the categories to predict.</span></span>
- <span data-ttu-id="9c4cb-146">Každá podsložka obsahuje obrazové soubory, které patří do jeho kategorie.</span><span class="sxs-lookup"><span data-stu-id="9c4cb-146">Each subfolder contains the image files belonging to its category.</span></span>

<span data-ttu-id="9c4cb-147">Ve struktuře složek, která je znázorněna níže, je adresář nejvyšší úrovně *flower_photos*.</span><span class="sxs-lookup"><span data-stu-id="9c4cb-147">In the folder structure illustrated below, the top-level directory is *flower_photos*.</span></span> <span data-ttu-id="9c4cb-148">Existuje pět podadresářů odpovídajících kategoriím, které chcete předpovědět: sedmikráska, pampeliška, růže, slunečnice a tulipány.</span><span class="sxs-lookup"><span data-stu-id="9c4cb-148">There are five subdirectories corresponding to the categories you want to predict: daisy, dandelion, roses, sunflowers, and tulips.</span></span> <span data-ttu-id="9c4cb-149">Každý z těchto podadresářů obsahuje obrázky, které patří do jeho příslušné kategorie.</span><span class="sxs-lookup"><span data-stu-id="9c4cb-149">Each of these subdirectories contains images belonging to its respective category.</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="9c4cb-150">Další kroky</span><span class="sxs-lookup"><span data-stu-id="9c4cb-150">Next steps</span></span>

<span data-ttu-id="9c4cb-151">Podle těchto kurzů můžete vytvářet aplikace pro strojové učení pomocí modelového tvůrce:</span><span class="sxs-lookup"><span data-stu-id="9c4cb-151">Follow these tutorials to build machine learning apps with Model Builder:</span></span>

- [<span data-ttu-id="9c4cb-152">Předvídání cen pomocí regrese</span><span class="sxs-lookup"><span data-stu-id="9c4cb-152">Predict prices using regression</span></span>](../tutorials/predict-prices-with-model-builder.md)
- [<span data-ttu-id="9c4cb-153">Analýza mínění ve webové aplikaci pomocí binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="9c4cb-153">Analyze sentiment in a web application using binary classification</span></span>](../tutorials/sentiment-analysis-model-builder.md )

<span data-ttu-id="9c4cb-154">Pokud trénujete model pomocí kódu, [přečtěte si, jak načíst data pomocí ML.NET rozhraní API](load-data-ml-net.md).</span><span class="sxs-lookup"><span data-stu-id="9c4cb-154">If you're training a model using code, [learn how to load data using the ML.NET API](load-data-ml-net.md).</span></span>
