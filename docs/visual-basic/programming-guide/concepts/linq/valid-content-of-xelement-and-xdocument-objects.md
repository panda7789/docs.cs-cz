---
title: Platný obsah XElement a XDocument Objects2
ms.date: 07/20/2015
ms.assetid: 400bb692-478a-40b6-ac1b-4ccbb4cbbd02
ms.openlocfilehash: bb5dda6bee0863a2ef951975e92c55184df9d516
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58828797"
---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a>Platný obsah objektů XElement a XDocument
Toto téma popisuje platné argumenty, které mohou být předány konstruktorů a metod, které použijete k přidání obsahu do prvků a dokumenty.  
  
## <a name="valid-content"></a>Platný obsah  
 Dotazy často vyhodnotit <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> nebo <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XAttribute>. Můžete předat kolekce <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XAttribute> objektů <xref:System.Xml.Linq.XElement> konstruktoru. Proto je vhodné pro předání výsledky dotazu jako obsah do metody a konstruktory, které můžete použít k naplnění stromů XML.  
  
 Při přidání jednoduchého obsahu, může být předán různé typy v této metodě. Platné typy zahrnují následující:  
  
-   <xref:System.String>  
  
-   <xref:System.Double>  
  
-   <xref:System.Single>  
  
-   <xref:System.Decimal>  
  
-   <xref:System.Boolean>  
  
-   <xref:System.DateTime>  
  
-   <xref:System.TimeSpan>  
  
-   <xref:System.DateTimeOffset>  
  
-   Libovolný typ, který implementuje `Object.ToString`.  
  
-   Libovolný typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601>.  
  
 Při přidávání komplexní obsahu, různé typy lze předat tuto metodu:  
  
-   <xref:System.Xml.Linq.XObject>  
  
-   <xref:System.Xml.Linq.XNode>  
  
-   <xref:System.Xml.Linq.XAttribute>  
  
-   Libovolný typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601>  
  
 Pokud objekt implementuje <xref:System.Collections.Generic.IEnumerable%601>, je vytvořena kolekce v objektu a jsou přidány všechny položky v kolekci. Pokud kolekce obsahuje <xref:System.Xml.Linq.XNode> nebo <xref:System.Xml.Linq.XAttribute> objekty, každá položka v kolekci se přidá samostatně. Pokud kolekce obsahuje text (nebo objekty, které jsou převedeny na text), je text v kolekci zřetězit a přidat jako jeden textový uzel.  
  
 Pokud je obsah `null`, není nic přidáno. Při předání kolekce položek v kolekci může být `null`. A `null` položky v kolekci nemá žádný vliv na stromové struktuře.  
  
 Přidání atributu musí mít jedinečný název v rámci svého nadřazeného prvku.  
  
 Při přidávání <xref:System.Xml.Linq.XNode> nebo <xref:System.Xml.Linq.XAttribute> objektů, pokud se nový obsah nemá žádný nadřazený objekt, pak objekty jednoduše připojeny ke stromu XML. Pokud nový obsah už je nadřazena a je součástí jiného stromu XML, poté klonovat nový obsah a nově naklonovaného obsahu je připojen ke stromu XML.  
  
## <a name="valid-content-for-documents"></a>Platný obsah pro dokumenty  
 Atributy a jednoduchý obsah nelze přidat do dokumentu.  
  
 Nejsou k dispozici mnoho scénářů, které vyžadují, abyste k vytvoření <xref:System.Xml.Linq.XDocument>. Místo toho je možné vytvářet vaše stromů XML s <xref:System.Xml.Linq.XElement> kořenový uzel. Pokud nemáte konkrétní požadavek na vytvoření dokumentu (například proto budete muset vytvořit pokyny pro zpracování a komentáře na nejvyšší úrovni, nebo máte pro podporu typů dokumentů), často je vhodné použít <xref:System.Xml.Linq.XElement> jako kořenový uzel.  
  
 Platný obsah pro dokument obsahuje následující:  
  
-   Nula nebo jedna <xref:System.Xml.Linq.XDocumentType> objekty. Typy dokumentů musí předcházet elementu.  
  
-   Žádný nebo jeden element.  
  
-   Nula nebo více komentářů.  
  
-   Nula nebo více pokyny pro zpracování.  
  
-   Nula nebo více textové uzly obsahující jenom prázdné znaky.  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a>Konstruktory a funkce, které umožňují přidávání obsahu  
 Následující metody umožňují přidat podřízený obsah do <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument>:  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.%23ctor%2A>|Vytvoří <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XDocument.%23ctor%2A>|Vytvoří <xref:System.Xml.Linq.XDocument>.|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|Přidá na konec podřízený obsah <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument>.|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|Přidá obsah po <xref:System.Xml.Linq.XNode>.|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|Přidá obsah před <xref:System.Xml.Linq.XNode>.|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|Přidá obsah na začátku podřízený obsah <xref:System.Xml.Linq.XContainer>.|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A>|Nahradí veškerý obsah (podřízených uzlů a atributy) ze <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A>|Nahradí atributy <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A>|Nahradí nový obsah podřízených uzlů.|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A>|Nahradí uzlu nový obsah.|  
  
## <a name="see-also"></a>Viz také:

- [Vytváření stromů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
