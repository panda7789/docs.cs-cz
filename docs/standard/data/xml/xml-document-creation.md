---
title: Vytváření dokumentů XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 877e9c62-b082-4bfb-bc5b-f47297eb30ef
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b76140fb7d79b1e191c0451cd7556963130d224a
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2018
ms.locfileid: "44369014"
---
# <a name="xml-document-creation"></a>Vytváření dokumentů XML
Existují dva způsoby, jak vytvořit dokument XML. Jedním ze způsobů je vytvoření **XmlDocument** bez parametrů. Druhý způsob je k vytvoření **XmlDocument** a předat jako parametr XmlNameTable. Následující příklad ukazuje, jak vytvořit nový, prázdný **XmlDocument** pomocí žádné parametry.  
  
```vb  
Dim doc As New XmlDocument()  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
```  
  
 Po vytvoření dokumentu, můžete je načíst data pomocí dat z řetězce, Streamovat, adresa URL, čtečky textu nebo **XmlReader** odvozené třídy pomocí **načíst** metody. Je také jinou metodu načtení, **příkaz LoadXML** metodu, která čte z řetězce XML. Další informace o různých **zatížení** metody, naleznete v tématu [čtení dokumentu XML do modelu DOM](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md).  
  
 Existuje třída volá se, **XmlNameTable**. Tato třída je tabulka atomizované objekty řetězcových objektů. Tato tabulka poskytuje efektivní způsob k analyzátoru XML používat stejný objekt řetězce pro všechny opakované elementu a názvy atributů v dokumentu XML. **XmlNameTable** se automaticky vytvoří během dokumentu se vytvoří, jak je znázorněno výše a je načtena s názvy elementu a atributu při načtení dokumentu. Pokud už máte dokument s názvem tabulky a tyto názvy může být užitečné v jiném dokumentu, můžete vytvořit nový dokument pomocí **zatížení** metodu, která přebírá **XmlNameTable** jako parametr. Když se dokument s touto metodou, využívá existující **XmlNameTable** s atributy a elementy, které už jsou do něho načtené z jiného dokumentu. Je možné pro efektivní porovnání názvy prvků a atributů. Další informace o **XmlNameTable**, naleznete v tématu [porovnání objektů pomocí XmlNameTable](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md). Odkaz, naleznete v tématu <xref:System.Xml.XmlNameTable>.  
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
