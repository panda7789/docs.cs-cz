---
title: Language-Integrated osy v jazyce Visual Basic (technologie LINQ to XML)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d450a556-a134-4261-b011-44e399660894
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d648ba7c8710f73c4aeb8dad3983f219c5fe1815
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="language-integrated-axes-in-visual-basic-linq-to-xml"></a><span data-ttu-id="6d175-102">Language-Integrated osy v jazyce Visual Basic (technologie LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="6d175-102">Language-Integrated Axes in Visual Basic (LINQ to XML)</span></span>
<span data-ttu-id="6d175-103">Tato část popisuje funkce přímo integrovaná [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] jazyka usnadňují přístup XML.</span><span class="sxs-lookup"><span data-stu-id="6d175-103">This section describes features built directly into the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] language to make it easy to access XML.</span></span> <span data-ttu-id="6d175-104">Mnoho příkladů v LINQ do dokumentace XML pomocí těchto integrované [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] osy.</span><span class="sxs-lookup"><span data-stu-id="6d175-104">Many of the examples in the LINQ to XML documentation use these integrated [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] axes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6d175-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="6d175-105">In This Section</span></span>  
  
|<span data-ttu-id="6d175-106">Téma</span><span class="sxs-lookup"><span data-stu-id="6d175-106">Topic</span></span>|<span data-ttu-id="6d175-107">Popis</span><span class="sxs-lookup"><span data-stu-id="6d175-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="6d175-108">Vlastnost osy podřízeného souboru XML</span><span class="sxs-lookup"><span data-stu-id="6d175-108">XML Child Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)|<span data-ttu-id="6d175-109">Poskytuje přístup k podřízené objekty daného jednu z následujících: <xref:System.Xml.Linq.XElement> objektu, <xref:System.Xml.Linq.XDocument> objektu, kolekce <xref:System.Xml.Linq.XElement> objekty nebo kolekci <xref:System.Xml.Linq.XDocument> objekty.</span><span class="sxs-lookup"><span data-stu-id="6d175-109">Provides access to the children of one of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="6d175-110">Je ekvivalentní této osy <xref:System.Xml.Linq.XContainer.Elements%2A> osy.</span><span class="sxs-lookup"><span data-stu-id="6d175-110">This axis is equivalent to the <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span>|  
|[<span data-ttu-id="6d175-111">Vlastnost osy nástupce XML</span><span class="sxs-lookup"><span data-stu-id="6d175-111">XML Descendant Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)|<span data-ttu-id="6d175-112">Poskytuje přístup k následníky následující: <xref:System.Xml.Linq.XElement> objektu, <xref:System.Xml.Linq.XDocument> objektu nebo kolekci <xref:System.Xml.Linq.XElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="6d175-112">Provides access to the descendants of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, or a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="6d175-113">Je ekvivalentní této osy <xref:System.Xml.Linq.XContainer.Descendants%2A> osy.</span><span class="sxs-lookup"><span data-stu-id="6d175-113">This axis is equivalent to the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>|  
|[<span data-ttu-id="6d175-114">Vlastnost osy atributu XML</span><span class="sxs-lookup"><span data-stu-id="6d175-114">XML Attribute Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)|<span data-ttu-id="6d175-115">Poskytuje přístup k atribut <xref:System.Xml.Linq.XElement> objektu.</span><span class="sxs-lookup"><span data-stu-id="6d175-115">Provides access to an attribute of an <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="6d175-116">Je této osy zhruba odpovídá <xref:System.Xml.Linq.XElement.Attribute%2A> osy.</span><span class="sxs-lookup"><span data-stu-id="6d175-116">This axis is roughly equivalent to the <xref:System.Xml.Linq.XElement.Attribute%2A> axis.</span></span> <span data-ttu-id="6d175-117">Této osy se liší od <xref:System.Xml.Linq.XElement.Attribute%2A> osy v tom, že ji vrací hodnotu pro atribut, není <xref:System.Xml.Linq.XAttribute> objektu.</span><span class="sxs-lookup"><span data-stu-id="6d175-117">This axis differs from the <xref:System.Xml.Linq.XElement.Attribute%2A> axis in that it returns the value of the attribute, not an <xref:System.Xml.Linq.XAttribute> object.</span></span>|  
|[<span data-ttu-id="6d175-118">Vlastnost indexeru rozšíření</span><span class="sxs-lookup"><span data-stu-id="6d175-118">Extension Indexer Property</span></span>](../../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)|<span data-ttu-id="6d175-119">Poskytuje přístup k jednotlivé elementy v kolekci.</span><span class="sxs-lookup"><span data-stu-id="6d175-119">Provides access to individual elements in a collection.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6d175-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="6d175-120">See Also</span></span>  
 [<span data-ttu-id="6d175-121">Technologie LINQ to XML osy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6d175-121">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
