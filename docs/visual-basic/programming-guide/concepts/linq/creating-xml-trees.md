---
title: Vytváření stromů XML (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e86ba12b-17de-4579-81bb-66322b84cfbe
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 08efc9a9b519d2b56f8503e050b9332be580d124
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="creating-xml-trees-visual-basic"></a><span data-ttu-id="f2b84-102">Vytváření stromů XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2b84-102">Creating XML Trees (Visual Basic)</span></span>
<span data-ttu-id="f2b84-103">Jeden z nejčastějších úloh XML je vytváření strom XML.</span><span class="sxs-lookup"><span data-stu-id="f2b84-103">One of the most common XML tasks is constructing an XML tree.</span></span> <span data-ttu-id="f2b84-104">Tato část popisuje několik způsobů, jak je vytvořte.</span><span class="sxs-lookup"><span data-stu-id="f2b84-104">This section describes several ways to create them.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f2b84-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="f2b84-105">In This Section</span></span>  
  
|<span data-ttu-id="f2b84-106">Téma</span><span class="sxs-lookup"><span data-stu-id="f2b84-106">Topic</span></span>|<span data-ttu-id="f2b84-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f2b84-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="f2b84-108">Funkční konstrukce (technologie LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2b84-108">Functional Construction (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md)|<span data-ttu-id="f2b84-109">Poskytuje přehled funkční konstrukce v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f2b84-109">Provides an overview of functional construction in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span> <span data-ttu-id="f2b84-110">Funkční konstrukce umožňuje vytvořit nebo její část stromu XML v jediném příkazu.</span><span class="sxs-lookup"><span data-stu-id="f2b84-110">Functional construction enables you to create all or part of your XML tree in a single statement.</span></span> <span data-ttu-id="f2b84-111">Toto téma také ukazuje, jak pro vložení dotazy při sestavování ve stromu XML.</span><span class="sxs-lookup"><span data-stu-id="f2b84-111">This topic also shows how to embed queries when constructing an XML tree.</span></span>|  
|[<span data-ttu-id="f2b84-112">Úvod do literálů XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f2b84-112">Introduction to XML Literals in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-xml-literals.md)|<span data-ttu-id="f2b84-113">Poskytuje rychlý úvod do vytváření stromů pomocí literálů XML v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f2b84-113">Provides a quick introduction to creating trees in Visual Basic by using XML literals.</span></span> <span data-ttu-id="f2b84-114">Toto téma obsahuje odkazy na dokumentaci jazyka Visual Basic literálů XML.</span><span class="sxs-lookup"><span data-stu-id="f2b84-114">This topic includes links to the Visual Basic documentation of XML literals.</span></span>|  
|[<span data-ttu-id="f2b84-115">Klonování vs. Připojení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2b84-115">Cloning vs. Attaching (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/cloning-vs-attaching.md)|<span data-ttu-id="f2b84-116">Ukazuje rozdíl mezi přidání uzlů z existující stromu XML (uzly jsou klonovat a potom přidat) a přidání uzlů žádný nadřazený (jsou jednoduše připojené).</span><span class="sxs-lookup"><span data-stu-id="f2b84-116">Demonstrates the difference between adding nodes from an existing XML tree (nodes are cloned and then added) and adding nodes with no parent (they are simply attached).</span></span>|  
|[<span data-ttu-id="f2b84-117">Analýza kódu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2b84-117">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)|<span data-ttu-id="f2b84-118">Ukazuje, jak analyzovat soubor XML z různých zdrojů.</span><span class="sxs-lookup"><span data-stu-id="f2b84-118">Shows how to parse XML from a variety of sources.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="f2b84-119"> tvoří vrstvu nad <xref:System.Xml.XmlReader>, který se používá k analyzovat kód XML.</span><span class="sxs-lookup"><span data-stu-id="f2b84-119"> is layered on top of <xref:System.Xml.XmlReader>, which is used to parse the XML.</span></span>|  
|[<span data-ttu-id="f2b84-120">Postupy: naplnění strom XML s XmlWriter (technologie LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2b84-120">How to: Populate an XML Tree with an XmlWriter (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml.md)|<span data-ttu-id="f2b84-121">Ukazuje, jak k naplnění strom XML pomocí <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="f2b84-121">Shows how to populate an XML tree by using an <xref:System.Xml.XmlWriter>.</span></span>|  
|[<span data-ttu-id="f2b84-122">Postupy: ověření pomocí XSD (technologie LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2b84-122">How to: Validate Using XSD (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md)|<span data-ttu-id="f2b84-123">Ukazuje, jak ověřit strom XML pomocí XSD.</span><span class="sxs-lookup"><span data-stu-id="f2b84-123">Shows how to validate an XML tree using XSD.</span></span>|  
|[<span data-ttu-id="f2b84-124">Platný obsah objektů XElement a XDocument</span><span class="sxs-lookup"><span data-stu-id="f2b84-124">Valid Content of XElement and XDocument Objects</span></span>](../../../../visual-basic/programming-guide/concepts/linq/valid-content-of-xelement-and-xdocument-objects.md)|<span data-ttu-id="f2b84-125">Popisuje platné argumenty, které lze předat konstruktorů a metod, které slouží k přidání obsahu do elementů a dokumenty.</span><span class="sxs-lookup"><span data-stu-id="f2b84-125">Describes the valid arguments that can be passed to the constructors and methods that are used to add content to elements and documents.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f2b84-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="f2b84-126">See Also</span></span>  
 [<span data-ttu-id="f2b84-127">Průvodce programováním (technologie LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2b84-127">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
