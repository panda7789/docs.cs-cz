---
title: Technologie LINQ to XML Annotations3
ms.date: 07/20/2015
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
ms.openlocfilehash: 13dd72a9016dea8c5b4389580f912625028e51ae
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43530361"
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

- [Pokročilé technologie LINQ to XML programování (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
