---
title: REF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c5f4cb35-69e9-44cc-b63b-ee38922bbda1
ms.openlocfilehash: c3bb22badcfadb92c8687a4eff3a5c7aad1ff1ee
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59090293"
---
# <a name="ref-entity-sql"></a>REF (Entity SQL)
Vrátí odkaz na instanci entity.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
REF( expression )   
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz, který vrací instanci typu entity.  
  
## <a name="return-value"></a>Návratová hodnota  
 Odkaz na zadané zapisovanou instanci entity.  
  
## <a name="remarks"></a>Poznámky  
 Odkaz na entitu se skládá z klíče entity a nastavte název entity. Protože sady různých entit může být založen na stejný typ entity, klíč konkrétní entity mohou objevit v několika sady entit. Odkaz na entitu je však vždy jedinečná. Pokud vstupní výraz představuje trvalou entitu, vrátí se odkaz na tuto entitu. Pokud vstupní výraz není trvalý entity, vrátí se odkaz s hodnotou null.  
  
 Pokud vlastnost extrakce – operátor (.) se používá pro přístup k vlastnosti entity, odkaz je automaticky přes ukazatel.  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL používá operátor REF vrací odkaz pro entity vstupní argument. Stejný dotaz přístupů přes ukazatel, odkaz vzhledem k tomu, že používáme operaci extrakce vlastnosti (.) pro přístup k vlastnosti entitou produkt. Dotaz je založen na modelu Sales AdventureWorks. Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:  
  
1.  Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecutePrimitiveTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#REF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref)]  
  
## <a name="see-also"></a>Viz také:

- [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)
- [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)
- [KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)
- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Definice typů](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)
