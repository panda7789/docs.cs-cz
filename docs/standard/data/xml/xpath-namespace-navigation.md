---
title: Navigace XPath Namespace
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 06cc7abb-7416-415c-9dd6-67751b8cabd5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e6d4f63dacc09208176b47dbca38783f1e9bc0a1
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44194704"
---
# <a name="xpath-namespace-navigation"></a>Navigace XPath Namespace
Používat dotazy jazyka XPath dokumentů XML, budete muset správnému adresování obory názvů XML a elementů obsažených ve obory názvů. Obory názvů zabraňují nejasnostem, které může dojít, když názvy se používají ve více než jednom kontextu; například název `ID` mohou odkazovat na více než jeden identifikátor přidružený k jiné prvky dokumentu XML. Syntaxe Namespace určuje identifikátory URI, názvů a předpony, které rozlišení prvků dokumentu XML.  
  
 V příkladu v tomto tématu ukazuje použití předpony v navigaci dokument XML s <xref:System.Xml.XPath.XPathNavigator>. Další informace o syntaxi a obory názvů, naleznete v tématu [obory názvů XML](https://msdn.microsoft.com/library/aa468565.aspx).  
  
## <a name="namespace-declarations"></a>Deklarace Namespace  
 Deklarací Namespace zkontrolujte elementů dokumentu XML odlišitelným a adresovatelný při použití instance <xref:System.Xml.XPath.XPathNavigator>. Namespace předpony poskytují stručné syntaxe pro adresování obory názvů.  
  
 Předpony, které jsou definovány pomocí formuláře: `<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.` v této syntaxe předponu "`e`" je zkratka pro formální identifikátor URI oboru názvů. Můžete určit `Body` element jako člen `Envelope` oboru názvů pomocí syntaxe: `e:Body`.  
  
 Následujícího dokumentu XML se bude odkazovat jako `response.xml` v příkladu navigace v další části.  
  
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
 Kód v této části používá <xref:System.Xml.XPath.XPathNavigator> a <xref:System.Xml.XmlNamespaceManager> objektů k výběru `Search` elementu z dokumentu XML v předchozí části. Dotaz `xpath` obsahuje obor názvů předpony na každý prvek v cestě. Určení přesné identity obory názvů, které obsahují každý prvek zaručuje správnou navigaci na `Search` elementu podle <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> metoda.  
  
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
  
 Přesnost plně kvalifikované názvy a obory názvů je větší než usnadnění. Malým množstvím experimentování s využitím definice dokumentu a kód v předchozích příkladech se ověří, že navigace bez názvů plně kvalifikovaný element vyvolá výjimky. Například definice prvku: `<Search xmlns="http://schemas.microsoft.com/v1/Search">`a dotazů: řetězec `xpath = "/s:Envelope/s:Body/Search";` bez předpony oboru názvů na `Search` element vrátí `null` místo `Search` elementu.  
  
## <a name="see-also"></a>Viz také:

- [Přístup k datům XML pomocí XPathNavigator](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
- [Výběr, vyhodnocení a spárování dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
