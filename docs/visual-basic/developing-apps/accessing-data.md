---
title: Přístup k datům v aplikacích Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- data [Visual Basic]
- Visual Basic, data access
ms.assetid: 3086ab38-3be5-4b22-9385-7d0e16b04f6a
ms.openlocfilehash: 0f17df93fc4ef22ef45f7ceff89bfb5f1ab1c18d
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523955"
---
# <a name="accessing-data-in-visual-basic-applications"></a><span data-ttu-id="6c79b-102">Přístup k datům v aplikacích Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6c79b-102">Accessing data in Visual Basic applications</span></span>

<span data-ttu-id="6c79b-103">Visual Basic obsahuje několik nových funkcí, které pomáhají při vývoji aplikací, které přistupují k datům.</span><span class="sxs-lookup"><span data-stu-id="6c79b-103">Visual Basic includes several new features to assist in developing applications that access data.</span></span> <span data-ttu-id="6c79b-104">Formuláře vázané na data pro aplikace systému Windows jsou vytvářeny přetažením položek z [okna zdroje dat](/visualstudio/data-tools/add-new-data-sources) do formuláře.</span><span class="sxs-lookup"><span data-stu-id="6c79b-104">Data-bound forms for Windows applications are created by dragging items from the [Data Sources Window](/visualstudio/data-tools/add-new-data-sources) onto the form.</span></span> <span data-ttu-id="6c79b-105">Ovládací prvky lze navazovat na data přetažením položek z **okna zdroje dat** do existujících ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="6c79b-105">You bind controls to data by dragging items from the **Data Sources Window** onto existing controls.</span></span>

## <a name="related-sections"></a><span data-ttu-id="6c79b-106">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="6c79b-106">Related sections</span></span>

