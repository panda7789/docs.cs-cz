---
title: Průvodce programováním
ms.date: 03/30/2017
ms.assetid: ed1012d4-3ff2-4877-af27-93125c4180ea
ms.openlocfilehash: 542567cf07e86b642a23a879fa6e5476253005b8
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78848935"
---
# <a name="programming-guide"></a><span data-ttu-id="06ce4-102">Průvodce programováním</span><span class="sxs-lookup"><span data-stu-id="06ce4-102">Programming Guide</span></span>
<span data-ttu-id="06ce4-103">Tato část obsahuje informace o tom, jak vytvořit a používat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objektový model.</span><span class="sxs-lookup"><span data-stu-id="06ce4-103">This section contains information about how to create and use your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="06ce4-104">Pokud používáte Visual Studio, můžete také použít objekt relační návrhářprovádět mnoho z těchto stejných úkolů.</span><span class="sxs-lookup"><span data-stu-id="06ce4-104">If you are using Visual Studio, you can also use the Object Relational Designer to perform many of these same tasks.</span></span>  
  
 <span data-ttu-id="06ce4-105">Můžete také vyhledat konkrétní problémy v dokumentech společnosti Microsoft a můžete se zúčastnit [fóra LINQ](https://social.msdn.microsoft.com/forums/home?forum=linqtosql), kde můžete podrobněji diskutovat o složitějších tématech s odborníky.</span><span class="sxs-lookup"><span data-stu-id="06ce4-105">You can also search Microsoft Docs for specific issues, and you can participate in the [LINQ Forum](https://social.msdn.microsoft.com/forums/home?forum=linqtosql), where you can discuss more complex topics in detail with experts.</span></span> <span data-ttu-id="06ce4-106">Nakonec [LINQ na SQL: .NET Jazyk integrovaný dotaz pro relační data](https://docs.microsoft.com/previous-versions/dotnet/articles/bb425822(v=msdn.10)) podrobnosti [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technologie, kompletní s příklady kódu jazyka A C#.</span><span class="sxs-lookup"><span data-stu-id="06ce4-106">Finally, the [LINQ to SQL: .NET Language-Integrated Query for Relational Data](https://docs.microsoft.com/previous-versions/dotnet/articles/bb425822(v=msdn.10)) white paper details [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology, complete with Visual Basic and C# code examples.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="06ce4-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="06ce4-107">In This Section</span></span>  
 [<span data-ttu-id="06ce4-108">Vytvoření objektového modelu</span><span class="sxs-lookup"><span data-stu-id="06ce4-108">Creating the Object Model</span></span>](creating-the-object-model.md)  
 <span data-ttu-id="06ce4-109">Popisuje, jak generovat objektový model.</span><span class="sxs-lookup"><span data-stu-id="06ce4-109">Describes how to generate an object model.</span></span>  
  
 [<span data-ttu-id="06ce4-110">Komunikace s databází</span><span class="sxs-lookup"><span data-stu-id="06ce4-110">Communicating with the Database</span></span>](communicating-with-the-database.md)  
 <span data-ttu-id="06ce4-111">Popisuje způsob použití <xref:System.Data.Linq.DataContext> objektu jako potrubí do databáze.</span><span class="sxs-lookup"><span data-stu-id="06ce4-111">Describes how to use a <xref:System.Data.Linq.DataContext> object as a conduit to the database.</span></span>  
  
 [<span data-ttu-id="06ce4-112">Dotazování na databázi</span><span class="sxs-lookup"><span data-stu-id="06ce4-112">Querying the Database</span></span>](querying-the-database.md)  
 <span data-ttu-id="06ce4-113">Popisuje, jak provádět dotazy [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]v , a poskytuje mnoho příkladů.</span><span class="sxs-lookup"><span data-stu-id="06ce4-113">Describes how to execute queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], and provides many examples.</span></span>  
  
 [<span data-ttu-id="06ce4-114">Vytvoření a odeslání změn dat</span><span class="sxs-lookup"><span data-stu-id="06ce4-114">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)  
 <span data-ttu-id="06ce4-115">Popisuje, jak změnit data v databázi.</span><span class="sxs-lookup"><span data-stu-id="06ce4-115">Describes how change data in the database.</span></span>  
  
 [<span data-ttu-id="06ce4-116">Podpora ladění</span><span class="sxs-lookup"><span data-stu-id="06ce4-116">Debugging Support</span></span>](debugging-support.md)  
 <span data-ttu-id="06ce4-117">Popisuje podporu, která je k [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dispozici pro ladění projektů.</span><span class="sxs-lookup"><span data-stu-id="06ce4-117">Describes the support available for debugging [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects.</span></span>  
  
 [<span data-ttu-id="06ce4-118">Základní informace</span><span class="sxs-lookup"><span data-stu-id="06ce4-118">Background Information</span></span>](background-information.md)  
 <span data-ttu-id="06ce4-119">Zahrnuje další položky, jako je například řešení konfliktů souběžnosti, vytváření nových databází a další položky pro pokročilejší uživatele.</span><span class="sxs-lookup"><span data-stu-id="06ce4-119">Includes additional items, such as concurrency conflict resolution, creating new databases, and more, for more advanced users.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="06ce4-120">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="06ce4-120">Related Sections</span></span>  
 [<span data-ttu-id="06ce4-121">Technologie LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="06ce4-121">LINQ to SQL</span></span>](index.md)  
 <span data-ttu-id="06ce4-122">Obsahuje odkazy na témata, která vysvětlují technologii [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] a demonstrují funkce.</span><span class="sxs-lookup"><span data-stu-id="06ce4-122">Provides links to topics that explain the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology and demonstrate features.</span></span>  
  
 [<span data-ttu-id="06ce4-123">Uložené procedury</span><span class="sxs-lookup"><span data-stu-id="06ce4-123">Stored Procedures</span></span>](stored-procedures.md)  
 <span data-ttu-id="06ce4-124">Obsahuje odkazy na témata, která ilustrují použití uložených procedur.</span><span class="sxs-lookup"><span data-stu-id="06ce4-124">Includes links to topics that illustrate how to use stored procedures.</span></span>  
  
 [<span data-ttu-id="06ce4-125">Úvod do LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="06ce4-125">Introduction to LINQ (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/index.md)  
 <span data-ttu-id="06ce4-126">Obsahuje prostředky, které vám pomohou začít se učit o LINQ na SQL pomocí jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="06ce4-126">Provides resources to help you begin to learn about LINQ to SQL using C#.</span></span>

 [<span data-ttu-id="06ce4-127">Úvod do LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06ce4-127">Introduction to LINQ (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)  
 <span data-ttu-id="06ce4-128">Obsahuje prostředky, které vám pomohou začít se učit o LINQ na SQL pomocí jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="06ce4-128">Provides resources to help you begin to learn about LINQ to SQL using Visual Basic.</span></span>
