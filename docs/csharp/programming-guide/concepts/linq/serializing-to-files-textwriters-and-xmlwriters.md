---
title: Serializace do tříd File, TextWriter a XmlWriter
ms.date: 07/20/2015
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
ms.openlocfilehash: 20cb84a9f79ca8de3e86a996f18c388dc53340ae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "68868847"
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a>Serializace do tříd File, TextWriter a XmlWriter

Stromy XML můžete serializovat <xref:System.IO.File>do <xref:System.IO.TextWriter>, a <xref:System.Xml.XmlWriter>nebo .

Pomocí metody můžete serializovat libovolnou <xref:System.Xml.Linq.XElement>komponentu `ToString` XML, včetně <xref:System.Xml.Linq.XDocument> a , do řetězce.

Pokud chcete potlačit formátování při serializaci na řetězec, můžete <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> použít metodu.

Výchozí chování při serializaci souboru je formátování (odsazení) výsledného dokumentu XML. Při odsazení se nevýznamné prázdné místo ve stromu XML nezachová. Chcete-li serializovat s formátováním, použijte jednu z přetížení následujících metod, které neberou <xref:System.Xml.Linq.SaveOptions> jako argument:

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

Pokud chcete možnost neodsadit a zachovat nevýznamné prázdné místo ve stromu XML, použijte jednu <xref:System.Xml.Linq.SaveOptions> z přetížení následujících metod, která bere jako argument:

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

Příklady naleznete v příslušném referenčním tématu.

## <a name="see-also"></a>Viz také

- [Serializace stromů XML (C#)](serializing-to-files-textwriters-and-xmlwriters.md)
