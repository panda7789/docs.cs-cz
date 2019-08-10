---
title: Serializace do tříd File, TextWriter a XmlWriter
ms.date: 07/20/2015
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
ms.openlocfilehash: 20cb84a9f79ca8de3e86a996f18c388dc53340ae
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2019
ms.locfileid: "68868847"
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a>Serializace do tříd File, TextWriter a XmlWriter

Můžete serializovat stromy XML na <xref:System.IO.File> <xref:System.IO.TextWriter>, nebo <xref:System.Xml.XmlWriter>.

Můžete serializovat jakoukoli komponentu XML, včetně <xref:System.Xml.Linq.XDocument> a <xref:System.Xml.Linq.XElement>, do řetězce pomocí `ToString` metody.

Pokud chcete potlačit formátování při serializaci na řetězec, můžete použít <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> metodu.

Výchozí chování při serializaci do souboru je formátování (odsazení) výsledného dokumentu XML. Při odsazení se nezachovají nevýznamné prázdné znaky ve stromu XML. Chcete-li serializovat s formátováním, použijte jedno z přetížení následujících metod, které nevezmou <xref:System.Xml.Linq.SaveOptions> jako argument:

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

Chcete-li, aby možnost neodsazena a zachovala nevýznamné prázdné znaky ve stromu XML, použijte jedno z přetížení následujících metod, které přebírají <xref:System.Xml.Linq.SaveOptions> jako argument:

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

Příklady najdete v příslušném referenčním tématu.

## <a name="see-also"></a>Viz také:

- [Serializace stromů XML (C#)](serializing-to-files-textwriters-and-xmlwriters.md)
