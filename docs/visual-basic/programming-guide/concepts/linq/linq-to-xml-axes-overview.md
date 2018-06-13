---
title: Technologie LINQ to přehled osy XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9161f151-cfa8-4408-94ba-08a9ba3a486d
ms.openlocfilehash: 9164dcff118c5fa3d15a5fe673b2174a4002e9d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651437"
---
# <a name="linq-to-xml-axes-overview-visual-basic"></a>Technologie LINQ to přehled osy XML (Visual Basic)
Po vytvoření strom XML nebo načíst dokument XML do strom XML, můžete ji najít elementy a atributy a jejich hodnoty načíst dotazovat. Načíst prostřednictvím kolekce *osy metody*, označovaný také *osy*. Některé z os jsou metody v <xref:System.Xml.Linq.XElement> a <xref:System.Xml.Linq.XDocument> třídy, který vrací <xref:System.Collections.Generic.IEnumerable%601> kolekce. Některé z os jsou rozšiřující metody v <xref:System.Xml.Linq.Extensions> třídy. Osy, které jsou implementovány jako rozšiřující metody pracovat na kolekce a vrátí kolekce.  
  
 Jak je popsáno v [přehledu třídy XElement](http://msdn.microsoft.com/library/d35180fe-7016-4895-9bfc-ba1e3f7875ec), <xref:System.Xml.Linq.XElement> objekt představuje uzel s jediným elementem. Obsah elementu může být složité (někdy nazývané strukturovaných obsahu), nebo může být jednoduchý element. Jednoduché element nesmí být prázdné nebo může obsahovat hodnotu. Pokud uzel obsahuje strukturovaných obsah, můžete použít různé metody osy načíst výčty následnickým elementům. Nejčastěji používané osy metody <xref:System.Xml.Linq.XContainer.Elements%2A> a <xref:System.Xml.Linq.XContainer.Descendants%2A>.  
  
 Kromě osy metody, které vrací kolekce, jsou k dispozici dvě další metody, které se běžně používáte [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazy. <xref:System.Xml.Linq.XContainer.Element%2A> Metoda vrátí hodnotu typu single <xref:System.Xml.Linq.XElement>. <xref:System.Xml.Linq.XElement.Attribute%2A> Metoda vrátí hodnotu typu single <xref:System.Xml.Linq.XAttribute>.  
  
 Mnoho důvodů [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy poskytují nejúčinnějších způsob, jak vyhledat stromu, extrahovat data z něj a transformovat. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy na objekty, které implementují pracovat <xref:System.Collections.Generic.IEnumerable%601>a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] OS vrátit <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> kolekcí, a <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XAttribute> kolekce. Je nutné tyto kolekce a provádět své dotazy.  
  
 Kromě osy metody, které načíst kolekce elementů a atributů jsou osy metody, které vám umožní iteraci v rámci stromu příliš podrobně. Místo práci s elementů a atributů, například můžete pracovat s uzly stromu. Uzly jsou jemnějšího úrovni členitosti než elementů a atributů. Při práci s uzly, můžete zkontrolovat komentáře XML, textové uzly zpracování pokynů a další. Tato funkce je důležitá, například pro někoho, kdo je psaní textovém editoru a chce pro uložení dokumentů ve formátu XML. Většina programátory v jazyce XML jsou primárně problémem s prvky, atributy a jejich hodnoty.  
  
## <a name="methods-for-retrieving-a-collection-of-elements"></a>Metody pro získání kolekci elementů  
 Následuje souhrn metody <xref:System.Xml.Linq.XElement> – třída (nebo jejích základních tříd), zavoláte na <xref:System.Xml.Linq.XElement> vrátit kolekci elementů.  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|Vrátí <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> z nadřazených tohoto elementu. Vrátí přetížení <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> z nadřazených, které mají zadaný <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>|Vrátí <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> následovníků tohoto elementu. Vrátí přetížení <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> podřízené položky, které mají zadaný <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|Vrátí <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> podřízených elementů tohoto elementu. Vrátí přetížení <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> podřízených elementů, které mají zadaný <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType>|Vrátí <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> elementů, které následují po tohoto elementu. Vrátí přetížení <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> elementů po tohoto elementu, které mají zadaný <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType>|Vrátí <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> prvků, které dřívější než tento element. Vrátí přetížení <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> elementů před tohoto elementu, které mají zadaný <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|Vrátí <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> tento prvek a jeho předchůdců. Vrátí přetížení <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> prvků, které mají zadaný <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType>|Vrátí <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> tento prvek a jeho následníky. Vrátí přetížení <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> prvků, které mají zadaný <xref:System.Xml.Linq.XName>.|  
  
## <a name="method-for-retrieving-a-single-element"></a>Metoda pro načtení jeden Element  
 Následující metoda načte jednu podřízenou z <xref:System.Xml.Linq.XElement> objektu.  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=nameWithType>|Vrací prvního podřízeného <xref:System.Xml.Linq.XElement> objekt, který má zadaný <xref:System.Xml.Linq.XName>.|  
  
## <a name="method-for-retrieving-a-collection-of-attributes"></a>Metoda pro získání kolekce atributů  
 Následující metoda načte atributů ze <xref:System.Xml.Linq.XElement> objektu.  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|Vrátí <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XAttribute> všech atributů.|  
  
## <a name="method-for-retrieving-a-single-attribute"></a>Metoda pro načtení jeden atribut  
 Následující metoda načte jeden atribut z <xref:System.Xml.Linq.XElement> objektu.  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>|Vrátí <xref:System.Xml.Linq.XAttribute> má zadaný <xref:System.Xml.Linq.XName>.|  
  
## <a name="see-also"></a>Viz také  
 [Technologie LINQ to XML osy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
