---
title: Technologie LINQ to XML Annotations3
ms.date: 07/20/2015
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
ms.openlocfilehash: 753fc656d78f2cefde98a8cbfb48713c7a107f77
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54676715"
---
# <a name="linq-to-xml-annotations"></a><span data-ttu-id="61647-102">Technologie LINQ to XML poznámky</span><span class="sxs-lookup"><span data-stu-id="61647-102">LINQ to XML Annotations</span></span>
<span data-ttu-id="61647-103">Poznámky v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] vám umožní přidružit libovolné součásti XML ve stromu XML libovolného objektu jakéhokoli libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="61647-103">Annotations in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] enable you to associate any arbitrary object of any arbitrary type with any XML component in an XML tree.</span></span>  
  
 <span data-ttu-id="61647-104">Přidat poznámku komponentě XML, jako například <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XAttribute>, volání <xref:System.Xml.Linq.XObject.AddAnnotation%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="61647-104">To add an annotation to an XML component, such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>, you call the <xref:System.Xml.Linq.XObject.AddAnnotation%2A> method.</span></span> <span data-ttu-id="61647-105">Načtení poznámek podle typu.</span><span class="sxs-lookup"><span data-stu-id="61647-105">You retrieve annotations by type.</span></span>  
  
 <span data-ttu-id="61647-106">Všimněte si, že poznámky nejsou součástí informační sadu XML; nejsou serializován nebo deserializován.</span><span class="sxs-lookup"><span data-stu-id="61647-106">Note that annotations are not part of the XML infoset; they are not serialized or deserialized.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="61647-107">Metody</span><span class="sxs-lookup"><span data-stu-id="61647-107">Methods</span></span>  
 <span data-ttu-id="61647-108">Při práci s poznámkami, můžete použít následující metody:</span><span class="sxs-lookup"><span data-stu-id="61647-108">You can use the following methods when working with annotations:</span></span>  
  
|<span data-ttu-id="61647-109">Metoda</span><span class="sxs-lookup"><span data-stu-id="61647-109">Method</span></span>|<span data-ttu-id="61647-110">Popis</span><span class="sxs-lookup"><span data-stu-id="61647-110">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|<span data-ttu-id="61647-111">Přidá objekt do seznamu poznámky <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="61647-111">Adds an object to the annotation list of an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.Annotation%2A>|<span data-ttu-id="61647-112">Získá první anotace objekt zadaného typu ze <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="61647-112">Gets the first annotation object of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.Annotations%2A>|<span data-ttu-id="61647-113">Získá kolekci poznámek zadaného typu pro <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="61647-113">Gets a collection of annotations of the specified type for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|<span data-ttu-id="61647-114">Odebere poznámky zadaného typu ze <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="61647-114">Removes the annotations of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="61647-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="61647-115">See also</span></span>

- [<span data-ttu-id="61647-116">Pokročilé technologie LINQ to XML programování (C#)</span><span class="sxs-lookup"><span data-stu-id="61647-116">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
