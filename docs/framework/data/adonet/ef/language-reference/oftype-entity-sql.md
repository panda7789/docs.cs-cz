---
title: OFTYPE (entita SQL)
ms.date: 03/30/2017
ms.assetid: 6d259ca7-bbf0-40f8-a154-181d25c0d67e
ms.openlocfilehash: e33d613f290338d63a232bf78e7ebd0826c19897
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32764119"
---
# <a name="oftype-entity-sql"></a>OFTYPE (entita SQL)
Vrátí kolekci objektů z výrazu dotazu, který je určitého typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
OFTYPE ( expression, [ONLY] test_type )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný dotaz výraz, který vrátí kolekci objektů.  
  
 `test_type`  
 Typ k otestování každý objekt vrácený `expression` proti. Typ musí být kvalifikován obor názvů.  
  
## <a name="return-value"></a>Návratová hodnota  
 Kolekce objektů, které jsou typu `test_type`, nebo základní typ nebo typ odvozené `test_type`. Pokud je zadána pouze, pouze instance služby `test_type` nebo vrátí prázdnou kolekci.  
  
## <a name="remarks"></a>Poznámky  
 `OFTYPE` Výraz Určuje výraz typu, který je vydán Pokud chcete provést test typ proti každý prvek kolekce.  `OFTYPE` Výraz vytvoří novou kolekci obsahující pouze elementy, které byly buď zadaný typ odpovídá typu nebo dílčí typ ho.  
  
 `OFTYPE` Výrazu je zkratkou následující výrazu dotazu:  
  
```  
select value treat(t as T) from ts as t where t is of (T)  
```  
  
 Vzhledem k tomu, že správce je podtypem zaměstnanců, následující výraz vytvoří kolekci pouze správce z kolekce zaměstnanců:  
  
```  
OfType(employees, NamespaceName.Manager)  
```  
  
 Je také možné až přetypování kolekce pomocí filtru typu:  
  
```  
OfType(executives, NamespaceName.Manager)  
```  
  
 Vzhledem k tomu, že všechny vedení správci, výsledná kolekce stále obsahuje všechny původní vedení, i když kolekce je nyní zadán jako kolekce správce.  
  
 Následující tabulka uvádí chování `OFTYPE` operátor přes některé vzory. Před vyvoláním zprostředkovatele, jsou všechny výjimky vyvolány ze strany klienta:  
  
|Vzor|Chování|  
|-------------|--------------|  
|OFTYPE(Collection(EntityType), EntityType)|Položku Collection(EntityType)|  
|OFTYPE(Collection(complexType), ComplexType)|Vyvolá|  
|OFTYPE(Collection(RowType), RowType)|Vyvolá|  
  
## <a name="example"></a>Příklad  
 Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazu pomocí operátoru OFTYPE vracet kolekci OnsiteCourse objekty z kolekce samozřejmě objekty. Dotaz je na základě [školní modelu](http://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac).  
  
 [!code-csharp[DP EntityServices Concepts 2#OFTYPE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#oftype)]  
  
## <a name="see-also"></a>Viz také  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
