---
title: "Vytváření dokumentů XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 877e9c62-b082-4bfb-bc5b-f47297eb30ef
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ea67841e44d8d88d2effec92eb1668142c1510f2
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="xml-document-creation"></a>Vytváření dokumentů XML
Existují dva způsoby, jak vytvořit dokument XML. Jedním ze způsobů je vytvoření **třídou XMLDocument nastavenou na** bez parametrů. Druhý způsob je vytvoření **třídou XMLDocument nastavenou na** a předejte ji XmlNameTable jako parametr. Následující příklad ukazuje, jak vytvořit nový, prázdný **třídou XMLDocument nastavenou na** pomocí žádné parametry.  
  
```vb  
Dim doc As New XmlDocument()  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
```  
  
 Po vytvoření dokumentu, můžete ho zatížení s daty z řetězce, stream, adresa URL, čtečku textu nebo **XmlReader** odvozené třídy pomocí **načíst** metoda. Je také jinou metodu načtení, **příkaz LoadXML** metodu, která čte XML z řetězce. Další informace o různých **zatížení** metody, najdete v části [čtení dokumentu XML do modelu DOM](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md).  
  
 Existuje třída volá **XmlNameTable**. Tato třída je tabulka objektů atomized řetězec. Tato tabulka obsahuje efektivní prostředky pro analyzátor XML, který chcete použít stejný objekt řetězce pro všechny opakované elementu a názvy atributů v dokumentu XML. **XmlNameTable** se automaticky vytvoří při dokumentu je vytvořen jako v příkladu nahoře a je načtena s názvy elementu a atributu při načtení dokumentu. Pokud již máte dokument s názvem tabulky a tyto názvy by být užitečné do jiného dokumentu, můžete vytvořit nový dokument pomocí **zatížení** metody, která použije **XmlNameTable** jako parametr. Pomocí této metody vytvoření dokumentu má použije existující **XmlNameTable** s atributy a elementy, které do ní již načten z jiného dokumentu. Slouží pro efektivní porovnávání názvy elementu a atributu. Další informace o **XmlNameTable**, najdete v části [objekt porovnání pomocí XmlNameTable](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md). Odkaz, najdete v části <xref:System.Xml.XmlNameTable>.  
  
## <a name="see-also"></a>Viz také  
 [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
