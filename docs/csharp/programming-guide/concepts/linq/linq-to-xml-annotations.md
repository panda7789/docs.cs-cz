---
title: Technologie LINQ to XML Annotations3
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: eadbc55ac6188fa3634745bf8bb222f07675a308
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="linq-to-xml-annotations"></a>Technologie LINQ to XML poznámky
Poznámky v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] vám umožní přidružit libovolné součásti XML ve stromu XML libovolného objektu jakéhokoli libovolného typu.  
  
 Přidání poznámky do komponentu XML, jako <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XAttribute>, zavoláte <xref:System.Xml.Linq.XObject.AddAnnotation%2A> metoda. Můžete načíst poznámky podle typu.  
  
 Všimněte si, že poznámky nejsou součástí informační sadu XML; jejich nejsou serializován nebo deserializován.  
  
## <a name="methods"></a>Metody  
 Při práci s poznámky, můžete použít následující metody:  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|Přidá objekt do seznamu poznámky <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObject.Annotation%2A>|Získá je první objekt zadaného typu z – Poznámka <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObject.Annotations%2A>|Získá kolekci poznámek zadaného typu pro <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|Odebere poznámky zadaného typu z <xref:System.Xml.Linq.XObject>.|  
  
## <a name="see-also"></a>Viz také  
 [Pokročilé technologie LINQ to XML programování (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
