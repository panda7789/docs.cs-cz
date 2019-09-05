---
title: REF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c5f4cb35-69e9-44cc-b63b-ee38922bbda1
ms.openlocfilehash: 9d35306d1299e91ecaa55a7d2818ee1e2982793f
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249201"
---
# <a name="ref-entity-sql"></a>REF (Entity SQL)
Vrátí odkaz na instanci entity.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
REF( expression )   
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz, který je výsledkem instance typu entity.  
  
## <a name="return-value"></a>Návratová hodnota  
 Odkaz na zadanou instanci entity  
  
## <a name="remarks"></a>Poznámky  
 Odkaz na entitu se skládá z klíče entity a názvu sady entit. Vzhledem k tomu, že různé sady entit můžou být založené na stejném typu entity, může se konkrétní klíč entity objevit v několika sadách entit. Odkaz na entitu je ale vždycky jedinečný. Pokud vstupní výraz představuje trvalou entitu, bude vrácena odkaz na tuto entitu. Pokud vstupní výraz není trvalá entita, vrátí se odkaz s hodnotou null.  
  
 Pokud se k přístupu k vlastnosti entity používá operátor extrakce vlastností (.), odkaz se automaticky odkázat.  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz pomocí operátoru REF vrátí odkaz na vstupní entitu argumentu. Stejný dotaz odkazuje na odkaz, protože používáme operaci extrakce vlastnosti (.) pro přístup k vlastnosti entity produktu. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-primitivetype-results.md)PrimitiveType.  
  
2. Předat následující dotaz jako argument `ExecutePrimitiveTypeQuery` metodě:  
  
 [!code-csharp[DP EntityServices Concepts 2#REF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref)]  
  
## <a name="see-also"></a>Viz také:

- [DEREF](deref-entity-sql.md)
- [CREATEREF](createref-entity-sql.md)
- [KEY](key-entity-sql.md)
- [Reference k Entity SQL](entity-sql-reference.md)
- [Definice typů](type-definitions-entity-sql.md)
