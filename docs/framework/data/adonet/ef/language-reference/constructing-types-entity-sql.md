---
title: Vytváření typů (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 41fa7bde-8d20-4a3f-a3d2-fb791e128010
ms.openlocfilehash: 7113aaf1c2caa982a8ab4751928856c1271570cb
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251123"
---
# <a name="constructing-types-entity-sql"></a>Vytváření typů (Entity SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]poskytuje tři druhy konstruktorů: konstruktory řádků, pojmenované typové konstruktory a konstruktory kolekcí.  
  
## <a name="row-constructors"></a>Konstruktory řádků  
 Konstruktory řádků v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nástroji slouží k vytváření anonymních strukturovaných typů záznamů z jedné nebo více hodnot. Typ výsledku konstruktoru řádku je typ řádku, jehož typy polí odpovídají typům hodnot, které slouží k vytvoření řádku. Například následující výraz vytvoří hodnotu typu `Record(a int, b string, c int)`:  
  
 `ROW(1 AS a, "abc" AS b, a + 34 AS c)`  
  
 Pokud neposkytnete alias pro výraz v konstruktoru řádku, Entity Framework se pokusí jednu vygenerovat. Další informace najdete v části pravidla aliasing v tématu [identifikátory](identifiers-entity-sql.md).  
  
 Následující pravidla platí pro aliasy výrazů v konstruktoru řádku:  
  
- Výrazy v konstruktoru řádku nemůžou odkazovat na jiné aliasy ve stejném konstruktoru.  
  
- Dva výrazy v konstruktoru stejného řádku nemohou mít stejný alias.  
  
 Další informace o konstruktorech řádků naleznete v tématu [řádek](row-entity-sql.md).  
  
## <a name="collection-constructors"></a>Konstruktory kolekcí  
 Konstruktory kolekce v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nástroji slouží k vytvoření instance multiset ze seznamu hodnot. Všechny hodnoty v konstruktoru musí být vzájemně kompatibilního typu `T`a konstruktor vytvoří kolekci typu. `Multiset<T>` Například následující výraz vytvoří kolekci celých čísel:  
  
 `Multiset(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
 Prázdné konstruktory multiset nejsou povoleny, protože nelze určit typ elementů. Následující není platný:  
  
 `multiset() {}`  
  
 Další informace najdete v tématu [MULTISET](multiset-entity-sql.md).  
  
## <a name="named-type-constructors-namedtype-initializers"></a>Konstruktory pojmenovaného typu (Inicializátory NamedType)  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]povoluje konstruktory typů (Inicializátory) k vytváření instancí pojmenovaných komplexních typů a typů entit. Například následující výraz vytvoří instanci `Person` typu.  
  
 `Person("abc", 12)`  
  
 Následující výraz vytvoří instanci komplexního typu.  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 Následující výraz vytvoří instanci vnořeného komplexního typu.  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 Následující výraz vytvoří instanci entity s vnořeným komplexním typem.  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 Následující příklad ukazuje, jak inicializovat vlastnost komplexního typu na hodnotu null. `MyModel.ZipCode(‘98118’, null)`  
  
 Předpokládá se, že argumenty konstruktoru jsou ve stejném pořadí jako deklarace atributů typu.  
  
 Další informace naleznete v tématu [konstruktor pojmenovaného typu](named-type-constructor-entity-sql.md).  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
- [Přehled Entity SQL](entity-sql-overview.md)
- [Systém typů](type-system-entity-sql.md)
