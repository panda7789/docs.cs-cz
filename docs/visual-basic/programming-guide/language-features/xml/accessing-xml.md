---
title: "Přístup ke XML v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 79c7b8a94731e151a803a041d91dd1e240ddeb97
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="accessing-xml-in-visual-basic"></a><span data-ttu-id="4da06-102">Přístup ke XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4da06-102">Accessing XML in Visual Basic</span></span>
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="4da06-103">poskytuje vlastnosti osy XML pro přístup k informacím a navigace [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] struktury.</span><span class="sxs-lookup"><span data-stu-id="4da06-103"> provides XML axis properties for accessing and navigating [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] structures.</span></span> <span data-ttu-id="4da06-104">Tyto vlastnosti pomocí speciální syntaxe vám umožní přístup zadáním názvů XML elementů a atributů.</span><span class="sxs-lookup"><span data-stu-id="4da06-104">These properties use a special syntax to enable you to access elements and attributes by specifying the XML names.</span></span>  
  
 <span data-ttu-id="4da06-105">Následující tabulka uvádí funkce jazyka, které vám umožní přístup k XML elementů a atributů v [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4da06-105">The following table lists the language features that enable you to access XML elements and attributes in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
### <a name="xml-axis-properties"></a><span data-ttu-id="4da06-106">Vlastnosti osy XML</span><span class="sxs-lookup"><span data-stu-id="4da06-106">XML Axis Properties</span></span>  
  
|<span data-ttu-id="4da06-107">Popis vlastnosti</span><span class="sxs-lookup"><span data-stu-id="4da06-107">Property description</span></span>|<span data-ttu-id="4da06-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="4da06-108">Example</span></span>|<span data-ttu-id="4da06-109">Popis</span><span class="sxs-lookup"><span data-stu-id="4da06-109">Description</span></span>|  
|--------------------------|-------------|-----------------|  
|<span data-ttu-id="4da06-110">*podřízené osy*</span><span class="sxs-lookup"><span data-stu-id="4da06-110">*child axis*</span></span>|`contact.<phone>`|<span data-ttu-id="4da06-111">Získá všechny `phone` prvky, které jsou podřízených elementů `contact` elementu.</span><span class="sxs-lookup"><span data-stu-id="4da06-111">Gets all `phone` elements that are child elements of the `contact` element.</span></span>|  
|<span data-ttu-id="4da06-112">*atribut osy*</span><span class="sxs-lookup"><span data-stu-id="4da06-112">*attribute axis*</span></span>|`phone.@type`|<span data-ttu-id="4da06-113">Získá všechny `type` atributy `phone` elementu.</span><span class="sxs-lookup"><span data-stu-id="4da06-113">Gets all `type` attributes of the `phone` element.</span></span>|  
|<span data-ttu-id="4da06-114">*Následnické osy*</span><span class="sxs-lookup"><span data-stu-id="4da06-114">*descendant axis*</span></span>|`contacts...<name>`|<span data-ttu-id="4da06-115">Získá všechny `name` prvky `contacts` elementu, bez ohledu na to, jak hluboko v hierarchii k nim dojde.</span><span class="sxs-lookup"><span data-stu-id="4da06-115">Gets all `name` elements of the `contacts` element, regardless of how deep in the hierarchy they occur.</span></span>|  
|<span data-ttu-id="4da06-116">*Indexovací modul rozšíření*</span><span class="sxs-lookup"><span data-stu-id="4da06-116">*extension indexer*</span></span>|`contacts...<name>(0)`|<span data-ttu-id="4da06-117">Získá první `name` element z pořadí.</span><span class="sxs-lookup"><span data-stu-id="4da06-117">Gets the first `name` element from the sequence.</span></span>|  
|<span data-ttu-id="4da06-118">*Hodnota*</span><span class="sxs-lookup"><span data-stu-id="4da06-118">*value*</span></span>|`contacts...<name>.Value`|<span data-ttu-id="4da06-119">Získá řetězcovou reprezentaci objektu první v pořadí, nebo `Nothing` Pokud sekvenci je prázdný.</span><span class="sxs-lookup"><span data-stu-id="4da06-119">Gets the string representation of the first object in the sequence, or `Nothing` if the sequence is empty.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="4da06-120">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="4da06-120">In This Section</span></span>  
 [<span data-ttu-id="4da06-121">Postupy: přístup k Následnickým elementům XML</span><span class="sxs-lookup"><span data-stu-id="4da06-121">How to: Access XML Descendant Elements</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)  
 <span data-ttu-id="4da06-122">Ukazuje, jak používat vlastnost osy nástupce pro přístup k všech elementů XML, které jsou obsažené v rámci zadaného elementu XML, které mají zadaný název.</span><span class="sxs-lookup"><span data-stu-id="4da06-122">Shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under a specified XML element.</span></span>  
  
 [<span data-ttu-id="4da06-123">Postupy: přístup k podřízeným elementům XML</span><span class="sxs-lookup"><span data-stu-id="4da06-123">How to: Access XML Child Elements</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-child-elements.md)  
 <span data-ttu-id="4da06-124">Ukazuje způsob použití podřízená osa – vlastnost přístup všech podřízených elementů XML, které mají zadaný název v elementu XML.</span><span class="sxs-lookup"><span data-stu-id="4da06-124">Shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="4da06-125">Postupy: přístup k atributům XML</span><span class="sxs-lookup"><span data-stu-id="4da06-125">How to: Access XML Attributes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-attributes.md)  
 <span data-ttu-id="4da06-126">Ukazuje, jak používat vlastnost osy atributu pro přístup k všechny atributy XML, které mají zadaný název v elementu XML.</span><span class="sxs-lookup"><span data-stu-id="4da06-126">Shows how to use an attribute axis property to access all XML attributes that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="4da06-127">Postupy: deklarace a používání předpon Namespace XML</span><span class="sxs-lookup"><span data-stu-id="4da06-127">How to: Declare and Use XML Namespace Prefixes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-declare-and-use-xml-namespace-prefixes.md)  
 <span data-ttu-id="4da06-128">Ukazuje, jak deklarovat předponu oboru názvů XML a použít ho k vytváření a přístup k elementům XML.</span><span class="sxs-lookup"><span data-stu-id="4da06-128">Shows how to declare an XML namespace prefix and use it to create and access XML elements.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4da06-129">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="4da06-129">Related Sections</span></span>  
 [<span data-ttu-id="4da06-130">Vlastnosti osy XML</span><span class="sxs-lookup"><span data-stu-id="4da06-130">XML Axis Properties</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 <span data-ttu-id="4da06-131">Obsahuje odkazy na oddíly, které popisují různé vlastnosti přístup XML.</span><span class="sxs-lookup"><span data-stu-id="4da06-131">Provides links to sections describing the various XML access properties.</span></span>  
  
 [<span data-ttu-id="4da06-132">Přehled technologie LINQ to XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4da06-132">Overview of LINQ to XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 <span data-ttu-id="4da06-133">Obsahuje úvod do používání [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4da06-133">Provides an introduction to using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>  
  
 [<span data-ttu-id="4da06-134">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4da06-134">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 <span data-ttu-id="4da06-135">Poskytuje úvod do používání literálů XML v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4da06-135">Provides an introduction to using XML literals in Visual Basic.</span></span>  
  
 [<span data-ttu-id="4da06-136">Zacházení s XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4da06-136">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 <span data-ttu-id="4da06-137">Obsahuje odkazy na části o načítání a úprava XML v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4da06-137">Provides links to sections about loading and modifying XML in Visual Basic.</span></span>  
  
 [<span data-ttu-id="4da06-138">XML</span><span class="sxs-lookup"><span data-stu-id="4da06-138">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 <span data-ttu-id="4da06-139">Obsahuje odkazy na části popisující, jak používat [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4da06-139">Provides links to sections describing how to use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>
