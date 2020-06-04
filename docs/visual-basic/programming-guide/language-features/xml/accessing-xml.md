---
title: Přístup k XML
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
ms.openlocfilehash: 282b7d91ec7cfe2f587c67bc9a982f0da22ad925
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410306"
---
# <a name="accessing-xml-in-visual-basic"></a><span data-ttu-id="9bc6e-102">Přístup ke XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9bc6e-102">Accessing XML in Visual Basic</span></span>
<span data-ttu-id="9bc6e-103">Visual Basic poskytuje vlastnosti osy XML pro přístup k strukturám a jejich navigaci [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9bc6e-103">Visual Basic provides XML axis properties for accessing and navigating [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] structures.</span></span> <span data-ttu-id="9bc6e-104">Tyto vlastnosti používají speciální syntaxi k umožnění přístupu k prvkům a atributům zadáním názvů XML.</span><span class="sxs-lookup"><span data-stu-id="9bc6e-104">These properties use a special syntax to enable you to access elements and attributes by specifying the XML names.</span></span>  
  
 <span data-ttu-id="9bc6e-105">V následující tabulce jsou uvedeny funkce jazyka, které vám umožní přístup k elementům a atributům XML v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9bc6e-105">The following table lists the language features that enable you to access XML elements and attributes in Visual Basic.</span></span>  
  
### <a name="xml-axis-properties"></a><span data-ttu-id="9bc6e-106">Vlastnosti osy XML</span><span class="sxs-lookup"><span data-stu-id="9bc6e-106">XML Axis Properties</span></span>  
  
|<span data-ttu-id="9bc6e-107">Popis vlastnosti</span><span class="sxs-lookup"><span data-stu-id="9bc6e-107">Property description</span></span>|<span data-ttu-id="9bc6e-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="9bc6e-108">Example</span></span>|<span data-ttu-id="9bc6e-109">Description</span><span class="sxs-lookup"><span data-stu-id="9bc6e-109">Description</span></span>|  
|--------------------------|-------------|-----------------|  
|<span data-ttu-id="9bc6e-110">*podřízená osa*</span><span class="sxs-lookup"><span data-stu-id="9bc6e-110">*child axis*</span></span>|`contact.<phone>`|<span data-ttu-id="9bc6e-111">Načte všechny `phone` prvky, které jsou podřízenými prvky `contact` elementu.</span><span class="sxs-lookup"><span data-stu-id="9bc6e-111">Gets all `phone` elements that are child elements of the `contact` element.</span></span>|  
|<span data-ttu-id="9bc6e-112">*osa atributu*</span><span class="sxs-lookup"><span data-stu-id="9bc6e-112">*attribute axis*</span></span>|`phone.@type`|<span data-ttu-id="9bc6e-113">Získá všechny `type` atributy `phone` elementu.</span><span class="sxs-lookup"><span data-stu-id="9bc6e-113">Gets all `type` attributes of the `phone` element.</span></span>|  
|<span data-ttu-id="9bc6e-114">*osa následníka*</span><span class="sxs-lookup"><span data-stu-id="9bc6e-114">*descendant axis*</span></span>|`contacts...<name>`|<span data-ttu-id="9bc6e-115">Načte všechny `name` prvky `contacts` elementu bez ohledu na to, jak hluboko v hierarchii nastanou.</span><span class="sxs-lookup"><span data-stu-id="9bc6e-115">Gets all `name` elements of the `contacts` element, regardless of how deep in the hierarchy they occur.</span></span>|  
|<span data-ttu-id="9bc6e-116">*Indexer rozšíření*</span><span class="sxs-lookup"><span data-stu-id="9bc6e-116">*extension indexer*</span></span>|`contacts...<name>(0)`|<span data-ttu-id="9bc6e-117">Získá první `name` prvek z sekvence.</span><span class="sxs-lookup"><span data-stu-id="9bc6e-117">Gets the first `name` element from the sequence.</span></span>|  
|<span data-ttu-id="9bc6e-118">*osa*</span><span class="sxs-lookup"><span data-stu-id="9bc6e-118">*value*</span></span>|`contacts...<name>.Value`|<span data-ttu-id="9bc6e-119">Získá řetězcovou reprezentaci prvního objektu v sekvenci nebo je- `Nothing` li sekvence prázdná.</span><span class="sxs-lookup"><span data-stu-id="9bc6e-119">Gets the string representation of the first object in the sequence, or `Nothing` if the sequence is empty.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="9bc6e-120">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="9bc6e-120">In This Section</span></span>  
 [<span data-ttu-id="9bc6e-121">Postupy: Přístup k následnickým elementům XML</span><span class="sxs-lookup"><span data-stu-id="9bc6e-121">How to: Access XML Descendant Elements</span></span>](how-to-access-xml-descendant-elements.md)  
 <span data-ttu-id="9bc6e-122">Ukazuje, jak použít vlastnost následníka pro přístup ke všem elementům XML, které mají zadaný název a které jsou obsaženy v zadaném elementu XML.</span><span class="sxs-lookup"><span data-stu-id="9bc6e-122">Shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under a specified XML element.</span></span>  
  
 [<span data-ttu-id="9bc6e-123">Postupy: Přístup k podřízeným elementům XML</span><span class="sxs-lookup"><span data-stu-id="9bc6e-123">How to: Access XML Child Elements</span></span>](how-to-access-xml-child-elements.md)  
 <span data-ttu-id="9bc6e-124">Ukazuje, jak použít vlastnost podřízené osy pro přístup ke všem podřízeným elementům XML, které mají zadaný název v elementu XML.</span><span class="sxs-lookup"><span data-stu-id="9bc6e-124">Shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="9bc6e-125">Postupy: Přístup k atributům XML</span><span class="sxs-lookup"><span data-stu-id="9bc6e-125">How to: Access XML Attributes</span></span>](how-to-access-xml-attributes.md)  
 <span data-ttu-id="9bc6e-126">Ukazuje, jak použít vlastnost osy atributu pro přístup ke všem atributům XML, které mají zadaný název v elementu XML.</span><span class="sxs-lookup"><span data-stu-id="9bc6e-126">Shows how to use an attribute axis property to access all XML attributes that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="9bc6e-127">Postupy: Deklarace a používání předpon oboru názvů XML</span><span class="sxs-lookup"><span data-stu-id="9bc6e-127">How to: Declare and Use XML Namespace Prefixes</span></span>](how-to-declare-and-use-xml-namespace-prefixes.md)  
 <span data-ttu-id="9bc6e-128">Ukazuje, jak deklarovat předponu oboru názvů XML a použít ji k vytvoření a přístup k elementům XML.</span><span class="sxs-lookup"><span data-stu-id="9bc6e-128">Shows how to declare an XML namespace prefix and use it to create and access XML elements.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9bc6e-129">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="9bc6e-129">Related Sections</span></span>  
 [<span data-ttu-id="9bc6e-130">Vlastnosti osy XML</span><span class="sxs-lookup"><span data-stu-id="9bc6e-130">XML Axis Properties</span></span>](../../../language-reference/xml-axis/index.md)  
 <span data-ttu-id="9bc6e-131">Obsahuje odkazy na oddíly popisující různé vlastnosti přístupu XML.</span><span class="sxs-lookup"><span data-stu-id="9bc6e-131">Provides links to sections describing the various XML access properties.</span></span>  
  
 [<span data-ttu-id="9bc6e-132">Přehled technologie LINQ to XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9bc6e-132">Overview of LINQ to XML in Visual Basic</span></span>](overview-of-linq-to-xml.md)  
 <span data-ttu-id="9bc6e-133">Poskytuje Úvod k použití [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9bc6e-133">Provides an introduction to using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>  
  
 [<span data-ttu-id="9bc6e-134">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9bc6e-134">Creating XML in Visual Basic</span></span>](creating-xml.md)  
 <span data-ttu-id="9bc6e-135">Poskytuje Úvod k použití literálů XML v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9bc6e-135">Provides an introduction to using XML literals in Visual Basic.</span></span>  
  
 [<span data-ttu-id="9bc6e-136">Zacházení s XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9bc6e-136">Manipulating XML in Visual Basic</span></span>](manipulating-xml.md)  
 <span data-ttu-id="9bc6e-137">Obsahuje odkazy na oddíly o načítání a úpravách XML v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9bc6e-137">Provides links to sections about loading and modifying XML in Visual Basic.</span></span>  
  
 [<span data-ttu-id="9bc6e-138">XML</span><span class="sxs-lookup"><span data-stu-id="9bc6e-138">XML</span></span>](index.md)  
 <span data-ttu-id="9bc6e-139">Obsahuje odkazy na oddíly, které popisují použití [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9bc6e-139">Provides links to sections describing how to use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>
