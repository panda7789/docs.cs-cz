---
title: Přístup ke XML v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
ms.openlocfilehash: 0540c52cf3e4cd7594f051c10832ea99cf58a34e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756959"
---
# <a name="accessing-xml-in-visual-basic"></a><span data-ttu-id="fb043-102">Přístup ke XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fb043-102">Accessing XML in Visual Basic</span></span>
<span data-ttu-id="fb043-103">Visual Basic poskytuje vlastnosti osy XML pro přístup k a navigace [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] struktury.</span><span class="sxs-lookup"><span data-stu-id="fb043-103">Visual Basic provides XML axis properties for accessing and navigating [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] structures.</span></span> <span data-ttu-id="fb043-104">Tyto vlastnosti pomocí speciální syntaxe umožňuje přístup k prvkům a atributům tak, že zadáte názvy XML.</span><span class="sxs-lookup"><span data-stu-id="fb043-104">These properties use a special syntax to enable you to access elements and attributes by specifying the XML names.</span></span>  
  
 <span data-ttu-id="fb043-105">V následující tabulce jsou uvedeny vlastnosti jazyka, které vám umožní přístup k XML elementů a atributů v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fb043-105">The following table lists the language features that enable you to access XML elements and attributes in Visual Basic.</span></span>  
  
### <a name="xml-axis-properties"></a><span data-ttu-id="fb043-106">Vlastnosti osy XML</span><span class="sxs-lookup"><span data-stu-id="fb043-106">XML Axis Properties</span></span>  
  
