---
title: "Řešení externí XSLT šablony stylů a dokumentů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 920cfe3b-d525-4bb2-abf6-9431651f9cf9
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a5e84935f9fff1f993a677d408287cd775269f03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="resolving-external-xslt-style-sheets-and-documents"></a>Řešení externí XSLT šablony stylů a dokumentů
Existují několikrát během transformace, kdy budete muset vyřešit externím prostředkům.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Třída je zastaralá ve [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Můžete provést jazyk XSL pro transformace transformace XSLT () pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy.  
  
 Existují několikrát během transformace, když potřebujete vyřešit externích zdrojů:  
  
-   Během <xref:System.Xml.Xsl.XslTransform.Load%2A> najít externí šabloně stylů.  
  
-   Během <xref:System.Xml.Xsl.XslTransform.Load%2A> vyřešit všechny `<xsl:include>` nebo `<xsl:import>` elementy najít v šabloně stylů.  
  
-   Během <xref:System.Xml.Xsl.XslTransform.Transform%2A> vyřešit všechny `document()` funkce.  
  
## <a name="using-the-xmlresolver-class"></a>Používání třídy objekt XmlResolver  
 Pokud se vyžaduje ověření pro přístup k prostředkům sítě, použijte <xref:System.Xml.Xsl.XslTransform.Load%2A> metody, které mají <xref:System.Xml.XmlResolver> parametr předat <xref:System.Xml.XmlResolver> objekt, který nemá nastaveny vlastnosti potřebné přihlašovací údaje.  
  
 Pokud máte vlastní <xref:System.Xml.XmlResolver> , kterou chcete použít, nebo pokud je třeba zadat jiná pověření, následující tabulka uvádí úlohy požadováno, v závislosti na tom, když na externí zdroj potřebuje řešení.  
  
|Jaký proces vyžaduje překlad|Požadované úlohy|  
|--------------------------------------|-------------------|  
|Během <xref:System.Xml.Xsl.XslTransform.Load%2A> najít šablony stylů.|Zadejte přetížené <xref:System.Xml.Xsl.XslTransform.Load%2A> metoda, která přebírá jako parametr, <xref:System.Xml.XmlResolver> Pokud šablony stylů na prostředek, který vyžaduje přihlašovací údaje.|  
|Během <xref:System.Xml.Xsl.XslTransform.Load%2A> vyřešit `<xsl:include>` nebo `<xsl:import>`.|Zadejte přetížené <xref:System.Xml.Xsl.XslTransform.Load%2A> metoda, která přebírá jako parametr, <xref:System.Xml.XmlResolver>. <xref:System.Xml.XmlResolver> Slouží k načtení šablony stylů odkazuje `import` nebo `include` příkazy. Pokud předáte v `null`, nejsou přeložit externí zdroje.|  
|Při transformaci vyřešit všechny `document()` funkce.|Zadejte <xref:System.Xml.XmlResolver> během transformace pomocí <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody, která použije <xref:System.Xml.XmlResolver> argument.|  
  
 `document()` Funkce načte další prostředky XML z šablony stylů, kromě počáteční data XML poskytované vstupního datového proudu. Vzhledem k tomu, že tato funkce umožňuje zahrnutí data XML, který může být umístěn jinde, <xref:System.Xml.XmlResolver> s `null` hodnota zadaná pro <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda zabraňuje `document()` funkce spuštění. Pokud chcete použít `document()` fungovat, použijte <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody, která použije <xref:System.Xml.XmlResolver> jako parametr, kromě nutnosti příslušných oprávnění nastavit.  
  
 Další informace o <xref:System.Xml.Xsl.XslTransform.Load%2A> metoda a jeho použití programu <xref:System.Xml.XmlResolver>, najdete v části <xref:System.Xml.Xsl.XslTransform.Load%28System.String%2CSystem.Xml.XmlResolver%29?displayProperty=nameWithType>.  
  
 Když <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda je volána, oprávnění jsou vypočtena podle důkaz zadávat v okamžiku zatížení a přiřazený sadě oprávnění proces celý transformace. Pokud `document()` funkce pokusí spustit akci, která vyžaduje oprávnění nebyl nalezen v sadě, je vyvolána výjimka.  
  
## <a name="see-also"></a>Viz také  
 [Transformace XSLT pomocí XslTransform – třída](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [Třída XslTransform implementuje procesoru XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)  
 [Výstupy z XslTransform](../../../../docs/standard/data/xml/outputs-from-an-xsltransform.md)  
 [Transformace XSLT přes různé úložiště](../../../../docs/standard/data/xml/xslt-transformations-over-different-stores.md)  
 [Třída XsltArgumentList pro parametry list stylu a rozšíření objekty](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md)  
 [Pomocí skriptování šablony stylů XSLT \<msxsl:script >](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md)  
 [Podpora pro msxsl:node-set() – funkce](../../../../docs/standard/data/xml/support-for-the-msxsl-node-set-function.md)  
 [Objektem XPathNavigator nastaveným v transformace](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
 [XPathNodeIterator v transformace](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
 [Vstup XPathDocument XslTransform](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
 [XmlDataDocument vstup XslTransform](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)  
 [Třídou XMLDocument nastavenou na vstup XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
