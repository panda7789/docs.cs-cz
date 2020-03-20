---
title: TREAT (Entita SQL)
ms.date: 03/30/2017
ms.assetid: 5b77f156-55de-4cb4-8154-87f707d4c635
ms.openlocfilehash: 06c4200434f443446e8981dcefe2baf43b1af4b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149892"
---
# <a name="treat-entity-sql"></a>TREAT (Entita SQL)
Zachází s objektem určitého základního typu jako s objektem zadaného odvozeného typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
TREAT ( expression as type)  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Libovolný platný výraz dotazu, který vrací entitu.  
  
> [!NOTE]
> Typ zadaného výrazu musí být podtypem zadaného datového typu nebo datový typ musí být podtypem typu výrazu.  
  
 `type`  
 Typ entity. Typ musí být kvalifikován oborem názvů.  
  
> [!NOTE]
> Zadaný výraz musí být podtypem zadaného datového typu nebo datový typ musí být podtypem výrazu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Hodnota zadaného datového typu.  
  
## <a name="remarks"></a>Poznámky  
 TREAT se používá k provádění upcasting mezi související třídy. Například pokud `Employee` je `Person` odvozen od a `Person` `TREAT(p AS NamespaceName.Employee)` p je typu `Person` , `Employee`upcasts obecná instance ; to znamená, že vám umožní `Employee`zacházet s p jako .  
  
 TREAT se používá ve scénářích dědičnosti, kde můžete provést dotaz, jako je následující:  
  
```sql  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)
```  
  
 Tento dotaz upcasts `Person` entity `Employee` typu. Pokud hodnota p není ve `Employee`skutečnosti typu , výraz `null`dává hodnotu .  
  
> [!NOTE]
> Zadaný `Employee` výraz musí být podtypem `Person`zadaného datového typu nebo datový typ musí být podtypem výrazu. V opačném případě výraz bude mít za následek chybu v době kompilace.  
  
 V následující tabulce je uvedeno chování treat přes některé typické vzory a některé méně běžné vzory. Všechny výjimky jsou vyvolány ze strany klienta před zprostředkovatel získá vyvolána:  
  
|Vzor|Chování|  
|-------------|--------------|  
|`TREAT (null AS EntityType)`|Vrací objekt `DbNull`.|  
|`TREAT (null AS ComplexType)`|Vyvolá výjimku.|  
|`TREAT (null AS RowType)`|Vyvolá výjimku/|  
|`TREAT (EntityType AS EntityType)`|Vrátí `EntityType` `null`nebo .|  
|`TREAT (ComplexType AS ComplexType)`|Vyvolá výjimku.|  
|`TREAT (RowType AS RowType)`|Vyvolá výjimku.|  
  
## <a name="example"></a>Příklad  
 Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz používá treat operátor převést objekt typu Course na kolekci objektů typu OnsiteCourse. Dotaz je založen na [školním modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).  
  
 [!code-sql[DP EntityServices Concepts#TREAT_ISOF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#treat_isof)]  
  
## <a name="see-also"></a>Viz také

- [Reference k Entity SQL](entity-sql-reference.md)
- [Strukturované typy s možnou hodnotou Null](nullable-structured-types-entity-sql.md)
