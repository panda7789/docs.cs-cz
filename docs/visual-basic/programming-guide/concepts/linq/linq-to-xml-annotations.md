---
title: Technologie LINQ to XML Annotations2
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c3e8b3ff-fceb-4428-b0ca-1ed6f128aac8
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ca84af7cd750529eadb9d0967f4d5570b7038a07
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="linq-to-xml-annotations"></a><span data-ttu-id="29c6e-102">Technologie LINQ to XML poznámky</span><span class="sxs-lookup"><span data-stu-id="29c6e-102">LINQ to XML Annotations</span></span>
<span data-ttu-id="29c6e-103">Poznámky v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] vám umožní přidružit libovolné součásti XML ve stromu XML libovolného objektu jakéhokoli libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="29c6e-103">Annotations in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] enable you to associate any arbitrary object of any arbitrary type with any XML component in an XML tree.</span></span>  
  
 <span data-ttu-id="29c6e-104">Přidání poznámky do komponentu XML, jako <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XAttribute>, zavoláte <xref:System.Xml.Linq.XObject.AddAnnotation%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="29c6e-104">To add an annotation to an XML component, such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>, you call the <xref:System.Xml.Linq.XObject.AddAnnotation%2A> method.</span></span> <span data-ttu-id="29c6e-105">Můžete načíst poznámky podle typu.</span><span class="sxs-lookup"><span data-stu-id="29c6e-105">You retrieve annotations by type.</span></span>  
  
 <span data-ttu-id="29c6e-106">Všimněte si, že poznámky nejsou součástí informační sadu XML; jejich nejsou serializován nebo deserializován.</span><span class="sxs-lookup"><span data-stu-id="29c6e-106">Note that annotations are not part of the XML infoset; they are not serialized or deserialized.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="29c6e-107">Metody</span><span class="sxs-lookup"><span data-stu-id="29c6e-107">Methods</span></span>  
 <span data-ttu-id="29c6e-108">Při práci s poznámky, můžete použít následující metody:</span><span class="sxs-lookup"><span data-stu-id="29c6e-108">You can use the following methods when working with annotations:</span></span>  
  
|<span data-ttu-id="29c6e-109">Metoda</span><span class="sxs-lookup"><span data-stu-id="29c6e-109">Method</span></span>|<span data-ttu-id="29c6e-110">Popis</span><span class="sxs-lookup"><span data-stu-id="29c6e-110">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|<span data-ttu-id="29c6e-111">Přidá objekt do seznamu poznámky <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="29c6e-111">Adds an object to the annotation list of an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.Annotation%2A>|<span data-ttu-id="29c6e-112">Získá je první objekt zadaného typu z – Poznámka <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="29c6e-112">Gets the first annotation object of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.Annotations%2A>|<span data-ttu-id="29c6e-113">Získá kolekci poznámek zadaného typu pro <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="29c6e-113">Gets a collection of annotations of the specified type for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|<span data-ttu-id="29c6e-114">Odebere poznámky zadaného typu z <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="29c6e-114">Removes the annotations of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="29c6e-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="29c6e-115">See Also</span></span>  
 [<span data-ttu-id="29c6e-116">Pokročilé technologie LINQ to XML programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29c6e-116">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
