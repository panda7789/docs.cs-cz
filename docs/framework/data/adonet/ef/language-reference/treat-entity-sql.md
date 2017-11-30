---
title: "ZPRACOVÁVAT (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b77f156-55de-4cb4-8154-87f707d4c635
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fa7bfd2a9fffdd0cfedced76cf83f9e01630c986
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="treat-entity-sql"></a>ZPRACOVÁVAT (entita SQL)
Objekt konkrétní základní typ zpracovává jako objekt zadaného typu odvozené.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
TREAT ( expression as type)  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný dotaz výraz, který vrátí entity.  
  
> [!NOTE]
>  Typ zadaný výraz musí být podtypem zadaný datový typ nebo datový typ musí být podtypem typ výrazu.  
  
 `type`  
 Typ entity. Typ musí být kvalifikován obor názvů.  
  
> [!NOTE]
>  Zadaný výraz musí být podtypem zadaný datový typ nebo datový typ musí být podtypem výraz.  
  
## <a name="return-value"></a>Návratová hodnota  
 Hodnota zadaného datového typu.  
  
## <a name="remarks"></a>Poznámky  
 ZPRACOVÁVAT slouží k provádění přetypování nahoru mezi související třídy. Například pokud `Employee` je odvozena z `Person` a p je typu `Person`, `TREAT(p AS NamespaceName.Employee)` upcasts a obecného `Person` instance na `Employee`; to znamená, umožňuje považovat za p `Employee`.  
  
 ZPRACOVÁVAT se používá ve scénářích dědičnosti, kde můžete provést dotaz takto:  
  
```  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)   
```  
  
 Tento dotaz upcasts `Person` entity k `Employee` typu. Pokud hodnota p není ve skutečnosti je typu `Employee`, výsledkem je hodnota, výraz `null`.  
  
> [!NOTE]
>  Zadaný výraz `Employee` musí být podtypem zadaný datový typ `Person`, nebo datový typ musí být podtypem výraz. Výraz, jinak bude výsledkem chyba kompilace.  
  
 Následující tabulka uvádí chování zpracovávat přes některé typické vzory a některé méně častých vzory. Všechny výjimky jsou vyvolány ze strany klienta předtím, než získá volá zprostředkovatele:  
  
|Vzor|Chování|  
|-------------|--------------|  
|`TREAT (null AS EntityType)`|Vrátí `DbNull`.|  
|`TREAT (null AS ComplexType)`|Vyvolá výjimku.|  
|`TREAT (null AS RowType)`|Vyvolá výjimku, nebo|  
|`TREAT (EntityType AS EntityType)`|Vrátí `EntityType` nebo `null`.|  
|`TREAT (ComplexType AS ComplexType)`|Vyvolá výjimku.|  
|`TREAT (RowType AS RowType)`|Vyvolá výjimku.|  
  
## <a name="example"></a>Příklad  
 Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz používá operátor ZPRACOVÁVAT převést objekt typu kurzu na kolekce objektů typu OnsiteCourse. Dotaz je na základě [školní modelu](http://msdn.microsoft.com/en-us/859a9587-81ea-4a45-9bc0-f8d330e1adac).  
  
 [!code-csharp[DP EntityServices Concepts 2#TREAT_ISOF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#treat_isof)]  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na entitu SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Strukturované typy s možnou hodnotou Null](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
