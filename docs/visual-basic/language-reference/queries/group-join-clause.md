---
title: Group Join – klauzule
ms.date: 07/20/2015
f1_keywords:
- vb.QueryGroupJoinIn
- vb.QueryGroupJoinOn
- vb.QueryGroupJoin
- vb.QueryGroupJoinInto
helpviewer_keywords:
- Group Join clause [Visual Basic]
- Group Join statement [Visual Basic]
- queries [Visual Basic], Group Join
ms.assetid: 37dbf79c-7b5c-421b-bbb7-dadfd2b92a1c
ms.openlocfilehash: 7916e51293c06016b2581b7109df3f0a599404ca
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359828"
---
# <a name="group-join-clause-visual-basic"></a>Group Join – klauzule (Visual Basic)
Kombinuje dvě kolekce do jedné hierarchické kolekce. Operace JOIN je založena na spárovaných klíčích.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Group Join element [As type] In collection _  
  On key1 Equals key2 [ And key3 Equals key4 [... ] ] _  
  Into expressionList  
```  
  
## <a name="parts"></a>Součásti  
  
|Pojem|Definice|  
|---|---|  
|`element`|Povinná hodnota. Řídicí proměnná pro kolekci, která je připojena.|  
|`type`|Nepovinný parametr. Typ `element` . Pokud `type` není zadán, typ `element` je odvozen z `collection` .|  
|`collection`|Povinná hodnota. Kolekce, která se má zkombinovat s kolekcí, která je na levé straně `Group Join` operátoru. `Group Join`Klauzule může být vnořena v `Join` klauzuli nebo v jiné `Group Join` klauzuli.|  
|`key1` `Equals` `key2`|Povinná hodnota. Identifikuje klíče pro připojené kolekce. `Equals`K porovnání klíčů z kolekcí, které jsou spojeny, je nutné použít operátor. Podmínky spojení můžete kombinovat pomocí `And` operátora k identifikaci více klíčů. `key1`Parametr musí být z kolekce na levé straně `Join` operátoru. `key2`Parametr musí být z kolekce na pravé straně `Join` operátoru.<br /><br /> Klíče používané v podmínce spojení mohou být výrazy, které obsahují více než jednu položku z kolekce. Každý klíčový výraz však může obsahovat pouze položky z příslušné kolekce.|  
|`expressionList`|Povinná hodnota. Jeden nebo více výrazů, které určují, jak jsou agregovány skupiny prvků z kolekce. Chcete-li identifikovat název člena pro seskupené výsledky, použijte `Group` klíčové slovo ( `<alias> = Group` ). Můžete také zahrnout agregační funkce, které se mají použít pro skupinu.|  
  
## <a name="remarks"></a>Poznámky  
 `Group Join`Klauzule kombinuje dvě kolekce na základě porovnání hodnot klíčů z připojených kolekcí. Výsledná kolekce může obsahovat člena, který odkazuje na kolekci prvků z druhé kolekce, která odpovídá hodnotě klíče z první kolekce. Můžete také zadat agregační funkce, které mají být použity pro seskupené prvky z druhé kolekce. Informace o agregačních funkcích naleznete v tématu [klauzule Aggregate](aggregate-clause.md).  
  
 Vezměte v úvahu například kolekci manažerů a kolekci zaměstnanců. Prvky z obou kolekcí mají vlastnost ManagerID, která identifikuje zaměstnance, kteří nahlásí konkrétnímu manažerovi. Výsledky operace join by obsahovaly výsledek pro každého manažera a zaměstnance s vyhovující hodnotou ManagerID. Výsledky `Group Join` operace by obsahovaly úplný seznam manažerů. Každý výsledek správce by měl člena, který odkazoval na seznam zaměstnanců, kteří byli shodou pro konkrétního manažera.  
  
 Kolekce výsledná z `Group Join` operace může obsahovat libovolnou kombinaci hodnot z kolekce identifikované v `From` klauzuli a výrazy identifikované v `Into` klauzuli `Group Join` klauzule. Další informace o platných výrazech pro `Into` klauzuli naleznete v tématu [klauzule Aggregate](aggregate-clause.md).  
  
 `Group Join`Operace vrátí všechny výsledky z kolekce identifikované na levé straně `Group Join` operátoru. To platí i v případě, že se v kolekci nevztahují žádné shody. To se podobá `LEFT OUTER JOIN` v SQL.  
  
 Klauzuli můžete použít `Join` ke kombinování kolekcí do jedné kolekce. To je ekvivalentem `INNER JOIN` v SQL.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu spojuje dvě kolekce pomocí `Group Join` klauzule.  
  
 [!code-vb[VbSimpleQuerySamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#14)]  
  
## <a name="see-also"></a>Viz také

- [Představení technologie LINQ v jazyce Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Dotazy](index.md)
- [Klauzule SELECT](select-clause.md)
- [Klauzule FROM](from-clause.md)
- [Klauzule JOIN](join-clause.md)
- [Klauzule WHERE](where-clause.md)
- [Group By – klauzule](group-by-clause.md)
