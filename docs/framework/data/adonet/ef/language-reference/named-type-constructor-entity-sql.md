---
title: Konstruktor typu s názvem (entita SQL)
ms.date: 03/30/2017
ms.assetid: 549dea04-d93d-4c87-a292-f81b1598dbfd
ms.openlocfilehash: 9ffaf55ed54e8479a56e6f9fc4d7a5efe47f8e2a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32763160"
---
# <a name="named-type-constructor-entity-sql"></a>Konstruktor typu s názvem (entita SQL)
Použít k vytvoření instance konceptuálního modelu nominální například Entity nebo komplexní typy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[{identifier. }] identifier( [expression [{, expression }]] )  
```  
  
## <a name="arguments"></a>Arguments  
 `identifier`  
 Hodnota, která je identifikátor jednoduchý nebo uvozovkách. Další informace najdete v tématu [identifikátory](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
  
 `expression`  
 Atributy typu, které se předpokládá, že se ve stejném pořadí, jak se zobrazují v deklaraci typu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Instance s názvem komplexní typy a typy entit.  
  
## <a name="remarks"></a>Poznámky  
 Následující příklady ukazují, jak vytvořit nominální a komplexní typy:  
  
 Následující výraz vytvoří instanci `Person` typu:  
  
 `Person("abc", 12)`  
  
 Následující výraz vytvoří instanci komplexního typu:  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 Následující výraz vytvoří instanci vnořené komplexního typu:  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 Následující výraz vytvoří instanci entity s vnořené komplexního typu:  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 Následující příklad ukazuje, jak k chybě při inicializaci vlastnosti pro komplexní typ na hodnotu null:`MyModel.ZipCode(‘98118’, null)`  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL konstruktor s názvem typu používá k vytvoření instance typu koncepčního modelu. Dotaz je založen na modelu prodej AdventureWorks. Pro zkompilování a spuštění tohoto dotazu, postupujte takto:  
  
1.  Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:  
  
 [!code-csharp[DP EntityServices Concepts 2#NAMED_TYPE_CONSTRUCTOR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#named_type_constructor)]  
  
## <a name="see-also"></a>Viz také  
 [Vytváření typů](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
