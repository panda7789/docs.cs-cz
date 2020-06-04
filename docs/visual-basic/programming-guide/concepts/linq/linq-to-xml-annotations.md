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
# <a name="linq-to-xml-annotations"></a>Poznámky v LINQ to XML
Poznámky v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] umožňují přidružit libovolný libovolný objekt libovolného typu k libovolné komponentě XML ve stromu XML.  
  
 Chcete-li přidat anotaci do komponenty XML, jako je například <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XAttribute> , zavoláte <xref:System.Xml.Linq.XObject.AddAnnotation%2A> metodu. Poznámky načtete podle typu.  
  
 Všimněte si, že poznámky nejsou součástí informační sady XML. nejsou serializovány nebo deserializovány.  
  
## <a name="methods"></a>Metody  
 Při práci s poznámkami můžete použít následující metody:  
  
|Metoda|Description|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|Přidá objekt do seznamu poznámek <xref:System.Xml.Linq.XObject> .|  
|<xref:System.Xml.Linq.XObject.Annotation%2A>|Získá první objekt poznámky zadaného typu z <xref:System.Xml.Linq.XObject> .|  
|<xref:System.Xml.Linq.XObject.Annotations%2A>|Získá kolekci poznámek zadaného typu pro <xref:System.Xml.Linq.XObject> .|  
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|Odstraní poznámky zadaného typu z <xref:System.Xml.Linq.XObject> .|  
  
## <a name="see-also"></a>Viz také

- [Rozšířené programování LINQ to XML (Visual Basic)](advanced-linq-to-xml-programming.md)
