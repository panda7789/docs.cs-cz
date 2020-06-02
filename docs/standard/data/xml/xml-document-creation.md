---
title: Vytváření dokumentů XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 877e9c62-b082-4bfb-bc5b-f47297eb30ef
ms.openlocfilehash: 577d353a30c986d198140b4596ae1a7e199ddd6e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291978"
---
# <a name="xml-document-creation"></a>Vytváření dokumentů XML
Existují dva způsoby, jak vytvořit dokument XML. Jedním ze způsobů je vytvořit **XmlDocument** bez parametrů. Druhým způsobem je vytvořit **XmlDocument** a předat mu XmlNameTable jako parametr. Následující příklad ukazuje, jak vytvořit novou prázdnou **XmlDocument** pomocí žádného parametru.  
  
```vb  
Dim doc As New XmlDocument()  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
```  
  
 Po vytvoření dokumentu ho můžete načíst s daty z řetězce, datového proudu, adresy URL, čtečky textu nebo odvozené třídy **XmlReader** pomocí metody **Load** . Existuje také jiná metoda Load, metoda **LoadXml** , která čte XML z řetězce. Další informace o různých metodách **zatížení** naleznete v tématu [čtení dokumentu XML do modelu DOM](reading-an-xml-document-into-the-dom.md).  
  
 Existuje třída s názvem **XmlNameTable**. Tato třída je tabulka objektů řetězců Atom. Tato tabulka poskytuje efektivní způsob, jak analyzátor XML použít stejný objekt řetězce pro všechny opakované názvy elementů a atributů v dokumentu XML. **XmlNameTable** se automaticky vytvoří, když se vytvoří dokument, jak je znázorněno výše, a při načtení dokumentu se načte pomocí atributů a názvů elementů. Pokud již máte dokument s tabulkou názvů a tyto názvy by byly užitečné v jiném dokumentu, můžete vytvořit nový dokument pomocí metody **Load** , který jako parametr přijímá **XmlNameTable** . Když je dokument vytvořen pomocí této metody, používá existující **XmlNameTable** se všemi atributy a prvky, které jsou již do něj načteny z druhého dokumentu. Dá se použít pro efektivní porovnávání názvů elementů a atributů. Další informace o **XmlNameTable**naleznete v tématu [porovnání objektů pomocí XmlNameTable](object-comparison-using-xmlnametable.md). Referenční informace najdete v tématu <xref:System.Xml.XmlNameTable> .  
  
## <a name="see-also"></a>Viz také

- [model DOM (Document Object Model) dokumentu XML](xml-document-object-model-dom.md)
