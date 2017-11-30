---
title: "GetType – operátor (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 38a984dce44133936f7f163e6afb20f0f336377c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
