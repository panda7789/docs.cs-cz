---
title: Serializace do souborů, TextWriter a XmlWriters3
ms.date: 07/20/2015
ms.assetid: 7a0c24df-79ef-41a0-87f5-e6cf79382da9
ms.openlocfilehash: d8b929ef02b8fd9c6a9f29ea997a754699a6e1c4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403560"
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a>Serializace do tříd File, TextWriter a XmlWriter

Můžete serializovat stromy XML na <xref:System.IO.File> , <xref:System.IO.TextWriter> nebo <xref:System.Xml.XmlWriter> .

Můžete serializovat jakoukoli komponentu XML, včetně <xref:System.Xml.Linq.XDocument> a <xref:System.Xml.Linq.XElement> , do řetězce pomocí `ToString` metody.

Pokud chcete potlačit formátování při serializaci na řetězec, můžete použít <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> metodu.

Výchozí chování při serializaci do souboru je formátování (odsazení) výsledného dokumentu XML. Při odsazení se nezachovají nevýznamné prázdné znaky ve stromu XML. Chcete-li serializovat s formátováním, použijte jedno z přetížení následujících metod, které nevezmou <xref:System.Xml.Linq.SaveOptions> jako argument:

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

Chcete-li, aby možnost neodsazena a zachovala nevýznamné prázdné znaky ve stromu XML, použijte jedno z přetížení následujících metod, které přebírají <xref:System.Xml.Linq.SaveOptions> jako argument:

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

Příklady najdete v příslušném referenčním tématu.

## <a name="see-also"></a>Viz také

- [Serializace stromů XML (Visual Basic)](serializing-xml-trees.md)
