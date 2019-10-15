---
title: ISOF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
ms.openlocfilehash: c4c4cbf74cb17cf43e79c42ff42d1e68122fd534
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319721"
---
# <a name="isof-entity-sql"></a>ISOF (Entity SQL)
Určuje, zda je typ výrazu zadaného typu nebo některého z jeho podtypů.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
expression IS [ NOT ] OF ( [ ONLY ] type )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz dotazu pro určení typu.  
  
 MĚNÍ  
 Negace datového modelu EDM. Logický výsledek pro je.  
  
 POUZE  
 Určuje, že vrací hodnotu `true` pouze v případě, že `expression` je typu `type` a nikoli žádné z jeho podtypu.  
  
 `type`  
 Typ pro otestování @no__t 0 proti. Typ musí být kvalifikovaný v oboru názvů.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`, pokud `expression` je typu T a T je buď základní typ, nebo odvozený typ `type`; null, pokud `expression` má za běhu hodnotu null; v opačném případě `false`.  
  
## <a name="remarks"></a>Poznámky  
 Výrazy `expression IS NOT OF (type)` a `expression IS NOT OF (ONLY type)` jsou syntakticky ekvivalentní `NOT (expression IS OF (type))` a `NOT (expression IS OF (ONLY type))` v uvedeném pořadí.  
  
 Následující tabulka ukazuje chování operátoru `IS OF` v některých typických a rohových vzorcích. Všechny výjimky jsou vyvolány na straně klienta před vyvoláním zprostředkovatele:  
  
|Vzor|Předvídatelně|  
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
 Následující dotaz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] používá operátor IS OF k určení typu výrazu dotazu a poté pomocí operátoru "považovat" převést objekt typu kurzu na kolekci objektů typu OnsiteCourse. Dotaz je založen na [školním modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).  
  
 [! Code-SQL [DP EntityServices koncepty # TREAT_ISOF] ~/samples/snippets/tsql/VS_Snippets_Data/dp EntityServices koncepty/TSQL/EntitySql. SQL # TREAT_ISOF)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
