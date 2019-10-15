---
title: Konstruktor pojmenovaného typu (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 549dea04-d93d-4c87-a292-f81b1598dbfd
ms.openlocfilehash: f40adce1a9e031ed0b7cd5d03d9c63db255aa610
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319577"
---
# <a name="named-type-constructor-entity-sql"></a>Konstruktor pojmenovaného typu (Entity SQL)
Slouží k vytváření instancí nominálních typů konceptuálního modelu, jako je například entita nebo komplexní typy.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
[{identifier. }] identifier( [expression [{, expression }]] )  
```  
  
## <a name="arguments"></a>Arguments  
 `identifier`  
 Hodnota, která je jednoduchý nebo v identifikátoru v uvozovkách. Další informace najdete v tématu [identifikátory](identifiers-entity-sql.md) .  
  
 `expression`  
 Atributy typu, které jsou považovány za stejné pořadí, jaké jsou uvedeny v deklaraci typu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Instance pojmenovaných komplexních typů a typů entit  
  
## <a name="remarks"></a>Poznámky  
 Následující příklady znázorňují způsob konstrukce nominálních a komplexních typů:  
  
 Výraz níže vytvoří instanci typu `Person`:  
  
 `Person("abc", 12)`  
  
 Výraz níže vytvoří instanci komplexního typu:  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 Výraz níže vytvoří instanci vnořeného komplexního typu:  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 Výraz níže vytvoří instanci entity s vnořeným komplexním typem:  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 Následující příklad ukazuje, jak inicializovat vlastnost komplexního typu na hodnotu null: `MyModel.ZipCode(‘98118’, null)`  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz používá konstruktor pojmenovaného typu k vytvoření instance typu koncepčního modelu. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#NAMED_TYPE_CONSTRUCTOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#named_type_constructor)]  
  
## <a name="see-also"></a>Viz také:

- [Vytváření typů](constructing-types-entity-sql.md)
- [Reference k Entity SQL](entity-sql-reference.md)
