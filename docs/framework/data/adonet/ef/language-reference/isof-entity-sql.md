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
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Libovolný platný výraz dotazu pro určení typu.  
  
 NOT  
 Negace datového modelu EDM. Logický výsledek pro je.  
  
 POUZE  
 Určuje, že funkce vrátí hodnotu `true` pouze v případě, že `expression` je typu `type`, nikoli některého z jeho podtypů.  
  
 `type`  
 Typ, pro který se má `expression` testovat Typ musí být kvalifikovaný v oboru názvů.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`, je-li `expression` typu T a T buď základní typ, nebo odvozený typ `type`; null, pokud `expression` má hodnotu null za běhu; v opačném případě `false`.  
  
## <a name="remarks"></a>Poznámky  
 Výrazy `expression IS NOT OF (type)` a `expression IS NOT OF (ONLY type)` jsou syntakticky ekvivalentní `NOT (expression IS OF (type))` a `NOT (expression IS OF (ONLY type))`, v uvedeném pořadí.  
  
 Následující tabulka ukazuje chování operátoru `IS OF` v některých typických a rohových vzorcích. Všechny výjimky jsou vyvolány na straně klienta před vyvoláním zprostředkovatele:  
  
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
 Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz používá operátor IS OF k určení typu výrazu dotazu a poté používá operátor "považovat" k převodu objektu typu kurz na kolekci objektů typu OnsiteCourse. Dotaz je založen na [školním modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).  
  
 [! Code-SQL [DP EntityServices koncepty # TREAT_ISOF] ~/Samples/Snippets/TSQL/VS_Snippets_Data/DP EntityServices koncepty/TSQL/EntitySql. SQL # treat_isof)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
