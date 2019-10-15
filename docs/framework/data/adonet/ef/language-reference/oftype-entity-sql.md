---
title: OFTYPE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 6d259ca7-bbf0-40f8-a154-181d25c0d67e
ms.openlocfilehash: f1dd5ba92c7b1eaf7117c9732a78e04e5d5a317a
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319459"
---
# <a name="oftype-entity-sql"></a>OFTYPE (Entity SQL)
Vrátí kolekci objektů z výrazu dotazu, který je určitého typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
OFTYPE ( expression, [ONLY] test_type )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz dotazu, který vrací kolekci objektů.  
  
 `test_type`  
 Typ pro otestování všech objektů vrácených `expression` proti. Typ musí být kvalifikován oborem názvů.  
  
## <a name="return-value"></a>Návratová hodnota  
 Kolekce objektů, které jsou typu `test_type` nebo základní typ nebo odvozený typ `test_type`. Pokud je zadáno pouze, budou vráceny pouze instance `test_type` nebo prázdné kolekce.  
  
## <a name="remarks"></a>Poznámky  
 Výraz `OFTYPE` určuje výraz typu, který je vystaven pro provedení testu typu proti jednotlivým prvkům kolekce.  Výraz `OFTYPE` vytvoří novou kolekci zadaného typu obsahující pouze prvky, které byly buď ekvivalentní tomuto typu, nebo dílčímu typu.  
  
 Výraz `OFTYPE` je zkratkou následujícího výrazu dotazu:  
  
```sql  
select value treat(t as T) from ts as t where t is of (T)  
```  
  
 Vzhledem k tom, že manažer je podtypu zaměstnance, vytvoří následující výraz kolekci pouze správců z kolekce zaměstnanců:  
  
```sql  
OfType(employees, NamespaceName.Manager)  
```  
  
 Je také možné přetypování kolekce pomocí filtru typů:  
  
```sql
OfType(executives, NamespaceName.Manager)  
```  
  
 Vzhledem k tomu, že všichni vedoucí pracovníci jsou manažeři, výsledná kolekce stále obsahuje všechny původní vedoucí pracovníky, i když je kolekce teď zadaná jako kolekce manažerů.  
  
 Následující tabulka ukazuje chování operátoru `OFTYPE` v některých vzorcích. Všechny výjimky jsou vyvolány na straně klienta před vyvoláním poskytovatele:  
  
|Vzor|Předvídatelně|  
|-------------|--------------|  
|OFTYPE (EntityType), EntityType)|Kolekce (EntityType)|  
|OFTYPE (Collection), ComplexType)|Vyvolá|  
|OFTYPE (Collection (RowType); RowType)|Vyvolá|  
  
## <a name="example"></a>Příklad  
 Následující dotaz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] používá operátor OFTYPE k vrácení kolekce objektů OnsiteCourse z kolekce objektů kurzu. Dotaz je založen na [školním modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).  
  
 [!code-sql[DP EntityServices Concepts#OFTYPE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#oftype)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
