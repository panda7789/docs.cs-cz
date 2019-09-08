---
title: Průvodce programováním
ms.date: 03/30/2017
ms.assetid: ed1012d4-3ff2-4877-af27-93125c4180ea
ms.openlocfilehash: c33c7749599de0450a9f969e5802485d154a61e1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781252"
---
# <a name="programming-guide"></a><span data-ttu-id="5dde2-102">Průvodce programováním</span><span class="sxs-lookup"><span data-stu-id="5dde2-102">Programming Guide</span></span>
<span data-ttu-id="5dde2-103">Tato část obsahuje informace o tom, jak vytvořit a použít [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objektový model.</span><span class="sxs-lookup"><span data-stu-id="5dde2-103">This section contains information about how to create and use your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="5dde2-104">Pokud používáte sadu Visual Studio, můžete také použít Návrhář relací objektů k provedení mnoha stejných úloh.</span><span class="sxs-lookup"><span data-stu-id="5dde2-104">If you are using Visual Studio, you can also use the Object Relational Designer to perform many of these same tasks.</span></span>  
  
 <span data-ttu-id="5dde2-105">Můžete také vyhledat konkrétní problémy v Microsoft Docs a můžete se zúčastnit [fóra LINQ](https://go.microsoft.com/fwlink/?LinkId=76488), kde můžete diskutovat o složitější témata podrobněji s odborníky.</span><span class="sxs-lookup"><span data-stu-id="5dde2-105">You can also search Microsoft Docs for specific issues, and you can participate in the [LINQ Forum](https://go.microsoft.com/fwlink/?LinkId=76488), where you can discuss more complex topics in detail with experts.</span></span> <span data-ttu-id="5dde2-106">Nakonec [LINQ to SQL: dotaz integrovaný na jazyku .NET pro](https://go.microsoft.com/fwlink/?LinkId=93205) technologii podrobného dokumentu s podrobnostmi o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] relačních datech, který se dokončí s příklady Visual Basic a C# kódu.</span><span class="sxs-lookup"><span data-stu-id="5dde2-106">Finally, the [LINQ to SQL: .NET Language-Integrated Query for Relational Data](https://go.microsoft.com/fwlink/?LinkId=93205) white paper details [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology, complete with Visual Basic and C# code examples.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5dde2-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="5dde2-107">In This Section</span></span>  
 [<span data-ttu-id="5dde2-108">Vytvoření objektového modelu</span><span class="sxs-lookup"><span data-stu-id="5dde2-108">Creating the Object Model</span></span>](creating-the-object-model.md)  
 <span data-ttu-id="5dde2-109">Popisuje, jak vygenerovat objektový model.</span><span class="sxs-lookup"><span data-stu-id="5dde2-109">Describes how to generate an object model.</span></span>  
  
 [<span data-ttu-id="5dde2-110">Komunikace s databází</span><span class="sxs-lookup"><span data-stu-id="5dde2-110">Communicating with the Database</span></span>](communicating-with-the-database.md)  
 <span data-ttu-id="5dde2-111">Popisuje způsob použití <xref:System.Data.Linq.DataContext> objektu jako trubky pro databázi.</span><span class="sxs-lookup"><span data-stu-id="5dde2-111">Describes how to use a <xref:System.Data.Linq.DataContext> object as a conduit to the database.</span></span>  
  
 [<span data-ttu-id="5dde2-112">Dotazování na databázi</span><span class="sxs-lookup"><span data-stu-id="5dde2-112">Querying the Database</span></span>](querying-the-database.md)  
 <span data-ttu-id="5dde2-113">Popisuje, jak spustit dotazy v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nástroji a poskytuje mnoho příkladů.</span><span class="sxs-lookup"><span data-stu-id="5dde2-113">Describes how to execute queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], and provides many examples.</span></span>  
  
 [<span data-ttu-id="5dde2-114">Vytvoření a odeslání změn dat</span><span class="sxs-lookup"><span data-stu-id="5dde2-114">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)  
 <span data-ttu-id="5dde2-115">Popisuje, jak změnit data v databázi.</span><span class="sxs-lookup"><span data-stu-id="5dde2-115">Describes how change data in the database.</span></span>  
  
 [<span data-ttu-id="5dde2-116">Podpora ladění</span><span class="sxs-lookup"><span data-stu-id="5dde2-116">Debugging Support</span></span>](debugging-support.md)  
 <span data-ttu-id="5dde2-117">Popisuje podporu, která je k [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dispozici pro ladění projektů.</span><span class="sxs-lookup"><span data-stu-id="5dde2-117">Describes the support available for debugging [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects.</span></span>  
  
 [<span data-ttu-id="5dde2-118">Základní informace</span><span class="sxs-lookup"><span data-stu-id="5dde2-118">Background Information</span></span>](background-information.md)  
 <span data-ttu-id="5dde2-119">Zahrnuje další položky, jako je například řešení konfliktů souběžnosti, vytváření nových databází a další, pro pokročilejší uživatele.</span><span class="sxs-lookup"><span data-stu-id="5dde2-119">Includes additional items, such as concurrency conflict resolution, creating new databases, and more, for more advanced users.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5dde2-120">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="5dde2-120">Related Sections</span></span>  
 [<span data-ttu-id="5dde2-121">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="5dde2-121">LINQ to SQL</span></span>](index.md)  
 <span data-ttu-id="5dde2-122">Obsahuje odkazy na témata, která vysvětlují [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technologii a předvádí funkce.</span><span class="sxs-lookup"><span data-stu-id="5dde2-122">Provides links to topics that explain the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology and demonstrate features.</span></span>  
  
 [<span data-ttu-id="5dde2-123">Uložené procedury</span><span class="sxs-lookup"><span data-stu-id="5dde2-123">Stored Procedures</span></span>](stored-procedures.md)  
 <span data-ttu-id="5dde2-124">Obsahuje odkazy na témata, která ukazují, jak používat uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="5dde2-124">Includes links to topics that illustrate how to use stored procedures.</span></span>  
  
 [<span data-ttu-id="5dde2-125">Úvod do LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="5dde2-125">Introduction to LINQ (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/index.md)  
 <span data-ttu-id="5dde2-126">Poskytuje materiály, které vám pomůžou začít se dozvědět o C#LINQ to SQL pomocí.</span><span class="sxs-lookup"><span data-stu-id="5dde2-126">Provides resources to help you begin to learn about LINQ to SQL using C#.</span></span>

 [<span data-ttu-id="5dde2-127">Úvod do LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5dde2-127">Introduction to LINQ (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)  
 <span data-ttu-id="5dde2-128">Poskytuje materiály, které vám pomůžou začít se dozvědět o LINQ to SQL pomocí Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5dde2-128">Provides resources to help you begin to learn about LINQ to SQL using Visual Basic.</span></span>
