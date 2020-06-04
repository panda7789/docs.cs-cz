---
title: LINQ to XML Annotations2
ms.date: 07/20/2015
ms.assetid: c3e8b3ff-fceb-4428-b0ca-1ed6f128aac8
ms.openlocfilehash: 917129a06483ce2001e178d744440504533d28d6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84369008"
---
# <a name="linq-to-xml-annotations"></a><span data-ttu-id="5cf4b-102">Poznámky v LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="5cf4b-102">LINQ to XML Annotations</span></span>
<span data-ttu-id="5cf4b-103">Poznámky v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] umožňují přidružit libovolný libovolný objekt libovolného typu k libovolné komponentě XML ve stromu XML.</span><span class="sxs-lookup"><span data-stu-id="5cf4b-103">Annotations in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] enable you to associate any arbitrary object of any arbitrary type with any XML component in an XML tree.</span></span>  
  
 <span data-ttu-id="5cf4b-104">Chcete-li přidat anotaci do komponenty XML, jako je například <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XAttribute> , zavoláte <xref:System.Xml.Linq.XObject.AddAnnotation%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="5cf4b-104">To add an annotation to an XML component, such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>, you call the <xref:System.Xml.Linq.XObject.AddAnnotation%2A> method.</span></span> <span data-ttu-id="5cf4b-105">Poznámky načtete podle typu.</span><span class="sxs-lookup"><span data-stu-id="5cf4b-105">You retrieve annotations by type.</span></span>  
  
 <span data-ttu-id="5cf4b-106">Všimněte si, že poznámky nejsou součástí informační sady XML. nejsou serializovány nebo deserializovány.</span><span class="sxs-lookup"><span data-stu-id="5cf4b-106">Note that annotations are not part of the XML infoset; they are not serialized or deserialized.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5cf4b-107">Metody</span><span class="sxs-lookup"><span data-stu-id="5cf4b-107">Methods</span></span>  
 <span data-ttu-id="5cf4b-108">Při práci s poznámkami můžete použít následující metody:</span><span class="sxs-lookup"><span data-stu-id="5cf4b-108">You can use the following methods when working with annotations:</span></span>  
  
|<span data-ttu-id="5cf4b-109">Metoda</span><span class="sxs-lookup"><span data-stu-id="5cf4b-109">Method</span></span>|<span data-ttu-id="5cf4b-110">Description</span><span class="sxs-lookup"><span data-stu-id="5cf4b-110">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|<span data-ttu-id="5cf4b-111">Přidá objekt do seznamu poznámek <xref:System.Xml.Linq.XObject> .</span><span class="sxs-lookup"><span data-stu-id="5cf4b-111">Adds an object to the annotation list of an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.Annotation%2A>|<span data-ttu-id="5cf4b-112">Získá první objekt poznámky zadaného typu z <xref:System.Xml.Linq.XObject> .</span><span class="sxs-lookup"><span data-stu-id="5cf4b-112">Gets the first annotation object of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.Annotations%2A>|<span data-ttu-id="5cf4b-113">Získá kolekci poznámek zadaného typu pro <xref:System.Xml.Linq.XObject> .</span><span class="sxs-lookup"><span data-stu-id="5cf4b-113">Gets a collection of annotations of the specified type for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|<span data-ttu-id="5cf4b-114">Odstraní poznámky zadaného typu z <xref:System.Xml.Linq.XObject> .</span><span class="sxs-lookup"><span data-stu-id="5cf4b-114">Removes the annotations of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5cf4b-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="5cf4b-115">See also</span></span>

- [<span data-ttu-id="5cf4b-116">Rozšířené programování LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5cf4b-116">Advanced LINQ to XML Programming (Visual Basic)</span></span>](advanced-linq-to-xml-programming.md)