|<span data-ttu-id="fb043-107">Popis vlastnosti</span><span class="sxs-lookup"><span data-stu-id="fb043-107">Property description</span></span>|<span data-ttu-id="fb043-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="fb043-108">Example</span></span>|<span data-ttu-id="fb043-109">Popis</span><span class="sxs-lookup"><span data-stu-id="fb043-109">Description</span></span>|  
|--------------------------|-------------|-----------------|  
|<span data-ttu-id="fb043-110">*podřízená osa*</span><span class="sxs-lookup"><span data-stu-id="fb043-110">*child axis*</span></span>|`contact.<phone>`|<span data-ttu-id="fb043-111">Získá všechny `phone` prvky, které jsou podřízené prvky `contact` elementu.</span><span class="sxs-lookup"><span data-stu-id="fb043-111">Gets all `phone` elements that are child elements of the `contact` element.</span></span>|  
|<span data-ttu-id="fb043-112">*atribut osy*</span><span class="sxs-lookup"><span data-stu-id="fb043-112">*attribute axis*</span></span>|`phone.@type`|<span data-ttu-id="fb043-113">Získá všechny `type` atributy `phone` elementu.</span><span class="sxs-lookup"><span data-stu-id="fb043-113">Gets all `type` attributes of the `phone` element.</span></span>|  
|<span data-ttu-id="fb043-114">*Následnické osy*</span><span class="sxs-lookup"><span data-stu-id="fb043-114">*descendant axis*</span></span>|`contacts...<name>`|<span data-ttu-id="fb043-115">Získá všechny `name` prvky `contacts` elementu, bez ohledu na to, jak hluboko v hierarchii k nim dojde.</span><span class="sxs-lookup"><span data-stu-id="fb043-115">Gets all `name` elements of the `contacts` element, regardless of how deep in the hierarchy they occur.</span></span>|  
|<span data-ttu-id="fb043-116">*Indexovací modul rozšíření*</span><span class="sxs-lookup"><span data-stu-id="fb043-116">*extension indexer*</span></span>|`contacts...<name>(0)`|<span data-ttu-id="fb043-117">Získá první `name` element z pořadí.</span><span class="sxs-lookup"><span data-stu-id="fb043-117">Gets the first `name` element from the sequence.</span></span>|  
|<span data-ttu-id="fb043-118">*value*</span><span class="sxs-lookup"><span data-stu-id="fb043-118">*value*</span></span>|`contacts...<name>.Value`|<span data-ttu-id="fb043-119">Získá řetězcovou reprezentaci objektu první v pořadí, nebo `Nothing` Pokud sekvence je prázdný.</span><span class="sxs-lookup"><span data-stu-id="fb043-119">Gets the string representation of the first object in the sequence, or `Nothing` if the sequence is empty.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="fb043-120">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="fb043-120">In This Section</span></span>  
 [<span data-ttu-id="fb043-121">Postupy: Přístup k Následnickým elementům XML</span><span class="sxs-lookup"><span data-stu-id="fb043-121">How to: Access XML Descendant Elements</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)  
 <span data-ttu-id="fb043-122">Ukazuje, jak používat vlastnost Následnické osy pro přístup k všech elementů XML, které jsou obsaženy v rámci zadaného elementu XML, které mají zadaný název.</span><span class="sxs-lookup"><span data-stu-id="fb043-122">Shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under a specified XML element.</span></span>  
  
 [<span data-ttu-id="fb043-123">Postupy: Přístup XML podřízených elementů</span><span class="sxs-lookup"><span data-stu-id="fb043-123">How to: Access XML Child Elements</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-child-elements.md)  
 <span data-ttu-id="fb043-124">Ukazuje, jak používat podřízený – vlastnost osy pro přístup k všechny podřízené prvky XML, které mají zadaný název v elementu jazyka XML.</span><span class="sxs-lookup"><span data-stu-id="fb043-124">Shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="fb043-125">Postupy: Přístup k atributům XML</span><span class="sxs-lookup"><span data-stu-id="fb043-125">How to: Access XML Attributes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-attributes.md)  
 <span data-ttu-id="fb043-126">Ukazuje, jak pomocí vlastnost osy atributu přístup ke všem atributům XML, které mají zadaný název v elementu jazyka XML.</span><span class="sxs-lookup"><span data-stu-id="fb043-126">Shows how to use an attribute axis property to access all XML attributes that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="fb043-127">Postupy: Deklarace a používání předpon Namespace XML</span><span class="sxs-lookup"><span data-stu-id="fb043-127">How to: Declare and Use XML Namespace Prefixes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-declare-and-use-xml-namespace-prefixes.md)  
 <span data-ttu-id="fb043-128">Ukazuje, jak deklarovat předponu oboru názvů XML a použít ho k vytváření a přístup k elementům XML.</span><span class="sxs-lookup"><span data-stu-id="fb043-128">Shows how to declare an XML namespace prefix and use it to create and access XML elements.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="fb043-129">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="fb043-129">Related Sections</span></span>  
 [<span data-ttu-id="fb043-130">Vlastnosti osy XML</span><span class="sxs-lookup"><span data-stu-id="fb043-130">XML Axis Properties</span></span>](../../../../visual-basic/language-reference/xml-axis/index.md)  
 <span data-ttu-id="fb043-131">Obsahuje odkazy na oddíly popisují různé vlastnosti přístupu XML.</span><span class="sxs-lookup"><span data-stu-id="fb043-131">Provides links to sections describing the various XML access properties.</span></span>  
  
 [<span data-ttu-id="fb043-132">Přehled technologie LINQ to XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fb043-132">Overview of LINQ to XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 <span data-ttu-id="fb043-133">Poskytuje úvod do používání [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fb043-133">Provides an introduction to using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>  
  
 [<span data-ttu-id="fb043-134">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fb043-134">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 <span data-ttu-id="fb043-135">Poskytuje úvod do používání literály XML v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fb043-135">Provides an introduction to using XML literals in Visual Basic.</span></span>  
  
 [<span data-ttu-id="fb043-136">Manipulace s kódem XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fb043-136">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 <span data-ttu-id="fb043-137">Poskytuje odkazy na části o načítání a úpravy XML v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fb043-137">Provides links to sections about loading and modifying XML in Visual Basic.</span></span>  
  
 [<span data-ttu-id="fb043-138">XML</span><span class="sxs-lookup"><span data-stu-id="fb043-138">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 <span data-ttu-id="fb043-139">Poskytuje odkazy na části popisující, jak používat [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fb043-139">Provides links to sections describing how to use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>
