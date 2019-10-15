---
title: ZPRACOVÁVÁ se (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b77f156-55de-4cb4-8154-87f707d4c635
ms.openlocfilehash: 38099fa83ed78b40d46faeb5e617157f7aa7c1a1
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319266"
---
# <a name="treat-entity-sql"></a>ZPRACOVÁVÁ se (Entity SQL)
Zpracovává objekt určitého základního typu jako objekt zadaného odvozeného typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
TREAT ( expression as type)  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz dotazu, který vrací entitu.  
  
> [!NOTE]
> Typ zadaného výrazu musí být podtyp zadaného datového typu nebo musí být datový typ podtypem typu výrazu.  
  
 `type`  
 Typ entity. Typ musí být kvalifikován oborem názvů.  
  
> [!NOTE]
> Zadaný výraz musí být podtypem zadaného datového typu nebo musí být datový typ podtypem výrazu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Hodnota zadaného datového typu.  
  
## <a name="remarks"></a>Poznámky  
 K provádění přetypování mezi souvisejícími třídami se používá zpracování. Například pokud `Employee` je odvozeno z `Person` a p je typu `Person`, `TREAT(p AS NamespaceName.Employee)` přetypování obecné instance `Person` na `Employee`; To znamená, že vám umožní považovat p za `Employee`.  
  
 Použití se používá ve scénářích dědičnosti, kde můžete provádět dotaz podobný následujícímu:  
  
```sql  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)   
```  
  
 Tento dotaz přetypování entit `Person` na typ `Employee`. Pokud hodnota p není ve skutečnosti typu `Employee`, výraz vrací hodnotu `null`.  
  
> [!NOTE]
> Zadaný výraz `Employee` musí být podtypem zadaného datového typu `Person` nebo datový typ musí být podtypem výrazu. V opačném případě výraz způsobí chybu při kompilaci.  
  
 V následující tabulce je uvedeno chování při zpracování několika typických vzorů a některých méně běžných vzorů. Všechny výjimky jsou vyvolány na straně klienta před vyvoláním zprostředkovatele:  
  
|Vzor|Předvídatelně|  
|-------------|--------------|  
|`TREAT (null AS EntityType)`|Vrátí `DbNull`.|  
|`TREAT (null AS ComplexType)`|Vyvolá výjimku.|  
|`TREAT (null AS RowType)`|Vyvolá výjimku/|  
|`TREAT (EntityType AS EntityType)`|Vrátí `EntityType` nebo `null`.|  
|`TREAT (ComplexType AS ComplexType)`|Vyvolá výjimku.|  
|`TREAT (RowType AS RowType)`|Vyvolá výjimku.|  
  
## <a name="example"></a>Příklad  
 Následující dotaz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] používá operátor považovat pro převod objektu typu kurzu na kolekci objektů typu OnsiteCourse. Dotaz je založen na [školním modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).  
  
 [!code-sql[DP EntityServices Concepts#TREAT_ISOF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#treat_isof)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
- [Strukturované typy s možnou hodnotou Null](nullable-structured-types-entity-sql.md)
