---
title: Serializace do souborů, tříd a XmlWriters1
ms.date: 07/20/2015
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
ms.openlocfilehash: c74dc7f429e4ae27f08f7acb6b3a6c39161aac71
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66483543"
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a>Serializace do tříd File, TextWriter a XmlWriter

Může serializovat stromů XML <xref:System.IO.File>, <xref:System.IO.TextWriter>, nebo <xref:System.Xml.XmlWriter>.

Může serializovat libovolné součásti XML, včetně <xref:System.Xml.Linq.XDocument> a <xref:System.Xml.Linq.XElement>, na řetězec pomocí `ToString` metody.

Pokud chcete potlačit formátování při serializaci do řetězce, můžete použít <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> metody.

Výchozí chování při serializaci do souboru se má formátovat dokument (odsazení) výsledného kódu XML. Při odsazení, není zachována nevýznamné prázdné znaky ve stromové struktuře XML. K serializaci formátování, použijte jednu z přetížení z následujících metod, které nepřebírají <xref:System.Xml.Linq.SaveOptions> jako argument:

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

Pokud chcete možnost odsazení a nevýznamné mezeru ve stromové struktuře XML, použijte jednu z přetížených z následujících metod, které provede <xref:System.Xml.Linq.SaveOptions> jako argument:

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

Příklady naleznete v tématu příslušný odkaz.

## <a name="see-also"></a>Viz také:

- [Serializace stromů XML (C#)](serializing-to-files-textwriters-and-xmlwriters.md)
