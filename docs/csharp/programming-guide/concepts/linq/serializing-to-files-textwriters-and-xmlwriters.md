---
title: Serializace do tříd File, TextWriter a XmlWriter
description: Přečtěte si o možnostech serializace stromů XML do souboru, TextWriter nebo XmlWriter v jazyce C# pomocí metod ToString nebo Save.
ms.date: 07/20/2015
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
ms.openlocfilehash: 43c51ae7e9bf1a7848d45fd900424d6186671e53
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302383"
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

## <a name="see-also"></a>Viz také:

- [Serializace stromů XML (C#)](serializing-to-files-textwriters-and-xmlwriters.md)
