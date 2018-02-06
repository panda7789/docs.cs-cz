---
title: 'Kurz: Manipulace se obsah v dokumentu WordprocessingML (C#)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: bc9815f8-13d2-4f50-a4d1-b1c0d50d37b3
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: dca728cf48c6af6437beb43bcb6a8c8b7283d639
ms.sourcegitcommit: 099aa20d9b6450d1b7452d782a55771a6ad8ff35
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/05/2018
---
# <a name="tutorial-manipulating-content-in-a-wordprocessingml-document-c"></a><span data-ttu-id="137a3-102">Kurz: Manipulace se obsah v dokumentu WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="137a3-102">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>
<span data-ttu-id="137a3-103">Tento kurz ukazuje, jak se má použít funkční transformational přístup a LINQ to XML k manipulaci s dokumenty XML.</span><span class="sxs-lookup"><span data-stu-id="137a3-103">This tutorial shows how to apply the functional transformational approach and LINQ to XML to manipulate XML documents.</span></span> <span data-ttu-id="137a3-104">Příklady C# dotaz a manipulovat s informacemi v dokumentech Office Open XML WordprocessingML, které jsou uloženy v aplikaci Microsoft Word.</span><span class="sxs-lookup"><span data-stu-id="137a3-104">The C# examples query and manipulate information in Office Open XML WordprocessingML documents that are saved by Microsoft Word.</span></span>  
  
 <span data-ttu-id="137a3-105">Další informace najdete v tématu [Úvod do WordprocessingML](http://ericwhite.com/blog/introduction-to-wordprocessingml-series/).</span><span class="sxs-lookup"><span data-stu-id="137a3-105">For more information, see [Introduction to WordprocessingML](http://ericwhite.com/blog/introduction-to-wordprocessingml-series/).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="137a3-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="137a3-106">In This Section</span></span>  
  
|<span data-ttu-id="137a3-107">Téma</span><span class="sxs-lookup"><span data-stu-id="137a3-107">Topic</span></span>|<span data-ttu-id="137a3-108">Popis</span><span class="sxs-lookup"><span data-stu-id="137a3-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="137a3-109">Tvar WordprocessingML dokumentů (C#)</span><span class="sxs-lookup"><span data-stu-id="137a3-109">Shape of WordprocessingML Documents (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/shape-of-wordprocessingml-documents.md)|<span data-ttu-id="137a3-110">Poskytuje rychlý vysvětlení podrobnosti WordprocessingML dokumentu.</span><span class="sxs-lookup"><span data-stu-id="137a3-110">Provides a quick explanation of details of a WordprocessingML document.</span></span>|  
|[<span data-ttu-id="137a3-111">Vytvoření zdrojového dokumentu Office Open XML (C#)</span><span class="sxs-lookup"><span data-stu-id="137a3-111">Creating the Source Office Open XML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md)|<span data-ttu-id="137a3-112">Poskytuje podrobné pokyny k vytvoření zdrojový dokument pro dotazy v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="137a3-112">Provides step-by-step instructions to create the source document for queries in this tutorial.</span></span>|  
|[<span data-ttu-id="137a3-113">Hledání výchozí styl odstavce (C#)</span><span class="sxs-lookup"><span data-stu-id="137a3-113">Finding the Default Paragraph Style (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/finding-the-default-paragraph-style.md)|<span data-ttu-id="137a3-114">Zobrazí dotaz, který najde název výchozí styl pro dokument.</span><span class="sxs-lookup"><span data-stu-id="137a3-114">Shows a query to find the name of the default style for a document.</span></span>|  
|[<span data-ttu-id="137a3-115">Načítání odstavců a jejich styly (C#)</span><span class="sxs-lookup"><span data-stu-id="137a3-115">Retrieving the Paragraphs and Their Styles (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md)|<span data-ttu-id="137a3-116">Zobrazí dotaz, který načte kolekci odstavců dokumentu.</span><span class="sxs-lookup"><span data-stu-id="137a3-116">Shows a query that retrieves a collection of the paragraphs of a document.</span></span>|  
|[<span data-ttu-id="137a3-117">Načítání textu odstavců (C#)</span><span class="sxs-lookup"><span data-stu-id="137a3-117">Retrieving the Text of the Paragraphs (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md)|<span data-ttu-id="137a3-118">Rozšiřuje předchozí dotaz pro načtení každý odstavec.</span><span class="sxs-lookup"><span data-stu-id="137a3-118">Augments the previous query to retrieve the text of each paragraph.</span></span>|  
|[<span data-ttu-id="137a3-119">Refaktoring pomocí metody rozšíření (C#)</span><span class="sxs-lookup"><span data-stu-id="137a3-119">Refactoring Using an Extension Method (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-using-an-extension-method.md)|<span data-ttu-id="137a3-120">Zjednodušuje kódu refaktoringu pomocí metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="137a3-120">Simplifies the code by refactoring using an extension method.</span></span>|  
|[<span data-ttu-id="137a3-121">Refaktoring pomocí čistý funkce (C#)</span><span class="sxs-lookup"><span data-stu-id="137a3-121">Refactoring Using a Pure Function (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-using-a-pure-function.md)|<span data-ttu-id="137a3-122">Další zjednodušuje kód refaktoring pomocí čistou funkci.</span><span class="sxs-lookup"><span data-stu-id="137a3-122">Further simplifies the code by refactoring using a pure function.</span></span>|  
|[<span data-ttu-id="137a3-123">Promítnutí kód XML v různých obrazce (C#)</span><span class="sxs-lookup"><span data-stu-id="137a3-123">Projecting XML in a Different Shape (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projecting-xml-in-a-different-shape.md)|<span data-ttu-id="137a3-124">Dokončení transformaci XML plánování XML v různých obrazce než původního dokumentu.</span><span class="sxs-lookup"><span data-stu-id="137a3-124">Completes an XML transformation by projecting XML in a different shape than the original document.</span></span>|  
|[<span data-ttu-id="137a3-125">Vyhledávání textu v dokumentech aplikace Word (C#)</span><span class="sxs-lookup"><span data-stu-id="137a3-125">Finding Text in Word Documents (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/finding-text-in-word-documents.md)|<span data-ttu-id="137a3-126">Předchozí dotazy se používá k nalezení zadaný textový řetězec v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="137a3-126">Uses the previous queries to find a specified text string in a document.</span></span>|  
|[<span data-ttu-id="137a3-127">Podrobnosti o Office otevřít dokumenty WordprocessingML XML (C#)</span><span class="sxs-lookup"><span data-stu-id="137a3-127">Details of Office Open XML WordprocessingML Documents (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md)|<span data-ttu-id="137a3-128">Poskytuje některé podrobnosti dokumentů Office Open XML WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="137a3-128">Provides some details of Office Open XML WordprocessingML documents.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="137a3-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="137a3-129">See Also</span></span>  
 [<span data-ttu-id="137a3-130">Čistý funkční transformace XML (C#)</span><span class="sxs-lookup"><span data-stu-id="137a3-130">Pure Functional Transformations of XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)  
 [<span data-ttu-id="137a3-131">Úvod do čistého funkční transformace (C#)</span><span class="sxs-lookup"><span data-stu-id="137a3-131">Introduction to Pure Functional Transformations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
