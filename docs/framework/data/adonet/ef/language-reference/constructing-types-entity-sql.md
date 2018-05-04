---
title: Vytváření typů (entita SQL)
ms.date: 03/30/2017
ms.assetid: 41fa7bde-8d20-4a3f-a3d2-fb791e128010
ms.openlocfilehash: 91ed123132965353ff354282f6850e9ef9cba3d0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="constructing-types-entity-sql"></a>Vytváření typů (entita SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] poskytuje tři druhy konstruktory: řádek konstruktory, pojmenovaného typu konstruktorů a konstruktorů kolekce.  
  
## <a name="row-constructors"></a>Řádek konstruktory  
 Použití konstruktorů řádek v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] vytvořit anonymní, strukturálně typové záznamů z jednoho nebo více hodnot. Výsledný typ konstruktor row je typu řádku, jehož pole typy odpovídají typům použitý k vytvoření řádek hodnot. Například následující výraz vytvoří hodnotu typu `Record(a int, b string, c int)`:  
  
 `ROW(1 AS a, "abc" AS b, a + 34 AS c)`  
  
 Pokud nezadáte alias pro výraz v konstruktoru row, rozhraní Entity Framework se pokusí vygenerovat. Další informace najdete v části "Pravidla pro aliasy" v [identifikátory](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).  
  
 Následující pravidla platí při aliasy výrazu v konstruktoru řádku:  
  
-   Výrazy v konstruktoru row nelze odkazovat na jiné aliasy v konstruktoru stejné.  
  
-   Dvou výrazů ve stejné konstruktor row nemůže mít stejný alias.  
  
 Další informace o řádku konstruktory najdete v tématu [řádek](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).  
  
## <a name="collection-constructors"></a>Kolekce konstruktory  
 Použití konstruktorů kolekce v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] k vytvoření instance multimnožina ze seznamu hodnot. Všechny hodnoty v konstruktoru musí být vzájemně kompatibilní typu `T`, a konstruktoru vytvoří kolekci typu `Multiset<T>`. Například následující výraz vytvoří kolekci celých čísel:  
  
 `Multiset(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
 Prázdný multiset konstruktory nejsou povoleny, protože nelze určit typ elementů. Toto není platná:  
  
 `multiset() {}`  
  
 Další informace najdete v tématu [MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md).  
  
## <a name="named-type-constructors-namedtype-initializers"></a>Konstruktory pojmenovaného typu (NamedType inicializátory)  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Umožňuje konstruktory typu (inicializátory) k vytvoření instancí s názvem komplexní typy a typy entit. Například následující výraz vytvoří instanci `Person` typu.  
  
 `Person("abc", 12)`  
  
 Následující výraz vytvoří instanci komplexního typu.  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 Následující výraz vytvoří instanci vnořené komplexního typu.  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 Následující výraz vytvoří instanci entity s vnořené komplexního typu.  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 Následující příklad ukazuje, jak k chybě při inicializaci vlastnosti pro komplexní typ na hodnotu null. `MyModel.ZipCode(‘98118’, null)`  
  
 Argumenty pro konstruktor se předpokládá, že se ve stejném pořadí jako deklaraci atributy typu.  
  
 Další informace najdete v tématu [konstruktor typu s názvem](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md).  
  
## <a name="see-also"></a>Viz také  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Přehled Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [Systém typů](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)
