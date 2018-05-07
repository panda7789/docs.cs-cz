---
title: Platný obsah XElement a XDocument Objects2
ms.date: 07/20/2015
ms.assetid: 400bb692-478a-40b6-ac1b-4ccbb4cbbd02
ms.openlocfilehash: 4b1d588f0ebbfec6d5cf7a58b63f92005db75acc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a>Platný obsah XElement a XDocument objektů
Toto téma popisuje platné argumenty, které lze předat konstruktorů a metod, které můžete použít k přidání obsahu do elementů a dokumenty.  
  
## <a name="valid-content"></a>Platný obsah  
 Dotazy často vyhodnocení <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> nebo <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XAttribute>. Můžete předat kolekce <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XAttribute> objekty ke <xref:System.Xml.Linq.XElement> konstruktor. Proto je vhodné k předání výsledků dotazu jako obsah do metod a konstruktory, které můžete použít k naplnění stromy XML.  
  
 Při přidávání jednoduchým obsahem, může být různých typů předané této metodě. Platné typy jsou následující:  
  
-   <xref:System.String>  
  
-   <xref:System.Double>  
  
-   <xref:System.Single>  
  
-   <xref:System.Decimal>  
  
-   <xref:System.Boolean>  
  
-   <xref:System.DateTime>  
  
-   <xref:System.TimeSpan>  
  
-   <xref:System.DateTimeOffset>  
  
-   Žádný typ, který implementuje `Object.ToString`.  
  
-   Žádný typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601>.  
  
 Při přidávání složitým obsahem, může být různých typů předaná této metodě:  
  
-   <xref:System.Xml.Linq.XObject>  
  
-   <xref:System.Xml.Linq.XNode>  
  
-   <xref:System.Xml.Linq.XAttribute>  
  
-   Žádný typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601>  
  
 Pokud objekt implementuje <xref:System.Collections.Generic.IEnumerable%601>, je vytvořena kolekce v objektu, a jsou přidány všechny položky v kolekci. Pokud kolekce obsahuje <xref:System.Xml.Linq.XNode> nebo <xref:System.Xml.Linq.XAttribute> objekty, každá položka v kolekci se přidá samostatně. Pokud kolekce obsahuje text (nebo objekty, které jsou převedeny na text), je text v kolekci zřetězených a přidat jako uzel jednoho textu.  
  
 Pokud je obsah `null`, není nic přidáno. Při předávání kolekce položek v kolekci může být `null`. A `null` položky v kolekci nemá žádný vliv na stromu.  
  
 Přidání atributu musí mít jedinečný název v rámci svého nadřazeného elementu.  
  
 Při přidávání <xref:System.Xml.Linq.XNode> nebo <xref:System.Xml.Linq.XAttribute> objekty, pokud nemá žádný nadřazený uzel s nový obsah, pak objekty jednoduše přiřazeny ke stromu XML. Pokud nový obsah už je nadřazena a je součástí jiného stromu XML, pak je nový obsah klonovat a nově naklonovaný obsah je připojen k stromové struktuře XML.  
  
## <a name="valid-content-for-documents"></a>Platný obsah pro dokumenty  
 Atributy a jednoduchý obsah nelze přidat do dokumentu.  
  
 Nejsou k dispozici mnoho scénářů, které vyžadují, abyste vytvořili <xref:System.Xml.Linq.XDocument>. Místo toho je možné vytvářet vaše stromy XML s <xref:System.Xml.Linq.XElement> kořenový uzel. Pokud máte specifické požadavky pro vytvoření dokumentu (například proto je nutné vytvořit pokyny pro zpracování a komentáře na nejvyšší úrovni, nebo nemáte k podpoře typů dokumentů), je často vhodnější použít <xref:System.Xml.Linq.XElement> jako kořenový uzel.  
  
 Platný obsah pro dokument obsahuje následující:  
  
-   Nula nebo jedna <xref:System.Xml.Linq.XDocumentType> objekty. Element musí předcházet typů dokumentů.  
  
-   Nula nebo jeden element.  
  
-   Komentáře v počtu nula či více.  
  
-   Pokyny pro zpracování nula nebo více.  
  
-   Nula nebo více textové uzly, které obsahují jenom prázdné znaky.  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a>Konstruktory a funkce, které umožňují přidávání obsahu  
 Následující metody umožňují přidat podřízené obsah tak, aby <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument>:  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.%23ctor%2A>|Vytvoří <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XDocument.%23ctor%2A>|Vytvoří <xref:System.Xml.Linq.XDocument>.|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|Přidá na konec obsahu z podřízené <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument>.|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|Přidá obsah po <xref:System.Xml.Linq.XNode>.|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|Přidá obsahu před <xref:System.Xml.Linq.XNode>.|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|Přidá obsah na začátku podřízené obsah <xref:System.Xml.Linq.XContainer>.|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A>|Nahradí všechny obsah (podřízené uzly a atributy) <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A>|Nahradí atributy <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A>|Podřízené uzly nahradí nový obsah.|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A>|Nahradí uzlu nový obsah.|  
  
## <a name="see-also"></a>Viz také  
 [Vytváření stromů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
