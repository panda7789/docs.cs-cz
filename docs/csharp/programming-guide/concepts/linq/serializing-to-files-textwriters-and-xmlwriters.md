---
title: "Serializace k souborům, TextWriters a XmlWriters1"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c2207ee3cf5bf1c89a01ba14875e788ceb53b01c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a>Serializace k souborům, TextWriters a XmlWriters
Může serializovat stromů XML <xref:System.IO.File>, <xref:System.IO.TextWriter>, nebo <xref:System.Xml.XmlWriter>.  
  
 Může serializovat libovolné součásti XML, včetně <xref:System.Xml.Linq.XDocument> a <xref:System.Xml.Linq.XElement>, na řetězec pomocí `ToString` metoda.  
  
 Pokud chcete potlačit, formátování při serializaci do řetězce, můžete použít <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> metoda.  
  
 Thedefault chování při serializaci do souboru je formátovat dokument (odsazení) výsledný soubor XML. Při odsazení, není zachována zanedbatelný mezer ve stromové struktuře XML. K serializaci s formátování, použijte jednu z následujících metod, které nepřebírají přetížení <xref:System.Xml.Linq.SaveOptions> jako argument:  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
 Pokud chcete, aby možnost, není pro odsazení a zachovat zanedbatelný mezer ve stromové struktuře XML, použijte jednu z přetížení následující metody, která přebírá <xref:System.Xml.Linq.SaveOptions> jako argument:  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
 Příklady najdete v tématu odpovídající odkaz.  
  
## <a name="see-also"></a>Viz také  
 [Serializace XML stromů (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
