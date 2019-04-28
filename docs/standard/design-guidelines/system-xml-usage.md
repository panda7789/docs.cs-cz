---
title: Použití System.Xml
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
author: KrzysztofCwalina
ms.openlocfilehash: fc94ac62d1f2413c5f51446a8f6d0a52d9151557
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650125"
---
# <a name="systemxml-usage"></a>Použití System.Xml
Tato část pojednává o využití z několika typů, které se nacházejí v <xref:System.Xml?displayProperty=nameWithType> obory názvů, který slouží k reprezentaci dat XML.  
  
 **X DO NOT** použít <xref:System.Xml.XmlNode> nebo <xref:System.Xml.XmlDocument> představují XML data. Upřednostní použití instancí <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, nebo podtypy <xref:System.Xml.Linq.XNode> místo. `XmlNode` a `XmlDocument` nejsou určeny pro vystavení ve veřejných rozhraní API.  
  
 **✓ DO** použít `XmlReader`, `IXPathNavigable`, nebo podtypů `XNode` jako vstup nebo výstup členy, kteří přijímají nebo vrátit kód XML.  
  
 Použijte tato abstrakce místo `XmlDocument`, `XmlNode`, nebo <xref:System.Xml.XPath.XPathDocument>, protože to odděluje metody z konkrétních implementací dokumentu XML v paměti a umožňuje pracovat s virtuální zdroje dat XML, které vystavují `XNode` , `XmlReader`, nebo <xref:System.Xml.XPath.XPathNavigator>.  
  
 **X DO NOT** podtřídami `XmlDocument` Pokud budete chtít vytvořit typ představující zobrazení základní objekt model nebo zdroj dat XML.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
- [Pokyny k používání](../../../docs/standard/design-guidelines/usage-guidelines.md)
