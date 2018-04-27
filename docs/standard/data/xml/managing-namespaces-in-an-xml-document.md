---
title: Správa oborů názvů v dokumentu XML
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 682643fc-b848-4e42-8c0d-50deeaeb5f2a
caps.latest.revision: 5
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 211d4f2ee3f47e1defdc8a3bd4fc81618fa3fefd
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="managing-namespaces-in-an-xml-document"></a>Správa oborů názvů v dokumentu XML
Obory názvů XML přidružit předdefinované a vlastní identifikátory URI názvy prvků a atributů v dokumentu XML. Chcete-li vytvořit těchto přidružení, definice předpony oboru názvů identifikátory URI a používání předpon, k vyfiltrování názvy prvků a atributů v datech XML. Obory názvů zabránit elementu a atributu kolize názvů a povolte elementů a atributů se stejným názvem, zpracovávají a ověřit jinak.  
  
<a name="declare"></a>   
## <a name="declaring-namespaces"></a>Deklarace oborů názvů  
 Pro deklaraci oboru názvů na element, můžete použít `xmlns:` atribut:  
  
 `xmlns:<name>=<"uri">`  
  
 kde `<name>` je Předpona oboru názvů a `<"uri">` je identifikátor URI, který identifikuje obor názvů. Po deklarujete předponu, můžete přidružit identifikátor URI oboru názvů a kvalifikaci elementů a atributů v dokumentu XML. Protože Předpona oboru názvů se používá v celém dokumentu, mělo by být krátký délku.  
  
 Tento příklad definuje dvě `BOOK` elementy. První elementu je kvalifikovaný předponu, `mybook`, a druhý prvkem je kvalifikovaný předponu, `bb`. Každý předpona je spojena s jiný identifikátor URI oboru názvů:  
  
```xml  
<mybook:BOOK xmlns:mybook="http://www.contoso.com/books.dtd">  
<bb:BOOK xmlns:bb="urn:blueyonderairlines">  
```  
  
 Chcete-li označit, že element je součástí konkrétní obor názvů, přidejte k němu Předpona oboru názvů. Například pokud `Author` níž prvek patří `mybook` obor názvů, je deklarován jako `<mybook:Author>`.  
  
<a name="scope"></a>   
## <a name="declaration-scope"></a>Deklarace oboru  
 Obor názvů je efektivní z bodu deklarace až do konce element byla deklarována v. V tomto příkladu obor názvů definované v `BOOK` element se nevztahuje na elementy mimo `BOOK` elementu, jako `Publisher` element:  
  
```xml  
<Author>Joe Smith</Author>  
<BOOK xmlns:book="http://www.contoso.com">  
    <title>My Wonderful Day</title>  
      <price>$3.95</price>  
</BOOK>  
<Publisher>  
    <Name>MSPress</Name>  
</Publisher>  
```  
  
 Před použitím, ale nemá zobrazí v horní části dokumentu XML, musí být deklarován obor názvů.  
  
 Pokud používáte více obory názvů v dokumentu XML, můžete definovat jeden obor názvů jako výchozí obor názvů k vytvoření čisticí vypadající dokument. Výchozí obor názvů je v kořenovém elementu deklarována a platí pro všechny neúplné elementy v dokumentu. Výchozí obory názvů budou použity pouze elementy, nikoli atributy.  
  
 Chcete-li použít výchozí obor názvů, vynechejte předponu a dvojtečka z deklarace na element:  
  
```xml  
<BOOK xmlns="http://www.contoso.com/books.dtd">  
```  
  
## <a name="managing-namespaces"></a>Správa oborů názvů  
 <xref:System.Xml.XmlNamespaceManager> Třída ukládá kolekce identifikátorů URI oboru názvů a předpony a umožňuje vyhledávat, přidávat a odebírat obory názvů z této kolekce. V některých kontextech Tato třída je vyžadována pro lepší výkon zpracování XML. Například <xref:System.Xml.Xsl.XsltContext> třídy používá <xref:System.Xml.XmlNamespaceManager> pro podporu jazyka XPath.  
  
 Obor názvů manager nebude provádět žádné ověření na obory názvů, ale předpokládá, že již byla ověřena předpony a obory názvů a v souladu s [obory názvů W3C](https://www.w3.org/TR/REC-xml-names/) specifikace.  
  
> [!NOTE]
>  [Technologie LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) nepoužívá <xref:System.Xml.XmlNamespaceManager> ke správě oborů názvů. V tématu [práci s obory názvů XML](https://msdn.microsoft.com/library/e3003209-3234-45be-a832-47feb7927430) v dokumentaci k LINQ informace o správě oborů názvů při použití technologie LINQ to XML.  
  
 Tady jsou některé úlohy správy a vyhledávání můžete provádět pomocí <xref:System.Xml.XmlNamespaceManager> třídy. Další informace a příklady naleznete na následujících odkazech na odkaz na stránku pro každé metody nebo vlastnosti.  
  
|Chcete-li|Použití|  
|--------|---------|  
|Přidat obor názvů|<xref:System.Xml.XmlNamespaceManager.AddNamespace%2A> – Metoda|  
|Odebrat obor názvů|<xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A> – Metoda|  
|Najít identifikátor URI pro výchozí obor názvů|<xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A> Vlastnost|  
|Najít identifikátor URI pro předponu oboru názvů|<xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A> – Metoda|  
|Najít předponu pro identifikátor URI oboru názvů|<xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A> – Metoda|  
|Získat seznam obory názvů v aktuálním uzlu|<xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A> – Metoda|  
|Obor obor názvů|<xref:System.Xml.XmlNamespaceManager.PushScope%2A> a <xref:System.Xml.XmlNamespaceManager.PopScope%2A> metody|  
|Zkontrolujte, zda je předpona je definována v aktuálním oboru|<xref:System.Xml.XmlNamespaceManager.HasNamespace%2A> – Metoda|  
|Získejte název tabulku použita k vyhledání předpony a identifikátory URI|<xref:System.Xml.XmlNamespaceManager.NameTable%2A> Vlastnost|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.XmlNamespaceManager>  
 [Dokumenty a data XML](../../../../docs/standard/data/xml/index.md)
