---
title: ISOF (entita SQL)
ms.date: 03/30/2017
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
ms.openlocfilehash: 7aecb8e2740ffd711278bfd5735c71c2dacf9c3c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="isof-entity-sql"></a>ISOF (entita SQL)
Určuje, zda typ výrazu je zadaného typu nebo jeden z jeho podtypech.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression IS [ NOT ] OF ( [ ONLY ] type )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Jakýkoli platný dotaz výraz k určení typu.  
  
 NENÍ  
 Neguje EDM. Logická hodnota výsledek je z.  
  
 POUZE  
 Určuje, zda je z vrátí `true` pouze v případě `expression` je typu `type` a nikoli jakákoliv jednoho jeho podtypech.  
  
 `type`  
 Typ k otestování `expression` proti. Typ musí být kvalifikovaný obor názvů.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true` Pokud `expression` je typu T a T je základní typ nebo odvozené typ `type`; hodnota null, pokud `expression` je null za běhu, jinak hodnota `false`.  
  
## <a name="remarks"></a>Poznámky  
 Výrazy `expression IS NOT OF (type)` a `expression IS NOT OF (ONLY type)` odpovídají syntakticky `NOT (expression IS OF (type))` a `NOT (expression IS OF (ONLY type))`, v uvedeném pořadí.  
  
 Následující tabulka uvádí chování `IS OF` operátor přes některé typické a rohu vzory. Všechny výjimky jsou vyvolány ze strany klienta předtím, než získá volá zprostředkovatele:  
  
|Vzor|Chování|  
|-------------|--------------|  
|Null není pro (EntityType)|Vyvolá|  
|NULL je z (ComplexType)|Vyvolá|  
|NULL je z (RowType)|Vyvolá|  
|ZPRACOVÁVAT (null AS EntityType) je pro (EntityType)|Vrátí DBNull|  
|ZPRACOVÁVAT (null AS ComplexType) je z (ComplexType)|Vyvolá|  
|ZPRACOVÁVAT (null AS RowType) je z (RowType)|Vyvolá|  
|JE typ entity (typu ENTITYTYPE)|Vrátí hodnotu true nebo false|  
|JE ComplexType (COMPLEXTYPE)|Vyvolá|  
|JE RowType z (RowType)|Vyvolá|  
  
## <a name="example"></a>Příklad  
 Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz používá operátor je z určit typ výrazu dotazu a pak operátor ZPRACOVÁVAT převést objekt typu kurzu na kolekce objektů typu OnsiteCourse. Dotaz je na základě [školní modelu](http://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac).  
  
 [!code-csharp[DP EntityServices Concepts 2#TREAT_ISOF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#treat_isof)]  
  
## <a name="see-also"></a>Viz také  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
