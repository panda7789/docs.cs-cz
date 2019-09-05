---
title: OFTYPE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 6d259ca7-bbf0-40f8-a154-181d25c0d67e
ms.openlocfilehash: 36701a5e75e804ea541d242aaff243de0b24cec3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249798"
---
# <a name="oftype-entity-sql"></a>OFTYPE (Entity SQL)
Vrátí kolekci objektů z výrazu dotazu, který je určitého typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
OFTYPE ( expression, [ONLY] test_type )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz dotazu, který vrací kolekci objektů.  
  
 `test_type`  
 Typ pro otestování všech objektů vrácených `expression` proti. Typ musí být kvalifikován oborem názvů.  
  
## <a name="return-value"></a>Návratová hodnota  
 Kolekce objektů, které jsou typu `test_type`, nebo základní typ nebo odvozený `test_type`typ. Pokud je zadáno pouze, budou vráceny pouze instance `test_type` nebo prázdná kolekce.  
  
## <a name="remarks"></a>Poznámky  
 `OFTYPE` Výraz určuje výraz typu, který je vystaven pro provedení testu typu proti jednotlivým prvkům kolekce.  `OFTYPE` Výraz vytvoří novou kolekci zadaného typu obsahující pouze prvky, které byly buď ekvivalentní tomuto typu, nebo dílčímu typu.  
  
 `OFTYPE` Výraz je zkratkou následujícího výrazu dotazu:  
  
```  
select value treat(t as T) from ts as t where t is of (T)  
```  
  
 Vzhledem k tom, že manažer je podtypu zaměstnance, vytvoří následující výraz kolekci pouze správců z kolekce zaměstnanců:  
  
```  
OfType(employees, NamespaceName.Manager)  
```  
  
 Je také možné přetypování kolekce pomocí filtru typů:  
  
```  
OfType(executives, NamespaceName.Manager)  
```  
  
 Vzhledem k tomu, že všichni vedoucí pracovníci jsou manažeři, výsledná kolekce stále obsahuje všechny původní vedoucí pracovníky, i když je kolekce teď zadaná jako kolekce manažerů.  
  
 Následující tabulka ukazuje chování `OFTYPE` operátoru nad některými vzorci. Všechny výjimky jsou vyvolány na straně klienta před vyvoláním poskytovatele:  
  
|Vzor|Chování|  
|-------------|--------------|  
|OFTYPE (EntityType), EntityType)|Kolekce (EntityType)|  
|OFTYPE (Collection), ComplexType)|Vyvolá|  
|OFTYPE (Collection (RowType); RowType)|Vyvolá|  
  
## <a name="example"></a>Příklad  
 Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz pomocí operátoru OfType vrátí kolekci objektů OnsiteCourse z kolekce objektů kurzu. Dotaz je založen na [školním modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).  
  
 [!code-csharp[DP EntityServices Concepts 2#OFTYPE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#oftype)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
