---
title: Namespace XPath navigace
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 06cc7abb-7416-415c-9dd6-67751b8cabd5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fed73c0a9c9bb4fba2644d76f470a8bdcace2b83
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572925"
---
# <a name="xpath-namespace-navigation"></a>Namespace XPath navigace
Chcete-li používat dotazy jazyka XPath s dokumenty XML, budete muset správně adres obory názvů XML a elementů obsažených ve obory názvů. Obory názvů zabránilo nejednoznačnosti, které může dojít, když se názvy jsou použity v více než jeden kontextu; například název `ID` mohou odkazovat na více než jeden identifikátor přidružený ke různé prvky dokumentu XML. Syntaxe Namespace určuje identifikátory URI, názvů a předpony, které rozlišení prvků dokument XML.  
  
 V příkladu v tomto tématu demonstruje použití předpony v dokumentu XML se navigace <xref:System.Xml.XPath.XPathNavigator>. Další informace o syntaxi a obory názvů najdete v tématu [obory názvů XML](https://msdn.microsoft.com/library/aa468565.aspx).  
  
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
 [Přístup k datům XML pomocí XPathNavigator](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 [Výběr, vyhodnocení a spárování dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
