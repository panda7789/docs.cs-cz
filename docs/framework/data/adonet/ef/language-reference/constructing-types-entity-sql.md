---
title: Vytváření typů (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 41fa7bde-8d20-4a3f-a3d2-fb791e128010
ms.openlocfilehash: 53aa7fcc82a476c8b8bd87b059e08bee6741c0d9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59073777"
---
# <a name="constructing-types-entity-sql"></a>Vytváření typů (Entity SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] nabízí tři druhy konstruktory: řádek konstruktory, konstruktory s názvem typu a kolekce konstruktory.  
  
## <a name="row-constructors"></a>Řádek konstruktory  
 Použití konstruktorů řádek v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] k sestavení kompletních anonymní, strukturálně typy záznamů z jedné nebo více hodnot. Výsledný typ konstruktoru řádku je typ řádku, jejichž pole typy odpovídají typům hodnot použitých k vytvoření řádku. Například následující výraz vytvoří hodnotu typu `Record(a int, b string, c int)`:  
  
 `ROW(1 AS a, "abc" AS b, a + 34 AS c)`  
  
 Pokud nezadáte alias pro výraz v konstruktoru row, Entity Framework se pokusí vygenerovat. Další informace najdete v části "Pravidla pro aliasy" v [identifikátory](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).  
  
 Výraz aliasing v konstruktoru row platí následující pravidla:  
  
-   Výrazy v konstruktoru row nelze odkazovat na jiné aliasy v konstruktoru stejné.  
  
-   Dvou výrazů ve stejné konstruktor row nemůže mít stejný alias.  
  
 Další informace o konstruktorech řádku, naleznete v tématu [řádek](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).  
  
## <a name="collection-constructors"></a>Kolekce konstruktory  
 Použití konstruktorů kolekce v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] k vytvoření instance multisady ze seznamu hodnot. Všechny hodnoty v konstruktoru musí být typu vzájemně kompatibilní `T`, a konstruktor vytvoří kolekci typu `Multiset<T>`. Například následující výraz vytvoří kolekci celých čísel:  
  
 `Multiset(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
 Multiset – prázdný konstruktory nejsou povolené, protože nelze určit typ elementů. Toto není platná:  
  
 `multiset() {}`  
  
 Další informace najdete v tématu [MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md).  
  
## <a name="named-type-constructors-namedtype-initializers"></a>Konstruktory (NamedType inicializátory) s názvem typu  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Umožňuje konstruktory typu (inicializátory) k vytvoření instance s názvem komplexní typy a typy entit. Například následující výraz vytvoří instanci `Person` typu.  
  
 `Person("abc", 12)`  
  
 Následující výraz vytvoří instanci komplexního typu.  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 Následující výraz vytvoří instanci vnořené komplexního typu.  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 Následující výraz vytvoří instanci entity vnořené komplexního typu.  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 Následující příklad ukazuje způsob inicializace vlastností komplexního typu na hodnotu null. `MyModel.ZipCode(‘98118’, null)`  
  
 Argumenty pro konstruktor předpokládá, že jsou ve stejném pořadí jako deklarace atributy typu.  
  
 Další informace najdete v tématu [konstruktor typu s názvem](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md).  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Přehled Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [Systém typů](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)
