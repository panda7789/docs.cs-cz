---
title: "Přístup k datům v aplikacích jazyka Visual Basic"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- data [Visual Basic]
- Visual Basic, data access
ms.assetid: 3086ab38-3be5-4b22-9385-7d0e16b04f6a
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fd4dbc66f37325afa64b7bf9720cad23e08c6bfb
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2017
---
# <a name="accessing-data-in-visual-basic-applications"></a><span data-ttu-id="94b35-102">Přístup k datům v aplikacích jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="94b35-102">Accessing data in Visual Basic applications</span></span>
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="94b35-103"> obsahuje několik nových funkcí, které pomáhají při vývoji aplikací přistupujících k datům.</span><span class="sxs-lookup"><span data-stu-id="94b35-103"> includes several new features to assist in developing applications that access data.</span></span> <span data-ttu-id="94b35-104">Vázané na data formuláře pro aplikace systému Windows jsou vytvořeny tak, že přetáhnete položky z [okno zdroje dat](/visualstudio/data-tools/add-new-data-sources) do formuláře.</span><span class="sxs-lookup"><span data-stu-id="94b35-104">Data-bound forms for Windows applications are created by dragging items from the [Data Sources Window](/visualstudio/data-tools/add-new-data-sources) onto the form.</span></span> <span data-ttu-id="94b35-105">Vytvoření vazby ovládacích prvků k datům tak, že přetáhnete položky z **okno zdroje dat** do existujícího ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="94b35-105">You bind controls to data by dragging items from the **Data Sources Window** onto existing controls.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="94b35-106">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="94b35-106">Related sections</span></span>  
 [<span data-ttu-id="94b35-107">Přístup k datům v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="94b35-107">Accessing Data in Visual Studio</span></span>](/visualstudio/data-tools/)  
 <span data-ttu-id="94b35-108">Obsahuje odkazy na stránky, které popisují zahrnutí funkce přístupu k datům do aplikací.</span><span class="sxs-lookup"><span data-stu-id="94b35-108">Provides links to pages that discuss incorporating data access functionality into your applications.</span></span>

 [<span data-ttu-id="94b35-109">Visual Studio Data Tools for .NET</span><span class="sxs-lookup"><span data-stu-id="94b35-109">Visual Studio data tools for .NET</span></span>](/visualstudio/data-tools/visual-studio-data-tools-for-dotnet)  
 <span data-ttu-id="94b35-110">Obsahuje odkazy na stránky o vytváření aplikací, které pracují s daty, pomocí [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="94b35-110">Provides links to pages on creating applications that work with data, using [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)].</span></span>  
  
 [<span data-ttu-id="94b35-111">LINQ</span><span class="sxs-lookup"><span data-stu-id="94b35-111">LINQ</span></span>](../../visual-basic/programming-guide/language-features/linq/index.md)  
 <span data-ttu-id="94b35-112">Obsahuje odkazy na témata popisující způsob použití technologie LINQ s jazykem Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="94b35-112">Provides links to topics that describe how to use LINQ with Visual Basic.</span></span>  
  
 [<span data-ttu-id="94b35-113">Technologie LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="94b35-113">LINQ to SQL</span></span>](../../../docs/framework/data/adonet/sql/linq/index.md)  
 <span data-ttu-id="94b35-114">Obsahuje informace o [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="94b35-114">Provides information about [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="94b35-115">Zahrnuje příklady programování.</span><span class="sxs-lookup"><span data-stu-id="94b35-115">Includes programming examples.</span></span>  
  
 [<span data-ttu-id="94b35-116">Technologie LINQ to SQL nástroje v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="94b35-116">LINQ to SQL Tools in Visual Studio</span></span>](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)  
 <span data-ttu-id="94b35-117">Obsahuje odkazy na témata o tom, jak vytvořit [technologie LINQ to SQL](../../../docs/framework/data/adonet/sql/linq/index.md) objektový model v aplikacích.</span><span class="sxs-lookup"><span data-stu-id="94b35-117">Provides links to topics about how to create a [LINQ to SQL](../../../docs/framework/data/adonet/sql/linq/index.md) object model in applications.</span></span>  
  
 [<span data-ttu-id="94b35-118">Práce s datovými sadami ve vícevrstvých aplikacích</span><span class="sxs-lookup"><span data-stu-id="94b35-118">Work with datasets in n-tier applications</span></span>](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications)  
 <span data-ttu-id="94b35-119">Obsahuje odkazy na témata o vytváření datových aplikací s více vrstvami.</span><span class="sxs-lookup"><span data-stu-id="94b35-119">Provides links to topics about how to create multitiered data applications.</span></span>  
     
 [<span data-ttu-id="94b35-120">Přidat nové připojení</span><span class="sxs-lookup"><span data-stu-id="94b35-120">Add new connections</span></span>](/visualstudio/data-tools/add-new-connections)  
 <span data-ttu-id="94b35-121">Obsahuje odkazy na stránky o připojení aplikace k datům pomocí návrhových nástrojů a objektů připojení rozhraní ADO.NET pomocí sady [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="94b35-121">Provides links to pages on connecting your application to data with design-time tools and ADO.NET connection objects, using [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)].</span></span>  

 [<span data-ttu-id="94b35-122">Datové sady nástrojů v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="94b35-122">Dataset Tools in Visual Studio</span></span>](/visualstudio/data-tools/dataset-tools-in-visual-studio)  
 <span data-ttu-id="94b35-123">Obsahuje odkazy na stránky, které popisují, jak načíst data do datových sad a jak spouštět SQL příkazy a uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="94b35-123">Provides links to pages describing how to load data into datasets and how to execute SQL statements and stored procedures.</span></span>  
  
 [<span data-ttu-id="94b35-124">Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="94b35-124">Bind controls to data in Visual Studio</span></span>](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)  
 <span data-ttu-id="94b35-125">Obsahuje odkazy na stránky, které vysvětlují, jak zobrazit data ve formulářích Windows Forms prostřednictvím ovládacích prvků vázaných na data.</span><span class="sxs-lookup"><span data-stu-id="94b35-125">Provides links to pages that explain how to display data on Windows Forms through data-bound controls.</span></span>  
  
 [<span data-ttu-id="94b35-126">Úpravy dat v datových sadách</span><span class="sxs-lookup"><span data-stu-id="94b35-126">Edit Data in Datasets</span></span>](/visualstudio/data-tools/edit-data-in-datasets)  
 <span data-ttu-id="94b35-127">Obsahuje odkazy na stránky popisující způsob, jakým lze manipulovat s daty v datových tabulkách datové sady.</span><span class="sxs-lookup"><span data-stu-id="94b35-127">Provides links to pages describing how to manipulate the data in the data tables of a dataset.</span></span>  
  
 [<span data-ttu-id="94b35-128">Ověřování dat v datových sadách</span><span class="sxs-lookup"><span data-stu-id="94b35-128">Validate data in datasets</span></span>](/visualstudio/data-tools/validate-data-in-datasets)  
 <span data-ttu-id="94b35-129">Obsahuje odkazy na stránky popisující způsob, jakým lze přidat ověřování do datové sady během změn řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="94b35-129">Provides links to pages describing how to add validation to a dataset during column and row changes.</span></span>  
  
 [<span data-ttu-id="94b35-130">Ukládání dat zpět do databáze</span><span class="sxs-lookup"><span data-stu-id="94b35-130">Save data back to the database</span></span>](/visualstudio/data-tools/save-data-back-to-the-database)  
 <span data-ttu-id="94b35-131">Poskytuje odkazy na stránky vysvětlující postup odeslaní aktualizovaných dat z aplikace do databáze.</span><span class="sxs-lookup"><span data-stu-id="94b35-131">Provides links to pages explaining how to send updated data from an application to the database.</span></span>  
  
 [<span data-ttu-id="94b35-132">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="94b35-132">ADO.NET</span></span>](https://msdn.microsoft.com/library/e80y5yhx.aspx)  
 <span data-ttu-id="94b35-133">Popisuje třídy rozhraní ADO.NET, které zpřístupňují služby pro přístup k datům programátorovi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="94b35-133">Describes the ADO.NET classes, which expose data-access services to the .NET Framework programmer.</span></span>

 [<span data-ttu-id="94b35-134">Data v řešeních pro systém Office</span><span class="sxs-lookup"><span data-stu-id="94b35-134">Data in Office Solutions</span></span>](https://msdn.microsoft.com/library/xx069ybh)  
 <span data-ttu-id="94b35-135">Obsahuje odkazy na stránky, které vysvětlují, jak fungují data v řešeních sady Office, včetně informací o programování zaměřeném na schéma, ukládání dat do mezipaměti a přístupu k datům na straně serveru.</span><span class="sxs-lookup"><span data-stu-id="94b35-135">Contains links to pages that explain how data works in Office solutions, including information about schema-oriented programming, data caching, and server-side data access.</span></span>
