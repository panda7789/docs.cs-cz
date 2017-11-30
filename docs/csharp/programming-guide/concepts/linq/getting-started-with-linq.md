---
title: "Začínáme s dotazy LINQ v jazyce C#"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- LINQ [C#]
- queries [LINQ in C#]
- LINQ, C#
- queries [LINQ], LINQ in C#
ms.assetid: b8700c1f-05c9-4380-b6eb-e34c4da38e54
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1e8f520f1fa5146f68bae0b634f8b2b1d5d875d9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="getting-started-with-linq-in-c"></a><span data-ttu-id="7c866-102">Začínáme s dotazy LINQ v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="7c866-102">Getting Started with LINQ in C#</span></span>
<span data-ttu-id="7c866-103">Tato část obsahuje základní informace, které vám pomohou pochopit, zbytek LINQ dokumentace a ukázky.</span><span class="sxs-lookup"><span data-stu-id="7c866-103">This section contains basic background information that will help you understand the rest of the LINQ documentation and samples.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7c866-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="7c866-104">In This Section</span></span>  
 [<span data-ttu-id="7c866-105">Úvod do dotazů LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="7c866-105">Introduction to LINQ Queries (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 <span data-ttu-id="7c866-106">Popisuje základní operace dotazů LINQ tří částí, které jsou společné pro všechny jazyky a datových zdrojů.</span><span class="sxs-lookup"><span data-stu-id="7c866-106">Describes the three parts of the basic LINQ query operation that are common across all languages and data sources.</span></span>  
  
 [<span data-ttu-id="7c866-107">LINQ a obecné typy (C#)</span><span class="sxs-lookup"><span data-stu-id="7c866-107">LINQ and Generic Types (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-generic-types.md)  
 <span data-ttu-id="7c866-108">Poskytuje stručný úvod do obecných typů, jak se používají v technologii LINQ.</span><span class="sxs-lookup"><span data-stu-id="7c866-108">Provides a brief introduction to generic types as they are used in LINQ.</span></span>  
  
 [<span data-ttu-id="7c866-109">Základní operace dotazů LINQ</span><span class="sxs-lookup"><span data-stu-id="7c866-109">Basic LINQ Query Operations</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-linq-query-operations.md)  
 <span data-ttu-id="7c866-110">Popisuje nejběžnějších typů operace dotazů a jak jsou vyjádřeny v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="7c866-110">Describes the most common types of query operations and how they are expressed in C#.</span></span>  
  
 [<span data-ttu-id="7c866-111">Transformace dat pomocí LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="7c866-111">Data Transformations with LINQ (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)  
 <span data-ttu-id="7c866-112">Popisuje různé způsoby, můžete převést data načtená v dotazech.</span><span class="sxs-lookup"><span data-stu-id="7c866-112">Describes the various ways that you can transform data retrieved in queries.</span></span>  
  
 [<span data-ttu-id="7c866-113">Vztahy typů v operacích dotazu LINQ</span><span class="sxs-lookup"><span data-stu-id="7c866-113">Type Relationships in LINQ Query Operations</span></span>](../../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)  
 <span data-ttu-id="7c866-114">Popisuje, jak jsou typy zachovaná nebo transformovat na tři části operace dotazů LINQ</span><span class="sxs-lookup"><span data-stu-id="7c866-114">Describes how types are preserved and/or transformed in the three parts of a LINQ query operation</span></span>  
  
 [<span data-ttu-id="7c866-115">Syntaxe využívající dotazy a syntaxe využívající metody v LINQ</span><span class="sxs-lookup"><span data-stu-id="7c866-115">Query Syntax and Method Syntax in LINQ</span></span>](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)  
 <span data-ttu-id="7c866-116">Porovná syntaxi dotazu a syntaxe využívající metody jako dva způsoby, jak express dotaz LINQ.</span><span class="sxs-lookup"><span data-stu-id="7c866-116">Compares method syntax and query syntax as two ways to express a LINQ query.</span></span>  
  
 [<span data-ttu-id="7c866-117">Funkce jazyka C# podporující LINQ</span><span class="sxs-lookup"><span data-stu-id="7c866-117">C# Features That Support LINQ</span></span>](../../../../csharp/programming-guide/concepts/linq/features-that-support-linq.md)  
 <span data-ttu-id="7c866-118">Popisuje jazykové konstrukty přidali v C# 3.0, které podporují LINQ.</span><span class="sxs-lookup"><span data-stu-id="7c866-118">Describes the language constructs added in C# 3.0 that support LINQ.</span></span>  
  
 [<span data-ttu-id="7c866-119">Návod: Zápis dotazů v C#</span><span class="sxs-lookup"><span data-stu-id="7c866-119">Walkthrough: Writing Queries in C#</span></span>](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)  
 <span data-ttu-id="7c866-120">Podrobné pokyny pro vytvoření projektu LINQ v C#, přidáním jednoduché datové zdroje a provádění některých operací základní dotazu.</span><span class="sxs-lookup"><span data-stu-id="7c866-120">Step-by-step instructions for creating a C# LINQ project, adding a simple data source, and performing some basic query operations.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7c866-121">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="7c866-121">Related Sections</span></span>  
 [<span data-ttu-id="7c866-122">Language-Integrated Query (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="7c866-122">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)  
 <span data-ttu-id="7c866-123">Obsahuje odkazy na témata, která popisují technologie LINQ.</span><span class="sxs-lookup"><span data-stu-id="7c866-123">Provides links to topics that explain the LINQ technologies.</span></span>  
  
 [<span data-ttu-id="7c866-124">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="7c866-124">LINQ Query Expressions</span></span>](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
 <span data-ttu-id="7c866-125">Obsahuje přehled dotazů LINQ a poskytuje odkazy na další zdroje informací.</span><span class="sxs-lookup"><span data-stu-id="7c866-125">Includes an overview of queries in LINQ and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="7c866-126">Visual Studio – sada IDE a nástrojů podpory pro výrazy LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="7c866-126">Visual Studio IDE and Tools Support for LINQ (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/visual-studio-ide-and-tools-support-for-linq.md)  
 <span data-ttu-id="7c866-127">Popisuje nástroje dostupné v prostředí Visual Studio pro návrh, kódování a ladění aplikace s povolenými LINQ.</span><span class="sxs-lookup"><span data-stu-id="7c866-127">Describes tools available in the Visual Studio environment for designing, coding, and debugging LINQ-enabled application.</span></span>  
  
 [<span data-ttu-id="7c866-128">Přehled standardních operátorů dotazu (C#)</span><span class="sxs-lookup"><span data-stu-id="7c866-128">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 <span data-ttu-id="7c866-129">Představuje standardní metody používané v technologii LINQ.</span><span class="sxs-lookup"><span data-stu-id="7c866-129">Introduces the standard methods used in LINQ.</span></span>  
  
 [<span data-ttu-id="7c866-130">Začínáme s dotazy LINQ v jazyku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7c866-130">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 <span data-ttu-id="7c866-131">Obsahuje odkazy na témata o použití LINQ v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7c866-131">Provides links to topics about using LINQ with Visual Basic.</span></span>
