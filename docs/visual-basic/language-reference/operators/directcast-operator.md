---
title: "DirectCast – operátor (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.directCast
- directCast
helpviewer_keywords: DirectCast keyword [Visual Basic]
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d9b81abea364e328b831ee98c3b847161c3f7dd3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="directcast-operator-visual-basic"></a>DirectCast – operátor (Visual Basic)
Představuje operaci převodu typ na základě dědičnosti nebo implementace.  
  
## <a name="remarks"></a>Poznámky  
 `DirectCast`nepoužívá Visual Basicu běhu pomocné rutiny pro převod, můžou poskytovat, poněkud lepší výkon než `CType` při převodu z datového typu `Object`.  
  
 Můžete použít `DirectCast` – klíčové slovo podobným způsobem můžete použít [CType – funkce](../../../visual-basic/language-reference/functions/ctype-function.md) a [TryCast – operátor](../../../visual-basic/language-reference/operators/trycast-operator.md) – klíčové slovo. Můžete zadat jako první argument a zadejte ji do převést jako druhý argument výrazu. `DirectCast`vyžaduje relaci dědičnosti nebo implementace mezi typy dat dva argumenty. To znamená, že jeden typ musí dědit z nebo implementovat dalších.  
  
## <a name="errors-and-failures"></a>Chyby a selhání  
 `DirectCast`Chyba kompilátoru generuje, pokud zjistí, že neexistuje žádný vztah dědičnosti nebo implementace. Ale nedostatek Chyba kompilátoru nezaručuje úspěšné převod. Pokud je zužující převod požadované, pravděpodobně nezdaří za běhu. Pokud k tomu dojde, modul runtime vyvolá <xref:System.InvalidCastException> chyby.  
  
## <a name="conversion-keywords"></a>Klíčová slova převodu  
 Porovnání klíčová slova převodu typu je následující.  
  
|– Klíčové slovo|Typy dat|Argument relace|Běhové chyby|  
|---|---|---|---|  
|[CType – funkce](../../../visual-basic/language-reference/functions/ctype-function.md)|Žádné datové typy|Je nutné definovat rozšiřující nebo zužující převod mezi dvěma datovými typy|Vyvolá<xref:System.InvalidCastException>|  
|`DirectCast`|Žádné datové typy|Jeden typ musí dědit z nebo provádět další typ.|Vyvolá<xref:System.InvalidCastException>|  
|[TryCast – operátor](../../../visual-basic/language-reference/operators/trycast-operator.md)|Odkazové typy pouze|Jeden typ musí dědit z nebo provádět další typ.|Vrátí [nic](../../../visual-basic/language-reference/nothing.md)|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje dva použití `DirectCast`, jeden, který selže na dobu spuštění a jeden neuspěje.  
  
 [!code-vb[VbVbalrKeywords#1](../../../visual-basic/language-reference/codesnippet/VisualBasic/directcast-operator_1.vb)]  
  
 V předchozím příkladu běhu typ `q` je `Double`. `CType`úspěšné, protože `Double` lze převést na `Integer`. Však první `DirectCast` nezdaří za běhu, protože běhu typ `Double` nemá žádný vztah dědičnosti s `Integer`, i když existuje převod. Druhý `DirectCast` úspěšné, protože převede z typu <xref:System.Windows.Forms.Form> na typ <xref:System.Windows.Forms.Control>, ze kterého <xref:System.Windows.Forms.Form> dědí.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Convert.ChangeType%2A?displayProperty=nameWithType>  
 [Rozšíření a zúžení převodů](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Implicitní a explicitní převody](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
