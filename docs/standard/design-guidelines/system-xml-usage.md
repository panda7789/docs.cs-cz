---
title: System.Xml využití
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce9869d538b69af9beaa74be3300175f279b8f53
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572811"
---
# <a name="systemxml-usage"></a>System.Xml využití
Tato část pojednává o použití několik typů, které se nacházejí v <xref:System.Xml?displayProperty=nameWithType> obory názvů, které můžete použít k reprezentování XML data.  
  
 **X nesmí** použít <xref:System.Xml.XmlNode> nebo <xref:System.Xml.XmlDocument> představují XML data. Upřednostnit pomocí instance <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, nebo podtypů <xref:System.Xml.Linq.XNode> místo. `XmlNode` a `XmlDocument` nejsou navrženy pro vystavení veřejné rozhraní API.  
  
 **PROVEĎTE ✓** použít `XmlReader`, `IXPathNavigable`, nebo podtypů `XNode` jako vstup nebo výstup členy, kteří přijímají nebo vrátit kód XML.  
  
 Pomocí těchto abstrakce místo `XmlDocument`, `XmlNode`, nebo <xref:System.Xml.XPath.XPathDocument>, protože to oddělí metody z konkrétní implementace dokumentu XML v paměti a umožňuje jim pro práci s virtuální zdroje dat XML, které zveřejňují `XNode` , `XmlReader`, nebo <xref:System.Xml.XPath.XPathNavigator>.  
  
 **X nesmí** podtřídami `XmlDocument` Pokud budete chtít vytvořit typ představující zobrazení základní objekt model nebo zdroj dat XML.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)  
 [Pokyny k používání](../../../docs/standard/design-guidelines/usage-guidelines.md)
