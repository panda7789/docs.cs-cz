---
title: ISOF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
ms.openlocfilehash: 72443060584eaca5aa8c1ea19393dfc043722c90
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54731540"
---
# <a name="isof-entity-sql"></a>ISOF (Entity SQL)
Určuje, zda je typ výrazu zadaný typ nebo některý z jeho podtypy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression IS [ NOT ] OF ( [ ONLY ] type )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný výraz platného dotazu k určení typu.  
  
 NOT  
 Neguje modelu EDM. Výsledek logickou hodnotu je z.  
  
 POUZE  
 Určuje, že se vrátí `true` pouze tehdy, pokud `expression` je typu `type` a nikoli jakákoliv některou jeho podtypy.  
  
 `type`  
 Typ, který chcete testovat `expression` proti. Typ musí být kvalifikovaný v oboru názvů.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true` Pokud `expression` je typu T a T je základní typ nebo odvozeným typem `type`; hodnota null, pokud `expression` je za běhu hodnotu null; v opačném případě `false`.  
  
## <a name="remarks"></a>Poznámky  
 Výrazy `expression IS NOT OF (type)` a `expression IS NOT OF (ONLY type)` syntakticky odpovídajících `NOT (expression IS OF (type))` a `NOT (expression IS OF (ONLY type))`v uvedeném pořadí.  
  
 V následující tabulce jsou uvedeny chování `IS OF` operátor přes některé typické - rohové a vzory. Všechny výjimky jsou vyvolány ze strany klienta předtím, než je volán za zprostředkovatele:  
  
|Vzor|Chování|  
|-------------|--------------|  
|NULL je typu (EntityType)|Vyvolá výjimku|  
|NULL je typu (ComplexType)|Vyvolá výjimku|  
|NULL je z (RowType)|Vyvolá výjimku|  
|POVAŽOVAT (třída EntityType hodnotu null jako) je typu (EntityType)|Vrátí DBNull|  
|POVAŽOVAT (null jako ComplexType) je typu (ComplexType)|Vyvolá výjimku|  
|POVAŽOVAT (null jako RowType) je z (RowType)|Vyvolá výjimku|  
|JE typ entity typu (EntityType)|Vrátí hodnotu true nebo false|  
|Typ ComplexType je typu (ComplexType)|Vyvolá výjimku|  
|JE RowType z (RowType)|Vyvolá výjimku|  
  
## <a name="example"></a>Příklad  
 Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazu používá operátor je určit typ výrazu dotazu a pak používá operátor POVAŽOVAT převést objekt typu kurzu ke kolekci objektů typu OnsiteCourse. Dotaz je založen na [školní modelu](https://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac).  
  
 [!code-csharp[DP EntityServices Concepts 2#TREAT_ISOF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#treat_isof)]  
  
## <a name="see-also"></a>Viz také:
- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
