---
title: Konstruktor pojmenovaného typu (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 549dea04-d93d-4c87-a292-f81b1598dbfd
ms.openlocfilehash: c7027614e5667acedb02d871a09df1ac9d799405
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250008"
---
# <a name="named-type-constructor-entity-sql"></a>Konstruktor pojmenovaného typu (Entity SQL)
Slouží k vytváření instancí nominálních typů konceptuálního modelu, jako je například entita nebo komplexní typy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
 Výraz níže vytvoří instanci `Person` typu:  
  
 `Person("abc", 12)`  
  
 Výraz níže vytvoří instanci komplexního typu:  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 Výraz níže vytvoří instanci vnořeného komplexního typu:  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 Výraz níže vytvoří instanci entity s vnořeným komplexním typem:  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 Následující příklad ukazuje, jak inicializovat vlastnost komplexního typu na hodnotu null:`MyModel.ZipCode(‘98118’, null)`  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz používá konstruktor pojmenovaného typu k vytvoření instance typu koncepčního modelu. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.  
  
2. Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:  
  
 [!code-csharp[DP EntityServices Concepts 2#NAMED_TYPE_CONSTRUCTOR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#named_type_constructor)]  
  
## <a name="see-also"></a>Viz také:

- [Vytváření typů](constructing-types-entity-sql.md)
- [Reference k Entity SQL](entity-sql-reference.md)
