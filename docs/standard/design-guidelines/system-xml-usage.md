---
title: Použití System.Xml
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
ms.openlocfilehash: 07828219f2e17be925d060fa3bb33a9209ecb62b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291666"
---
# <a name="systemxml-usage"></a>Použití System.Xml
Tato část pojednává o použití několika typů umístěných v <xref:System.Xml?displayProperty=nameWithType> oborech názvů, které lze použít k reprezentaci dat XML.

 ❌Nepoužívejte <xref:System.Xml.XmlNode> nebo <xref:System.Xml.XmlDocument> k reprezentaci dat XML. Místo toho používejte instance typu <xref:System.Xml.XPath.IXPathNavigable> , <xref:System.Xml.XmlReader> , <xref:System.Xml.XmlWriter> nebo <xref:System.Xml.Linq.XNode> . `XmlNode`a `XmlDocument` nejsou navržené pro vystavení ve veřejných rozhraních API.

 ✔️ použít `XmlReader` , `IXPathNavigable` nebo podtypy `XNode` jako vstup nebo výstup členů, kteří přijímají nebo vracejí kód XML.

 Použijte tyto abstrakce namísto `XmlDocument` , `XmlNode` , nebo <xref:System.Xml.XPath.XPathDocument> , protože se tím odpojí metody od konkrétních implementací dokumentu XML v paměti a umožňuje jim pracovat s virtuálními zdroji dat XML, které zveřejňují `XNode` , `XmlReader` nebo <xref:System.Xml.XPath.XPathNavigator> .

 ❌Nepoužívejte podtřídu `XmlDocument` , pokud chcete vytvořit typ reprezentující zobrazení XML základního objektového modelu nebo zdroje dat.

 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*

## <a name="see-also"></a>Viz také

- [Pokyny k návrhu architektury](index.md)
- [Pokyny k použití](usage-guidelines.md)
