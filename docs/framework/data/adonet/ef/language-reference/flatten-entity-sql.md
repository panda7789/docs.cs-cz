---
title: Sloučit (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 1a670c63-0a29-4738-80e6-101f66af05c3
ms.openlocfilehash: 4f9a6315fc9cc2f295c21cc5fb7e1007e47796b9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59304569"
---
# <a name="flatten-entity-sql"></a>Sloučit (Entity SQL)
Převede kolekci kolekcí plochá kolekce. Nová kolekce obsahuje stejné prvky jako původní kolekce, ale bez vnořené struktury.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
FLATTEN ( collection )  
```  
  
## <a name="arguments"></a>Arguments  
 `collection`  
 Libovolný platný výraz, který vrátí kolekci hodnota kolekce k shrnout do jedné kolekce.  
  
## <a name="remarks"></a>Poznámky  
 `FLATTEN` je jedním z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] množinové operátory. Všechny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sadu operátorů jsou vyhodnocovány zleva doprava. Zobrazit [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) prioritu informace pro [!INCLUDE[esql](../../../../../../includes/esql-md.md)] množinové operátory.  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL používá `FLATTEN` operátor převést kolekci plochá kolekce kolekcí. Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:  
  
1. Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#FLATTEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#flatten)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
