---
title: Průvodce programováním
ms.date: 03/30/2017
ms.assetid: ed1012d4-3ff2-4877-af27-93125c4180ea
ms.openlocfilehash: c63fbedc1cf7484943614c50e7dd7554a2ddea0e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742936"
---
# <a name="programming-guide"></a><span data-ttu-id="e4627-102">Průvodce programováním</span><span class="sxs-lookup"><span data-stu-id="e4627-102">Programming Guide</span></span>
<span data-ttu-id="e4627-103">Tato část obsahuje informace o tom, jak vytvořit a používat vaše [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objektový model.</span><span class="sxs-lookup"><span data-stu-id="e4627-103">This section contains information about how to create and use your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="e4627-104">Pokud používáte Visual Studio, můžete také použít Návrhář relací objektů provádět spoustu těchto stejných úkolů.</span><span class="sxs-lookup"><span data-stu-id="e4627-104">If you are using Visual Studio, you can also use the Object Relational Designer to perform many of these same tasks.</span></span>  
  
 <span data-ttu-id="e4627-105">Můžete také prohledat Microsoft Docs pro specifické problémy a se můžete zapojit [LINQ fórum](https://go.microsoft.com/fwlink/?LinkId=76488), kde můžete diskutovat o složitějších tématech podrobně s odborníky.</span><span class="sxs-lookup"><span data-stu-id="e4627-105">You can also search Microsoft Docs for specific issues, and you can participate in the [LINQ Forum](https://go.microsoft.com/fwlink/?LinkId=76488), where you can discuss more complex topics in detail with experts.</span></span> <span data-ttu-id="e4627-106">Nakonec [technologie LINQ to SQL: .NET Language-Integrated dotazu pro relační Data](https://go.microsoft.com/fwlink/?LinkId=93205) dokument white paper o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technologie, s příklady kódu jazyka Visual Basic a C#.</span><span class="sxs-lookup"><span data-stu-id="e4627-106">Finally, the [LINQ to SQL: .NET Language-Integrated Query for Relational Data](https://go.microsoft.com/fwlink/?LinkId=93205) white paper details [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology, complete with Visual Basic and C# code examples.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e4627-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="e4627-107">In This Section</span></span>  
 [<span data-ttu-id="e4627-108">Vytvoření objektového modelu</span><span class="sxs-lookup"><span data-stu-id="e4627-108">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 <span data-ttu-id="e4627-109">Popisuje, jak generovat objektový model.</span><span class="sxs-lookup"><span data-stu-id="e4627-109">Describes how to generate an object model.</span></span>  
  
 [<span data-ttu-id="e4627-110">Komunikace s databází</span><span class="sxs-lookup"><span data-stu-id="e4627-110">Communicating with the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)  
 <span data-ttu-id="e4627-111">Popisuje způsob použití <xref:System.Data.Linq.DataContext> objektu jako kanál k databázi.</span><span class="sxs-lookup"><span data-stu-id="e4627-111">Describes how to use a <xref:System.Data.Linq.DataContext> object as a conduit to the database.</span></span>  
  
 [<span data-ttu-id="e4627-112">Dotazování na databázi</span><span class="sxs-lookup"><span data-stu-id="e4627-112">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)  
 <span data-ttu-id="e4627-113">Popisuje, jak k provádění dotazů v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]a poskytuje mnoho příkladů.</span><span class="sxs-lookup"><span data-stu-id="e4627-113">Describes how to execute queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], and provides many examples.</span></span>  
  
 [<span data-ttu-id="e4627-114">Vytvoření a odeslání změn dat</span><span class="sxs-lookup"><span data-stu-id="e4627-114">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 <span data-ttu-id="e4627-115">Popisuje, jak se mění data v databázi.</span><span class="sxs-lookup"><span data-stu-id="e4627-115">Describes how change data in the database.</span></span>  
  
 [<span data-ttu-id="e4627-116">Podpora ladění</span><span class="sxs-lookup"><span data-stu-id="e4627-116">Debugging Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)  
 <span data-ttu-id="e4627-117">Popisuje podporu pro ladění k dispozici [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projekty.</span><span class="sxs-lookup"><span data-stu-id="e4627-117">Describes the support available for debugging [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects.</span></span>  
  
 [<span data-ttu-id="e4627-118">Základní informace</span><span class="sxs-lookup"><span data-stu-id="e4627-118">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 <span data-ttu-id="e4627-119">Zahrnuje další položky, jako je například řešení konfliktů souběžnosti, vytvoření nových databází a navíc pro pokročilejší uživatele.</span><span class="sxs-lookup"><span data-stu-id="e4627-119">Includes additional items, such as concurrency conflict resolution, creating new databases, and more, for more advanced users.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e4627-120">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="e4627-120">Related Sections</span></span>  
 [<span data-ttu-id="e4627-121">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="e4627-121">LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 <span data-ttu-id="e4627-122">Obsahuje odkazy na témata, která popisují [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technologie a předvedení funkcí.</span><span class="sxs-lookup"><span data-stu-id="e4627-122">Provides links to topics that explain the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology and demonstrate features.</span></span>  
  
 [<span data-ttu-id="e4627-123">Uložené procedury</span><span class="sxs-lookup"><span data-stu-id="e4627-123">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)  
 <span data-ttu-id="e4627-124">Obsahuje odkazy na témata, která ukazují, jak pomocí uložených procedur.</span><span class="sxs-lookup"><span data-stu-id="e4627-124">Includes links to topics that illustrate how to use stored procedures.</span></span>  
  
 [<span data-ttu-id="e4627-125">Úvod do LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="e4627-125">Introduction to LINQ (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/index.md)  
 <span data-ttu-id="e4627-126">Obsahuje materiály, které umožňují učit o LINQ na SQL a příkazu C#.</span><span class="sxs-lookup"><span data-stu-id="e4627-126">Provides resources to help you begin to learn about LINQ to SQL using C#.</span></span>

 [<span data-ttu-id="e4627-127">Úvod do LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e4627-127">Introduction to LINQ (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)  
 <span data-ttu-id="e4627-128">Obsahuje materiály, které umožňují učit o LINQ to SQL s použitím jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e4627-128">Provides resources to help you begin to learn about LINQ to SQL using Visual Basic.</span></span>
