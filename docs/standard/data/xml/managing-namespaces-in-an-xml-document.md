---
title: Správa oborů názvů v dokumentu XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 682643fc-b848-4e42-8c0d-50deeaeb5f2a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4b0ace73d81783852242a52bec006b0ad2edaadd
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2019
ms.locfileid: "56836133"
---
# <a name="managing-namespaces-in-an-xml-document"></a>Správa oborů názvů v dokumentu XML
Obory názvů XML přidružit identifikátory URI předdefinované a vlastní názvy prvků a atributů v dokumentu XML. Tato přidružení vytvoříte definovat předpony pro obor názvů URI a použijte tyto předpony kvalifikovat názvy prvků a atributů v datech XML. Obory názvů zabránit kolize názvů prvků a atributů a povolit elementů a atributů se stejným názvem, zpracovat a ověřen jiným způsobem.  
  
<a name="declare"></a>   
## <a name="declaring-namespaces"></a>Deklarace oborů názvů  
 K deklarování oboru názvů pro element, použijete `xmlns:` atribut:  
  
 `xmlns:<name>=<"uri">`  
  
 kde `<name>` je Předpona oboru názvů a `<"uri">` je identifikátor URI pro určení oboru názvů. Po deklaraci předpona, která vám pomůže ho kvalifikovat prvkům a atributům v dokumentu XML a přidružit je k oboru názvů identifikátoru URI. Předpona oboru názvů, protože se používají v celém dokumentu by mělo být krátký délku.  
  
 Tento příklad definuje dvě `BOOK` elementy. První prvek je kvalifikována předponu, `mybook`, a druhý prvek je kvalifikována předponu, `bb`. Každou předponu je přidružen jiný obor názvů identifikátoru URI:  
  
```xml  
<mybook:BOOK xmlns:mybook="http://www.contoso.com/books.dtd">  
<bb:BOOK xmlns:bb="urn:blueyonderairlines">  
```  
  
 Chcete-li označit, že element je součástí konkrétní obor názvů, přidejte do ní Předpona oboru názvů. Například pokud `Author` element patří do `mybook` obor názvů, je deklarována jako `<mybook:Author>`.  
  
<a name="scope"></a>   
## <a name="declaration-scope"></a>Deklarace oboru  
 Obor názvů je účinné z místa deklarace až do konce element byl deklarován v. V tomto příkladu obor názvů definovaný v `BOOK` element neplatí pro prvky mimo `BOOK` elementu, například `Publisher` element:  
  
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
  
 Obor názvů musí být deklarována, než je možné, ale nemusí se zobrazí v horní části dokumentu XML.  
  
 Při použití více oborů názvů v dokumentu XML, můžete definovat jeden obor názvů jako výchozí obor názvů a vytvoříte čisticí vypadající textový dokument. Výchozí obor názvů je deklarován v kořenovém prvku a platí pro všechny nekvalifikované elementy v dokumentu. Výchozí obory názvů budou použity pouze prvky, nikoli atributů.  
  
 Pokud chcete použít výchozí obor názvů, vynechte předponu a identit od deklarace na element:  
  
```xml  
<BOOK xmlns="http://www.contoso.com/books.dtd">  
```  
  
## <a name="managing-namespaces"></a>Správa oborů názvů  
 <xref:System.Xml.XmlNamespaceManager> Třídy ukládá kolekce identifikátorů URI oboru názvů a jejich předpony a umožňuje vyhledat, přidání a odebrání oborů názvů z této kolekce. V některých kontextech Tato třída je povinné pro lepší výkon pro zpracování XML. Například <xref:System.Xml.Xsl.XsltContext> třídy používá <xref:System.Xml.XmlNamespaceManager> pro podporu jazyka XPath.  
  
 Obor názvů správce neprovede žádné ověření na obory názvů, ale předpokládá, že již byly ověřeny předpony a obory názvů a v souladu s [obory názvů W3C](https://www.w3.org/TR/REC-xml-names/) specifikace.  
  
> [!NOTE]
> [Technologie LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) a [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) nepoužívejte <xref:System.Xml.XmlNamespaceManager> ke správě oborů názvů. Zobrazit [práce s názvovými prostory XML (C#)](../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md) a [práce s názvovými prostory XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md) v LINQ dokumentaci informace o správě oborů názvů, při použití technologie LINQ to XML.  
  
 Tady jsou některé úlohy správy a vyhledávání můžete provádět pomocí <xref:System.Xml.XmlNamespaceManager> třídy. Další informace a příklady najdete na odkazech na referenční stránce pro každou metodu nebo vlastnost.  
  
|Chcete-li|Použití|  
|--------|---------|  
|Přidat obor názvů|<xref:System.Xml.XmlNamespaceManager.AddNamespace%2A> – Metoda|  
|Odebrat obor názvů|<xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A> – Metoda|  
|Najít identifikátor URI pro výchozí obor názvů|<xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A> Vlastnost|  
|Najít identifikátor URI pro předponu oboru názvů|<xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A> – Metoda|  
|Najít předponu pro obor názvů identifikátoru URI|<xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A> – Metoda|  
|Získání seznamu oborů názvů v aktuálním uzlu|<xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A> – Metoda|  
|Určení rozsahu oboru názvů|<xref:System.Xml.XmlNamespaceManager.PushScope%2A> a <xref:System.Xml.XmlNamespaceManager.PopScope%2A> metody|  
|Zkontrolujte, zda je v aktuálním oboru definovánu předponu|<xref:System.Xml.XmlNamespaceManager.HasNamespace%2A> – Metoda|  
|Získejte název tabulky použitý při vyhledávání předpon a identifikátory URI|<xref:System.Xml.XmlNamespaceManager.NameTable%2A> Vlastnost|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.XmlNamespaceManager>
- [Dokumenty a data XML](../../../../docs/standard/data/xml/index.md)