[<span data-ttu-id="6c79b-107">Přístup k datům v aplikaci Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6c79b-107">Accessing Data in Visual Studio</span></span>](/visualstudio/data-tools/)  
<span data-ttu-id="6c79b-108">Obsahuje odkazy na stránky, které popisují zahrnutí funkce přístupu k datům do aplikací.</span><span class="sxs-lookup"><span data-stu-id="6c79b-108">Provides links to pages that discuss incorporating data access functionality into your applications.</span></span>

[<span data-ttu-id="6c79b-109">Visual Studio Data Tools for .NET</span><span class="sxs-lookup"><span data-stu-id="6c79b-109">Visual Studio data tools for .NET</span></span>](/visualstudio/data-tools/visual-studio-data-tools-for-dotnet)  
<span data-ttu-id="6c79b-110">Obsahuje odkazy na stránky o vytváření aplikací pracujících s daty pomocí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6c79b-110">Provides links to pages on creating applications that work with data, using Visual Studio.</span></span>

[<span data-ttu-id="6c79b-111">LINQ</span><span class="sxs-lookup"><span data-stu-id="6c79b-111">LINQ</span></span>](../../visual-basic/programming-guide/language-features/linq/index.md)  
<span data-ttu-id="6c79b-112">Obsahuje odkazy na témata popisující způsob použití technologie LINQ s jazykem Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6c79b-112">Provides links to topics that describe how to use LINQ with Visual Basic.</span></span>

[<span data-ttu-id="6c79b-113">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="6c79b-113">LINQ to SQL</span></span>](../../framework/data/adonet/sql/linq/index.md)  
<span data-ttu-id="6c79b-114">Obsahuje informace o [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6c79b-114">Provides information about [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="6c79b-115">Zahrnuje příklady programování.</span><span class="sxs-lookup"><span data-stu-id="6c79b-115">Includes programming examples.</span></span>  

[<span data-ttu-id="6c79b-116">Nástroje LINQ to SQL v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6c79b-116">LINQ to SQL Tools in Visual Studio</span></span>](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)  
<span data-ttu-id="6c79b-117">Obsahuje odkazy na témata týkající se vytváření [LINQ to SQL](../../framework/data/adonet/sql/linq/index.md) objektového modelu v aplikacích.</span><span class="sxs-lookup"><span data-stu-id="6c79b-117">Provides links to topics about how to create a [LINQ to SQL](../../framework/data/adonet/sql/linq/index.md) object model in applications.</span></span>

[<span data-ttu-id="6c79b-118">Práce s datovými sadami ve vícevrstvých aplikacích</span><span class="sxs-lookup"><span data-stu-id="6c79b-118">Work with datasets in n-tier applications</span></span>](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications)  
<span data-ttu-id="6c79b-119">Obsahuje odkazy na témata o vytváření datových aplikací s více vrstvami.</span><span class="sxs-lookup"><span data-stu-id="6c79b-119">Provides links to topics about how to create multitiered data applications.</span></span>

[<span data-ttu-id="6c79b-120">Přidání nových připojení</span><span class="sxs-lookup"><span data-stu-id="6c79b-120">Add new connections</span></span>](/visualstudio/data-tools/add-new-connections)  
<span data-ttu-id="6c79b-121">Obsahuje odkazy na stránky o připojení aplikace k datům pomocí nástrojů pro dobu návrhu a objektů připojení ADO.NET pomocí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6c79b-121">Provides links to pages on connecting your application to data with design-time tools and ADO.NET connection objects, using Visual Studio.</span></span>

[<span data-ttu-id="6c79b-122">Nástroje datové sady v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6c79b-122">Dataset Tools in Visual Studio</span></span>](/visualstudio/data-tools/dataset-tools-in-visual-studio)  
<span data-ttu-id="6c79b-123">Obsahuje odkazy na stránky, které popisují, jak načíst data do datových sad a jak spouštět SQL příkazy a uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="6c79b-123">Provides links to pages describing how to load data into datasets and how to execute SQL statements and stored procedures.</span></span>  

[<span data-ttu-id="6c79b-124">Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6c79b-124">Bind controls to data in Visual Studio</span></span>](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)  
<span data-ttu-id="6c79b-125">Obsahuje odkazy na stránky, které vysvětlují, jak zobrazit data ve formulářích Windows Forms prostřednictvím ovládacích prvků vázaných na data.</span><span class="sxs-lookup"><span data-stu-id="6c79b-125">Provides links to pages that explain how to display data on Windows Forms through data-bound controls.</span></span>

[<span data-ttu-id="6c79b-126">Úprava dat v datových sadách</span><span class="sxs-lookup"><span data-stu-id="6c79b-126">Edit Data in Datasets</span></span>](/visualstudio/data-tools/edit-data-in-datasets)  
<span data-ttu-id="6c79b-127">Obsahuje odkazy na stránky popisující způsob, jakým lze manipulovat s daty v datových tabulkách datové sady.</span><span class="sxs-lookup"><span data-stu-id="6c79b-127">Provides links to pages describing how to manipulate the data in the data tables of a dataset.</span></span>  

[<span data-ttu-id="6c79b-128">Ověřování dat v datových sadách</span><span class="sxs-lookup"><span data-stu-id="6c79b-128">Validate data in datasets</span></span>](/visualstudio/data-tools/validate-data-in-datasets)  
<span data-ttu-id="6c79b-129">Obsahuje odkazy na stránky popisující způsob, jakým lze přidat ověřování do datové sady během změn řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="6c79b-129">Provides links to pages describing how to add validation to a dataset during column and row changes.</span></span>

[<span data-ttu-id="6c79b-130">Ukládání dat zpět do databáze</span><span class="sxs-lookup"><span data-stu-id="6c79b-130">Save data back to the database</span></span>](/visualstudio/data-tools/save-data-back-to-the-database)  
<span data-ttu-id="6c79b-131">Poskytuje odkazy na stránky vysvětlující postup odeslaní aktualizovaných dat z aplikace do databáze.</span><span class="sxs-lookup"><span data-stu-id="6c79b-131">Provides links to pages explaining how to send updated data from an application to the database.</span></span>

[<span data-ttu-id="6c79b-132">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6c79b-132">ADO.NET</span></span>](../../framework/data/adonet/index.md)  
<span data-ttu-id="6c79b-133">Popisuje třídy rozhraní ADO.NET, které zpřístupňují služby pro přístup k datům programátorovi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6c79b-133">Describes the ADO.NET classes, which expose data-access services to the .NET Framework programmer.</span></span>

[<span data-ttu-id="6c79b-134">Data v řešeních pro systém Office</span><span class="sxs-lookup"><span data-stu-id="6c79b-134">Data in Office Solutions</span></span>](/visualstudio/vsto/data-in-office-solutions)  
<span data-ttu-id="6c79b-135">Obsahuje odkazy na stránky, které vysvětlují, jak fungují data v řešeních sady Office, včetně informací o programování zaměřeném na schéma, ukládání dat do mezipaměti a přístupu k datům na straně serveru.</span><span class="sxs-lookup"><span data-stu-id="6c79b-135">Contains links to pages that explain how data works in Office solutions, including information about schema-oriented programming, data caching, and server-side data access.</span></span>
