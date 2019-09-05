---
title: ISOF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
ms.openlocfilehash: 3b746a82f72fc7f42f9d91ddd0a7d6f4f86ac0bb
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250579"
---
# <a name="isof-entity-sql"></a>ISOF (Entity SQL)
Určuje, zda je typ výrazu zadaného typu nebo některého z jeho podtypů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression IS [ NOT ] OF ( [ ONLY ] type )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz dotazu pro určení typu.  
  
 NOT  
 Negace datového modelu EDM. Logický výsledek pro je.  
  
 POUZE  
 Určuje, že se vrátí `true` pouze v `expression` případě, že `type` je typu, a ne některého z jeho podtypů.  
  
 `type`  
 Typ, pro který `expression` se má testovat. Typ musí být kvalifikovaný v oboru názvů.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`Pokud `expression` je typu t a T je buď základní typ, nebo odvozený `type`typ; null, pokud `expression` má hodnotu null za běhu, jinak `false`.  
  
## <a name="remarks"></a>Poznámky  
 Výrazy `expression IS NOT OF (type)` a `expression IS NOT OF (ONLY type)` `NOT (expression IS OF (ONLY type))`jsousyntaktickyekvivalentní a v uvedeném pořadí. `NOT (expression IS OF (type))`  
  
 Následující tabulka ukazuje chování `IS OF` operátora v některých typických a rohových vzorcích. Všechny výjimky jsou vyvolány na straně klienta před vyvoláním zprostředkovatele:  
  
|Vzor|Chování|  
|-------------|--------------|  
|hodnota null je typu (EntityType).|Vyvolá|  
|hodnota null je (ComplexType).|Vyvolá|  
|hodnota null je (RowType).|Vyvolá|  
|ZPRACOVÁVÁ se (hodnota null jako EntityType) je typu (EntityType).|Vrátí hodnotu DBNull.|  
|ZPRACOVÁVÁ se (hodnota null jako ComplexType) je (ComplexType).|Vyvolá|  
|ZPRACOVÁVÁ se (hodnota null jako RowType) je (RowType).|Vyvolá|  
|EntityType je typu (EntityType).|Vrátí hodnotu true nebo false.|  
|ComplexType je typu (ComplexType).|Vyvolá|  
|RowType je (RowType)|Vyvolá|  
  
## <a name="example"></a>Příklad  
 Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz používá operátor is of k určení typu výrazu dotazu a poté pomocí operátoru "považovat" převést objekt typu kurz na kolekci objektů typu OnsiteCourse. Dotaz je založen na [školním modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).  
  
 [!code-csharp[DP EntityServices Concepts 2#TREAT_ISOF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#treat_isof)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
