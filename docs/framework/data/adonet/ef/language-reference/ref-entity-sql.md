---
title: REF (entita SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c5f4cb35-69e9-44cc-b63b-ee38922bbda1
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 1836b91876ac3c993f07902a644c130dda76f158
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ref-entity-sql"></a>REF (entita SQL)
Vrátí odkaz na instanci entity.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
REF( expression )   
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Jakýkoli platný výraz, který poskytne instanci typu entity.  
  
## <a name="return-value"></a>Návratová hodnota  
 Odkaz na instanci zadané entity.  
  
## <a name="remarks"></a>Poznámky  
 Odkaz na entitu se skládá z klíče entity a nastavte název entity. Protože sad různých entit může být založen na stejný typ entity, se může zobrazit klíč konkrétní entity ve víc sadách entit. Odkaz na entitu je však vždy jedinečný. Pokud vstupní výraz představuje trvalou entity, se vrátí odkaz na tuto entitu. Pokud vstupní výraz není trvalý entity, bude vrácen odkaz s hodnotou null.  
  
 Pokud je vlastnost extrakce – operátor (.) se používá pro přístup k vlastnosti entity, je automaticky dereferenced odkaz.  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL pomocí operátoru REF vrací odkaz pro argument vstupní entity. Stejný dotaz dereferences odkaz, protože jsme se o přístup k vlastnosti entity produktu pomocí operace extrakce vlastnost (.). Dotaz je založen na modelu prodej AdventureWorks. Pro zkompilování a spuštění tohoto dotazu, postupujte takto:  
  
1.  Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecutePrimitiveTypeQuery` metoda:  
  
 [!code-csharp[DP EntityServices Concepts 2#REF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref)]  
  
## <a name="see-also"></a>Viz také  
 [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)  
 [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
 [KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Definice typů](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)
