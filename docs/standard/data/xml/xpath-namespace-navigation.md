---
title: Namespace XPath navigace
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 06cc7abb-7416-415c-9dd6-67751b8cabd5
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: beb6265e8b245893cd7fa5edca28ba1b081481ba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="xpath-namespace-navigation"></a>Namespace XPath navigace
Chcete-li používat dotazy jazyka XPath s dokumenty XML, budete muset správně adres obory názvů XML a elementů obsažených ve obory názvů. Obory názvů zabránilo nejednoznačnosti, které může dojít, když se názvy jsou použity v více než jeden kontextu; například název `ID` mohou odkazovat na více než jeden identifikátor přidružený ke různé prvky dokumentu XML. Syntaxe Namespace určuje identifikátory URI, názvů a předpony, které rozlišení prvků dokument XML.  
  
 V příkladu v tomto tématu demonstruje použití předpony v dokumentu XML se navigace <xref:System.Xml.XPath.XPathNavigator>. Další informace o syntaxi a obory názvů najdete v tématu [obory názvů XML](http://go.microsoft.com/fwlink/?linkid=140245).  
  
## <a name="namespace-declarations"></a>Namespace – deklarace  
 Namespace – deklarace Zkontrolujte elementy dokumentu XML odlišit a adresovatelné při použití instance <xref:System.Xml.XPath.XPathNavigator>. Namespace předpony zadejte stručný syntaxe pro adresování obory názvů.  
  
 Formuláře jsou definovány předpony: `<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.` v této syntaxe předponu "`e`" je zkratka pro formální identifikátor URI oboru názvů. Můžete identifikovat `Body` element jako člena `Envelope` oboru názvů pomocí syntaxe: `e:Body`.  
  
 V následujícím dokumentu XML se bude odkazovat jako `response.xml` v příkladu navigace v další části.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<e:Envelope xmlns:e="http://schemas.xmlsoap.org/soap/envelope/">  
  <e:Body>  
    <s:Search xmlns:s="http://schemas.microsoft.com/v1/Search">  
      <r:request xmlns:r="http://schemas.microsoft.com/v1/Search/metadata"   
                 xmlns:i="http://www.w3.org/2001/XMLSchema-instance">  
      </r:request>  
    </s:Search>  
  </e:Body>  
</e:Envelope>  
```  
  
## <a name="navigation-by-namespace-prefix"></a>Navigace podle předpony Namespace  
 Kód v této části používá <xref:System.Xml.XPath.XPathNavigator> a <xref:System.Xml.XmlNamespaceManager> objektů k výběru `Search` elementu z dokumentu XML v předchozí části. Dotaz `xpath` zahrnuje předpony oboru názvů na každý prvek v cestě. Určení přesné identity obory názvů, které obsahují každý prvek zaručuje správné navigace k `Search` element podle <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> metoda.  
  
```  
using (XmlReader reader = XmlReader.Create("response.xml"))  
            {  
                XPathDocument doc = new XPathDocument(reader);  
                XPathNavigator nav = doc.CreateNavigator();  
                XmlNamespaceManager nsmgr =  
                         new XmlNamespaceManager(nav.NameTable);  
                nsmgr.AddNamespace("e",   
                         @"http://schemas.xmlsoap.org/soap/envelope/");  
                nsmgr.AddNamespace("s",   
                            @"http://schemas.microsoft.com/v1/Search");  
                nsmgr.AddNamespace("r",   
                   @"http://schemas.microsoft.com/v1/Search/metadata");  
                nsmgr.AddNamespace("i",   
                         @"http://www.w3.org/2001/XMLSchema-instance");  
  
                string xpath = "/e:Envelope/e:Body/s:Search";  
  
                XPathNavigator element = nav.SelectSingleNode(xpath, nsmgr);  
  
                Console.WriteLine("Element Prefix:" + element.Prefix +   
                           " Local name:" + element.LocalName);  
                Console.WriteLine("Namespace URI: " +   
                            element.NamespaceURI);  
  
            }  
```  
  
 Přesnost plně kvalifikované názvy oborů názvů a je větší než pro vaše pohodlí. Trochu experimenty s definice dokumentu a kódu v předchozích příkladech ověří, že navigační bez element plně kvalifikované názvy vyvolá výjimek. Například definice elementu: `<Search xmlns="http://schemas.microsoft.com/v1/Search">`a dotazů: řetězec `xpath = "/s:Envelope/s:Body/Search";` bez Předpona oboru názvů na `Search` element vrátí `null` místo `Search` elementu.  
  
## <a name="see-also"></a>Viz také  
 [Přístup k datům XML pomocí objektem XPathNavigator nastaveným na](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 [Výběr, Evaluating a porovnávání dat XML pomocí objektem XPathNavigator nastaveným na](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
