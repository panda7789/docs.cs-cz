---
title: GetType – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 581f576222eb149aede841a5da7a0e5f38c77b58
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="gettype-operator-visual-basic"></a>GetType – operátor (Visual Basic)
Vrátí <xref:System.Type> objekt pro zadaný typ. <xref:System.Type> Objekt poskytuje informace o typu, například jeho vlastnosti, metod a události.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
GetType(typename)  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---|---|  
|`typename`|Název typu, pro které očekáváte informace.|  
  
## <a name="remarks"></a>Poznámky  
 `GetType` Vrátí operátor <xref:System.Type> objekt pro zadaný `typename`. Můžete předat název typu žádné definované v `typename`. To zahrnuje následující:  
  
-   Zadejte všechna data jazyka Visual Basic, například `Boolean` nebo `Date`.  
  
-   Všechny třídy rozhraní .NET Framework, struktury, modul nebo rozhraní, jako například <xref:System.ArgumentException?displayProperty=nameWithType> nebo <xref:System.Double?displayProperty=nameWithType>.  
  
-   Všechny třídy, struktury, modul nebo rozhraní definovaný vaší aplikací.  
  
-   Žádné pole definovaný vaší aplikací.  
  
-   Všechny delegát definovaný vaší aplikací.  
  
-   Všechny výčtu definované jazyka Visual Basic, rozhraní .NET Framework nebo aplikace.  
  
 Pokud chcete získat objekt typu objektové proměnné, použijte <xref:System.Type.GetType%2A?displayProperty=nameWithType> metoda.  
  
 `GetType` Operátor může být užitečné v následujících případech:  
  
-   Metadata pro typ potřebuje přístup za běhu. <xref:System.Type> Objekt poskytuje metadata například členy typu a informace o nasazení. Potřebujete, například tak, aby odrážela přes sestavení. Další informace naleznete v tématu <xref:System.Reflection?displayProperty=nameWithType>.  
  
-   Chcete porovnat dva odkazy na objekty zobrazíte Pokud odkazují instance stejného typu. Pokud tomu tak je, `GetType` vrátí odkazy na stejné <xref:System.Type> objektu.  
  
## <a name="example"></a>Příklad  
 Následující příklady zobrazují `GetType` operátor používá.  
  
 [!code-vb[VbVbalrOperators#26](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/gettype-operator_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Operátory a výrazy](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
