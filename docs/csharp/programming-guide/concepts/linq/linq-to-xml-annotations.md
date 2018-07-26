---
title: Technologie LINQ to XML Annotations3
ms.date: 07/20/2015
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
ms.openlocfilehash: 8b8e03b0174ad2bf044c21eb9a9d3391da37fb7f
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960696"
---
# <a name="linq-to-xml-annotations"></a>Technologie LINQ to XML poznámky
Poznámky v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] vám umožní přidružit libovolné součásti XML ve stromu XML libovolného objektu jakéhokoli libovolného typu.  
  
 Přidat poznámku komponentě XML, jako například <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XAttribute>, volání <xref:System.Xml.Linq.XObject.AddAnnotation%2A> metody. Načtení poznámek podle typu.  
  
 Všimněte si, že poznámky nejsou součástí informační sadu XML; nejsou serializován nebo deserializován.  
  
## <a name="methods"></a>Metody  
 Při práci s poznámkami, můžete použít následující metody:  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|Přidá objekt do seznamu poznámky <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObject.Annotation%2A>|Získá první anotace objekt zadaného typu ze <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObject.Annotations%2A>|Získá kolekci poznámek zadaného typu pro <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|Odebere poznámky zadaného typu ze <xref:System.Xml.Linq.XObject>.|  
  
## <a name="see-also"></a>Viz také  
 [Pokročilé technologie LINQ to XML programování (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
