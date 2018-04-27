---
title: Průvodce programováním
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed1012d4-3ff2-4877-af27-93125c4180ea
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 703f10466755ddea5a0117a3413374613e178346
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="programming-guide"></a><span data-ttu-id="13b64-102">Průvodce programováním</span><span class="sxs-lookup"><span data-stu-id="13b64-102">Programming Guide</span></span>
<span data-ttu-id="13b64-103">Tato část obsahuje informace o tom, jak vytvořit a používat vaše [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objektový model.</span><span class="sxs-lookup"><span data-stu-id="13b64-103">This section contains information about how to create and use your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="13b64-104">Pokud používáte Visual Studio, můžete také použít [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] mnoho z těchto úloh.</span><span class="sxs-lookup"><span data-stu-id="13b64-104">If you are using Visual Studio, you can also use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to perform many of these same tasks.</span></span>  
  
 <span data-ttu-id="13b64-105">Můžete také prohledat Microsoft Docs pro specifické problémy a se můžete zapojit [LINQ fórum](http://go.microsoft.com/fwlink/?LinkId=76488), kde můžete složitější témata podrobně popisují s odborníky.</span><span class="sxs-lookup"><span data-stu-id="13b64-105">You can also search Microsoft Docs for specific issues, and you can participate in the [LINQ Forum](http://go.microsoft.com/fwlink/?LinkId=76488), where you can discuss more complex topics in detail with experts.</span></span> <span data-ttu-id="13b64-106">Nakonec [technologie LINQ to SQL: .NET Language-Integrated dotaz na relační Data](http://go.microsoft.com/fwlink/?LinkId=93205) dokumentu white paper podrobnosti [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technologie kompletní s příklady kódu jazyka Visual Basic a C#.</span><span class="sxs-lookup"><span data-stu-id="13b64-106">Finally, the [LINQ to SQL: .NET Language-Integrated Query for Relational Data](http://go.microsoft.com/fwlink/?LinkId=93205) white paper details [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology, complete with Visual Basic and C# code examples.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="13b64-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="13b64-107">In This Section</span></span>  
 [<span data-ttu-id="13b64-108">Vytvoření objektového modelu</span><span class="sxs-lookup"><span data-stu-id="13b64-108">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 <span data-ttu-id="13b64-109">Popisuje, jak vygenerovat objektový model.</span><span class="sxs-lookup"><span data-stu-id="13b64-109">Describes how to generate an object model.</span></span>  
  
 [<span data-ttu-id="13b64-110">Komunikace s databází</span><span class="sxs-lookup"><span data-stu-id="13b64-110">Communicating with the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)  
 <span data-ttu-id="13b64-111">Popisuje způsob použití <xref:System.Data.Linq.DataContext> objektu jako kanál do databáze.</span><span class="sxs-lookup"><span data-stu-id="13b64-111">Describes how to use a <xref:System.Data.Linq.DataContext> object as a conduit to the database.</span></span>  
  
 [<span data-ttu-id="13b64-112">Dotazování na databázi</span><span class="sxs-lookup"><span data-stu-id="13b64-112">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)  
 <span data-ttu-id="13b64-113">Popisuje, jak na provedení dotazů v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]a obsahuje mnoho příklady.</span><span class="sxs-lookup"><span data-stu-id="13b64-113">Describes how to execute queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], and provides many examples.</span></span>  
  
 [<span data-ttu-id="13b64-114">Vytvoření a odeslání změn dat</span><span class="sxs-lookup"><span data-stu-id="13b64-114">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 <span data-ttu-id="13b64-115">Popisuje, jak změnit data v databázi.</span><span class="sxs-lookup"><span data-stu-id="13b64-115">Describes how change data in the database.</span></span>  
  
 [<span data-ttu-id="13b64-116">Podpora ladění</span><span class="sxs-lookup"><span data-stu-id="13b64-116">Debugging Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)  
 <span data-ttu-id="13b64-117">Popisuje podporu, které jsou k dispozici pro ladění [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projekty.</span><span class="sxs-lookup"><span data-stu-id="13b64-117">Describes the support available for debugging [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects.</span></span>  
  
 [<span data-ttu-id="13b64-118">Základní informace</span><span class="sxs-lookup"><span data-stu-id="13b64-118">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 <span data-ttu-id="13b64-119">Zahrnuje další položky, jako je například řešení konfliktů souběžnosti, vytváření nových databází a další, pro pokročilejší uživatele.</span><span class="sxs-lookup"><span data-stu-id="13b64-119">Includes additional items, such as concurrency conflict resolution, creating new databases, and more, for more advanced users.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="13b64-120">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="13b64-120">Related Sections</span></span>  
 [<span data-ttu-id="13b64-121">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="13b64-121">LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 <span data-ttu-id="13b64-122">Obsahuje odkazy na témata, které vysvětlují [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technologie a předvedení funkcí.</span><span class="sxs-lookup"><span data-stu-id="13b64-122">Provides links to topics that explain the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology and demonstrate features.</span></span>  
  
 [<span data-ttu-id="13b64-123">Uložené procedury</span><span class="sxs-lookup"><span data-stu-id="13b64-123">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)  
 <span data-ttu-id="13b64-124">Obsahuje odkazy na témata, která ukazují, jak pomocí uložených procedur.</span><span class="sxs-lookup"><span data-stu-id="13b64-124">Includes links to topics that illustrate how to use stored procedures.</span></span>  
  
 [<span data-ttu-id="13b64-125">Úvod do jazyka LINQ</span><span class="sxs-lookup"><span data-stu-id="13b64-125">Introduction to LINQ</span></span>](http://msdn.microsoft.com/library/24dddf19-12a0-4707-a4bc-eba4fa7f219e)  
 <span data-ttu-id="13b64-126">Obsahuje materiály, které vám pomohou při další informace o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="13b64-126">Provides resources to help you begin to learn about [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>
