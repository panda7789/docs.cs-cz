---
title: Technologie LINQ to XML Annotations2
ms.date: 07/20/2015
ms.assetid: c3e8b3ff-fceb-4428-b0ca-1ed6f128aac8
ms.openlocfilehash: a7b81b8c1856c11cb0c5e777f31986a330cf115f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644794"
---
# <a name="linq-to-xml-annotations"></a><span data-ttu-id="ae90b-102">Technologie LINQ to XML poznámky</span><span class="sxs-lookup"><span data-stu-id="ae90b-102">LINQ to XML Annotations</span></span>
<span data-ttu-id="ae90b-103">Poznámky v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] vám umožní přidružit libovolné součásti XML ve stromu XML libovolného objektu jakéhokoli libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="ae90b-103">Annotations in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] enable you to associate any arbitrary object of any arbitrary type with any XML component in an XML tree.</span></span>  
  
 <span data-ttu-id="ae90b-104">Přidání poznámky do komponentu XML, jako <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XAttribute>, zavoláte <xref:System.Xml.Linq.XObject.AddAnnotation%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="ae90b-104">To add an annotation to an XML component, such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>, you call the <xref:System.Xml.Linq.XObject.AddAnnotation%2A> method.</span></span> <span data-ttu-id="ae90b-105">Můžete načíst poznámky podle typu.</span><span class="sxs-lookup"><span data-stu-id="ae90b-105">You retrieve annotations by type.</span></span>  
  
 <span data-ttu-id="ae90b-106">Všimněte si, že poznámky nejsou součástí informační sadu XML; jejich nejsou serializován nebo deserializován.</span><span class="sxs-lookup"><span data-stu-id="ae90b-106">Note that annotations are not part of the XML infoset; they are not serialized or deserialized.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ae90b-107">Metody</span><span class="sxs-lookup"><span data-stu-id="ae90b-107">Methods</span></span>  
 <span data-ttu-id="ae90b-108">Při práci s poznámky, můžete použít následující metody:</span><span class="sxs-lookup"><span data-stu-id="ae90b-108">You can use the following methods when working with annotations:</span></span>  
  
|<span data-ttu-id="ae90b-109">Metoda</span><span class="sxs-lookup"><span data-stu-id="ae90b-109">Method</span></span>|<span data-ttu-id="ae90b-110">Popis</span><span class="sxs-lookup"><span data-stu-id="ae90b-110">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|<span data-ttu-id="ae90b-111">Přidá objekt do seznamu poznámky <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="ae90b-111">Adds an object to the annotation list of an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.Annotation%2A>|<span data-ttu-id="ae90b-112">Získá je první objekt zadaného typu z – Poznámka <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="ae90b-112">Gets the first annotation object of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.Annotations%2A>|<span data-ttu-id="ae90b-113">Získá kolekci poznámek zadaného typu pro <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="ae90b-113">Gets a collection of annotations of the specified type for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|<span data-ttu-id="ae90b-114">Odebere poznámky zadaného typu z <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="ae90b-114">Removes the annotations of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ae90b-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="ae90b-115">See Also</span></span>  
 [<span data-ttu-id="ae90b-116">Pokročilé technologie LINQ to XML programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae90b-116">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
