---
title: Přehled LINQ to XML osy (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9161f151-cfa8-4408-94ba-08a9ba3a486d
ms.openlocfilehash: 43649800869f4829d56977f1e6e62d30192b0604
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44128797"
---
# <a name="linq-to-xml-axes-overview-visual-basic"></a>Přehled LINQ to XML osy (Visual Basic)
Po vytvoření stromu XML nebo načíst dokument XML do stromu XML, můžete ho najít prvky a atributy a jejich hodnoty získat dotazovat. Načtení kolekce prostřednictvím *metody osy*, označované také jako *osy*. Některé osy jsou metody v <xref:System.Xml.Linq.XElement> a <xref:System.Xml.Linq.XDocument> třídy, který vrací <xref:System.Collections.Generic.IEnumerable%601> kolekce. Některé osy jsou metody rozšíření v <xref:System.Xml.Linq.Extensions> třídy. Osy, které jsou implementovány jako metody rozšíření pracují s kolekcemi a vrací kolekce.  
  
 Jak je popsáno v [přehled třídy XElement](../../../../visual-basic/programming-guide/concepts/linq/xelement-class-overview.md), <xref:System.Xml.Linq.XElement> objekt představuje jeden element uzel. Obsah elementu může být složité (říká se jim Strukturovaný obsah), nebo může být jednoduchý prvek. Jednoduchý prvek může být prázdný nebo obsahovat hodnotu. Pokud uzel obsahuje Strukturovaný obsah, můžete použít různé metody osy načíst výčty následovnické elementy. Nejčastěji používané osy metody jsou <xref:System.Xml.Linq.XContainer.Elements%2A> a <xref:System.Xml.Linq.XContainer.Descendants%2A>.  
  
 Kromě metod osy, které vracejí kolekce, jsou dvě další metody, které se běžně používají v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazy. <xref:System.Xml.Linq.XContainer.Element%2A> Metoda vrací jedinou <xref:System.Xml.Linq.XElement>. <xref:System.Xml.Linq.XElement.Attribute%2A> Metoda vrací jedinou <xref:System.Xml.Linq.XAttribute>.  
  
 Pro celou řadu účelů [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy poskytují nejúčinnější způsob, jak prozkoumat větve, z něj extrahovat data a transformovali je. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy pracovat s objekty, které implementují <xref:System.Collections.Generic.IEnumerable%601>a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] OS vrátit <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> kolekce, a <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XAttribute> kolekce. Je nutné tyto kolekce můžete provádět vaše dotazy.  
  
 Kromě metod osy načtení kolekce elementů a atributů způsoby osy, které umožňují iteraci v rámci stromu podrobně skvělé. Například místo práci s prvky a atributy, můžete pracovat s uzly stromu. Uzly jsou jemnější úrovni členitosti než elementů a atributů. Při práci s uzly, můžete zkontrolovat komentáře XML, textové uzly, zpracování pokyny a další. Tato funkce je důležitá, například někomu, kdo je psaní textový procesor a chce, aby se k uložení dokumentů ve formátu XML. Ale většinou programátorů XML se především soustředí elementů, atributů a jejich hodnoty.  
  
## <a name="methods-for-retrieving-a-collection-of-elements"></a>Metody pro načtení kolekce elementů  
 Tady je uveden seznam metod <xref:System.Xml.Linq.XElement> třídy (nebo její základní třídy), které volají na <xref:System.Xml.Linq.XElement> vrátit kolekci elementů.  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|Vrátí <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> z předchůdce tohoto elementu. Vrátí přetížení <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> z předchůdce, které mají zadanou <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>|Vrátí <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> podřízené položky tohoto elementu. Vrátí přetížení <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> podřízené položky, které mají zadanou <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|Vrátí <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> z podřízených prvků tohoto prvku. Vrátí přetížení <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> z podřízených prvků, které mají zadanou <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType>|Vrátí <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> prvků, které následují po tomto prvku. Vrátí přetížení <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> prvků po tomto elementu, které mají zadanou <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType>|Vrátí <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> prvky, které jsou před tímto prvkem. Vrátí přetížení <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> prvky před tímto prvkem, které mají zadanou <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|Vrátí <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> z tohoto elementu a jeho nadřazenými prvky. Vrátí přetížení <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> prvky, které mají zadanou <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType>|Vrátí <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> tento element a jejích potomků. Vrátí přetížení <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> prvky, které mají zadanou <xref:System.Xml.Linq.XName>.|  
  
## <a name="method-for-retrieving-a-single-element"></a>Metoda pro načtení jednoho elementu  
 Následující metoda načte jednu podřízenou ze <xref:System.Xml.Linq.XElement> objektu.  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=nameWithType>|Vrací prvního podřízeného <xref:System.Xml.Linq.XElement> objekt, který má zadaný <xref:System.Xml.Linq.XName>.|  
  
## <a name="method-for-retrieving-a-collection-of-attributes"></a>Metoda pro načtení kolekce atributů  
 Následující metoda načte atributy ze <xref:System.Xml.Linq.XElement> objektu.  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|Vrátí <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XAttribute> všech atributů.|  
  
## <a name="method-for-retrieving-a-single-attribute"></a>Metoda pro načtení jednoho atributu  
 Následující metoda načte jeden atribut ze <xref:System.Xml.Linq.XElement> objektu.  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>|Vrátí <xref:System.Xml.Linq.XAttribute> , který má zadaný <xref:System.Xml.Linq.XName>.|  
  
## <a name="see-also"></a>Viz také:

- [Osy LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
