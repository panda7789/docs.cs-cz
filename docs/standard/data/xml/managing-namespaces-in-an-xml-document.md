---
title: Správa oborů názvů v dokumentu XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 682643fc-b848-4e42-8c0d-50deeaeb5f2a
ms.openlocfilehash: b60e773183bd008c99022946a2ec53932234fe23
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289145"
---
# <a name="managing-namespaces-in-an-xml-document"></a>Správa oborů názvů v dokumentu XML
Obory názvů XML přiřadí prvky a názvy atributů v dokumentu XML s vlastními a předdefinovanými identifikátory URI. Chcete-li vytvořit tato přidružení, definujete předpony pro identifikátor URI oboru názvů a použijete tyto předpony pro kvalifikaci názvů elementů a atributů v datech XML. Obory názvů zabraňují kolizím názvů prvků a atributů a umožňují, aby elementy a atributy stejného názvu byly zpracovány a ověřovány jinak.  
  
<a name="declare"></a>
## <a name="declaring-namespaces"></a>Deklarace oborů názvů  
 Chcete-li deklarovat obor názvů pro element, použijte `xmlns:` atribut:  
  
 `xmlns:<name>=<"uri">`  
  
 kde `<name>` je předpona oboru názvů a `<"uri">` je identifikátor URI, který identifikuje obor názvů. Po deklaraci předpony ji můžete použít k získání prvků a atributů v dokumentu XML a jejich přidružení k identifikátoru URI oboru názvů. Vzhledem k tomu, že předpona oboru názvů se používá v celém dokumentu, měla by být krátká délka.  
  
 Tento příklad definuje dva `BOOK` prvky. První prvek je kvalifikován předponou, `mybook` a druhý prvek je kvalifikován předponou, `bb` . Každá předpona je přidružená k jinému identifikátoru URI oboru názvů:  
  
```xml  
<mybook:BOOK xmlns:mybook="http://www.contoso.com/books.dtd">  
<bb:BOOK xmlns:bb="urn:blueyonderairlines" />
</mybook>
```  
  
 Chcete-li označit, že element je součástí konkrétního oboru názvů, přidejte do něj předponu oboru názvů. Například pokud `Author` prvek patří do `mybook` oboru názvů, je deklarován jako `<mybook:Author>` .  
  
<a name="scope"></a>
## <a name="declaration-scope"></a>Rozsah deklarace  
 Obor názvů je platný od svého bodu deklarace až do konce elementu, ve kterém byl deklarován. V tomto příkladu se obor názvů definovaný v `BOOK` elementu nevztahuje na prvky mimo `BOOK` prvek, jako je například `Publisher` element:  
  
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
  
 Obor názvů musí být deklarován dříve, než může být použit, ale nemusí být zobrazen v horní části dokumentu XML.  
  
 Použijete-li v dokumentu XML více oborů názvů, můžete definovat jeden obor názvů jako výchozí obor názvů pro vytvoření čisticího dokumentu. Výchozí obor názvů je deklarován v kořenovém elementu a vztahuje se na všechny nekvalifikované prvky v dokumentu. Výchozí obory názvů platí pouze pro prvky, nikoli pro atributy.  
  
 Chcete-li použít výchozí obor názvů, vynechejte předponu a dvojtečku z deklarace elementu:  
  
```xml  
<BOOK xmlns="http://www.contoso.com/books.dtd">  
...
</BOOK>
```  
  
## <a name="managing-namespaces"></a>Správa oborů názvů  
 <xref:System.Xml.XmlNamespaceManager>Třída ukládá kolekci identifikátorů URI oboru názvů a jejich předpon a umožňuje vyhledat, přidat a odebrat obory názvů z této kolekce. V některých kontextech je tato třída potřebná pro lepší výkon zpracování XML. Například <xref:System.Xml.Xsl.XsltContext> Třída používá <xref:System.Xml.XmlNamespaceManager> pro podporu XPath.  
  
 Správce oboru názvů neprovádí žádné ověřování u oborů názvů, ale předpokládá, že předpony a obory názvů již byly ověřeny a odpovídají specifikaci [oborů názvů W3C](https://www.w3.org/TR/REC-xml-names/) .  
  
> [!NOTE]
> Technologie LINQ TO XML v [jazyce C#](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) a [Visual Basic](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) Nepoužívejte <xref:System.Xml.XmlNamespaceManager> ke správě oborů názvů. Informace o správě oborů názvů při použití LINQ to XML naleznete v tématu [práce s obory názvů XML (C#)](../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md) a [práce s obory názvů XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md) v dokumentaci LINQ.  
  
 Tady jsou některé úlohy správy a vyhledávání, které můžete s <xref:System.Xml.XmlNamespaceManager> třídou provádět. Další informace a příklady naleznete v odkazech na referenční stránku pro jednotlivé metody nebo vlastnosti.  
  
|Akce|Použití|  
|--------|---------|  
|Přidat obor názvů|Metoda <xref:System.Xml.XmlNamespaceManager.AddNamespace%2A>|  
|Odebrání oboru názvů|Metoda <xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A>|  
|Najít identifikátor URI pro výchozí obor názvů|<xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A>majetek|  
|Najít identifikátor URI pro předponu oboru názvů|Metoda <xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A>|  
|Vyhledání předpony pro identifikátor URI oboru názvů|Metoda <xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A>|  
|Získá seznam oborů názvů v aktuálním uzlu.|Metoda <xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A>|  
|Obor oboru názvů|<xref:System.Xml.XmlNamespaceManager.PushScope%2A>a <xref:System.Xml.XmlNamespaceManager.PopScope%2A> metody|  
|Ověří, jestli je v aktuálním oboru definovaná předpona.|Metoda <xref:System.Xml.XmlNamespaceManager.HasNamespace%2A>|  
|Získat tabulku názvů použitou k vyhledání předpon a identifikátorů URI|<xref:System.Xml.XmlNamespaceManager.NameTable%2A>majetek|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.XmlNamespaceManager>
- [Dokumenty a data XML](index.md)
