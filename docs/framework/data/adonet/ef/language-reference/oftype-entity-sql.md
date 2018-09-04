---
title: OFTYPE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 6d259ca7-bbf0-40f8-a154-181d25c0d67e
ms.openlocfilehash: c90950e11cbfca7a49b505c1654d08be504990e1
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43564650"
---
# <a name="oftype-entity-sql"></a>OFTYPE (Entity SQL)
Vrátí kolekci objektů z výrazu dotazu, který je určitého typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
OFTYPE ( expression, [ONLY] test_type )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný výraz platný dotaz, který vrací kolekce objektů.  
  
 `test_type`  
 Typ, který chcete otestovat každý objekt vrácený `expression` proti. Typ musí být kvalifikován oborem názvů.  
  
## <a name="return-value"></a>Návratová hodnota  
 Kolekce objektů, které jsou typu `test_type`, nebo základního typu nebo odvozený typ `test_type`. Pokud je zadána pouze, pouze instance aplikace `test_type` nebo vrátí prázdnou kolekci.  
  
## <a name="remarks"></a>Poznámky  
 `OFTYPE` Výraz Určuje výraz typu, která je vydala pro typ testu pro každý prvek kolekce.  `OFTYPE` Výraz vytvoří novou kolekci obsahující pouze prvky, které byly buď zadaný typ odpovídá typu nebo dílčí typu.  
  
 `OFTYPE` Výraz je zkratka pro následující výraz dotazu:  
  
```  
select value treat(t as T) from ts as t where t is of (T)  
```  
  
 Vzhledem k tomu, že správce je podtypem typu zaměstnance, následující výraz vytvoří kolekci pouze správci z kolekce zaměstnanců:  
  
```  
OfType(employees, NamespaceName.Manager)  
```  
  
 Je také možné provést až přetypování pomocí filtru, který typ kolekce:  
  
```  
OfType(executives, NamespaceName.Manager)  
```  
  
 Vzhledem k tomu, že všechny vedení manažery, výsledný kolekce stále obsahuje všechny původní vedení, i když kolekce je nyní zadán jako kolekce správci.  
  
 V následující tabulce jsou uvedeny chování `OFTYPE` operátor přes některé vzory. Všechny výjimky jsou vyvolány ze strany klienta před vyvoláním zprostředkovatele:  
  
|Vzor|Chování|  
|-------------|--------------|  
|OFTYPE(Collection(EntityType), EntityType)|Položku Collection(EntityType)|  
|OFTYPE(Collection(complexType), ComplexType)|Vyvolá výjimku|  
|OFTYPE(Collection(RowType), RowType)|Vyvolá výjimku|  
  
## <a name="example"></a>Příklad  
 Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz vrací kolekce objektů OnsiteCourse z kolekce samozřejmě objekty pomocí operátoru OFTYPE. Dotaz je založen na [školní modelu](https://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac).  
  
 [!code-csharp[DP EntityServices Concepts 2#OFTYPE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#oftype)]  
  
## <a name="see-also"></a>Viz také  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
