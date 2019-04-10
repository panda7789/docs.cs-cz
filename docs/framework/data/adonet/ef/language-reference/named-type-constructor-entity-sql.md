---
title: Konstruktor pojmenovaného typu (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 549dea04-d93d-4c87-a292-f81b1598dbfd
ms.openlocfilehash: f95f0dcb92068675b2efff0af7e97b349976bf42
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59329463"
---
# <a name="named-type-constructor-entity-sql"></a>Konstruktor pojmenovaného typu (Entity SQL)
Použít k vytvoření instance nominální typy konceptuálních modelů, jako je například Entity nebo komplexní typy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[{identifier. }] identifier( [expression [{, expression }]] )  
```  
  
## <a name="arguments"></a>Arguments  
 `identifier`  
 Hodnota, která je v uvozovkách nebo jednoduchý identifikátor. Další informace najdete v tématu [identifikátory](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
  
 `expression`  
 Atributy typu, které jsou považovány za umístěné ve stejném pořadí, jak se objeví v deklaraci typu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Instance s názvem komplexní typy a typy entit.  
  
## <a name="remarks"></a>Poznámky  
 Následující příklady ukazují, jak vytvořit nominální a komplexní typy:  
  
 Výraz níže vytvoří instanci `Person` typu:  
  
 `Person("abc", 12)`  
  
 Výraz níže vytvoří instanci komplexní typ:  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 Výraz níže vytvoří instanci vnořené komplexní typ:  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 Výraz níže vytvoří instanci entity s vnořené komplexní typ:  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 Následující příklad ukazuje způsob inicializace vlastností komplexního typu na hodnotu null:`MyModel.ZipCode(‘98118’, null)`  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL používá konstruktor pojmenovaného typu k vytvoření instance typu koncepčního modelu. Dotaz je založen na modelu Sales AdventureWorks. Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:  
  
1. Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#NAMED_TYPE_CONSTRUCTOR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#named_type_constructor)]  
  
## <a name="see-also"></a>Viz také:

- [Vytváření typů](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)
- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
