---
title: Použití System.Xml
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
ms.openlocfilehash: c57f5451526094d58066d7d391f41795f17732de
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709033"
---
# <a name="systemxml-usage"></a>Použití System.Xml
Tato část pojednává o použití několika typů umístěných v <xref:System.Xml?displayProperty=nameWithType> oborech názvů, které lze použít k reprezentaci dat XML.  
  
 **X DO NOT** použít <xref:System.Xml.XmlNode> nebo <xref:System.Xml.XmlDocument> představují XML data. Místo toho používejte instance <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>nebo podtypy <xref:System.Xml.Linq.XNode>. `XmlNode` a `XmlDocument` nejsou navržené pro vystavení ve veřejných rozhraních API.  
  
 **✓ DO** použít `XmlReader`, `IXPathNavigable`, nebo podtypů `XNode` jako vstup nebo výstup členy, kteří přijímají nebo vrátit kód XML.  
  
 Tyto abstrakce použijte místo `XmlDocument`, `XmlNode`nebo <xref:System.Xml.XPath.XPathDocument>, protože se tím odpojí metody od konkrétních implementací dokumentu XML v paměti a umožňuje jim pracovat s virtuálními zdroji dat XML, které zveřejňují `XNode`, `XmlReader`nebo <xref:System.Xml.XPath.XPathNavigator>.  
  
 **X DO NOT** podtřídami `XmlDocument` Pokud budete chtít vytvořit typ představující zobrazení základní objekt model nebo zdroj dat XML.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
- [Pokyny k používání](../../../docs/standard/design-guidelines/usage-guidelines.md)
