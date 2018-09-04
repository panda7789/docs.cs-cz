---
title: POVAŽOVAT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b77f156-55de-4cb4-8154-87f707d4c635
ms.openlocfilehash: c3291dc6d5bc79430c8bf011ee6a2f4dc213ffad
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43510404"
---
# <a name="treat-entity-sql"></a>POVAŽOVAT (Entity SQL)
Zpracovává konkrétní základního typu objektu jako objekt zadaného typu odvozené.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
TREAT ( expression as type)  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný dotaz výraz, který vrátí entity.  
  
> [!NOTE]
>  Typ zadaného výrazu musí být podtypem typu zadaného datového typu nebo datový typ musí být podtypem typu výrazu.  
  
 `type`  
 Typ entity. Typ musí být kvalifikován oborem názvů.  
  
> [!NOTE]
>  Zadaný výraz musí být podtypem typu zadaného datového typu nebo datový typ musí být podtypem typu výrazu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Hodnota zadaného datového typu.  
  
## <a name="remarks"></a>Poznámky  
 NAKLÁDÁNÍ se používá k provedení upcasting mezi souvisejícími třídami. Například pokud `Employee` je odvozena z `Person` a p je typu `Person`, `TREAT(p AS NamespaceName.Employee)` upcasts a Obecné `Person` instance na `Employee`; to znamená, je možné považovat za p `Employee`.  
  
 NAKLÁDÁNÍ se používá ve scénářích dědičnosti, kde lze dotaz podobný tomuto:  
  
```  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)   
```  
  
 Tento dotaz upcasts `Person` entity, které `Employee` typu. Pokud hodnota p není ve skutečnosti je typu `Employee`, výraz vrací hodnotu `null`.  
  
> [!NOTE]
>  Zadaný výraz `Employee` musí být podtypem typu zadaného datového typu `Person`, nebo datový typ musí být podtypem typu výrazu. V opačném případě výraz způsobí chybu kompilace.  
  
 Následující tabulka uvádí chování považovat za některé typické vzory a některé méně běžné vzory. Všechny výjimky jsou vyvolány ze strany klienta předtím, než je volán za zprostředkovatele:  
  
|Vzor|Chování|  
|-------------|--------------|  
|`TREAT (null AS EntityType)`|Vrátí `DbNull`.|  
|`TREAT (null AS ComplexType)`|Vyvolá výjimku.|  
|`TREAT (null AS RowType)`|Vyvolá výjimku /|  
|`TREAT (EntityType AS EntityType)`|Vrátí `EntityType` nebo `null`.|  
|`TREAT (ComplexType AS ComplexType)`|Vyvolá výjimku.|  
|`TREAT (RowType AS RowType)`|Vyvolá výjimku.|  
  
## <a name="example"></a>Příklad  
 Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazu používá operátor POVAŽOVAT převést objekt typu kurzu ke kolekci objektů typu OnsiteCourse. Dotaz je založen na [školní modelu](https://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac).  
  
 [!code-csharp[DP EntityServices Concepts 2#TREAT_ISOF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#treat_isof)]  
  
## <a name="see-also"></a>Viz také  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Strukturované typy s možnou hodnotou Null](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
