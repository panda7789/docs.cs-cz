---
title: Porovnání hodnot
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], comparing values
- Visual Basic code, operators
- Visual Basic code, expressions
- comparison operators [Visual Basic], comparing expressions
- numeric expressions
- operators [Visual Basic], comparison
- expressions [Visual Basic], comparing
ms.assetid: 60da0c76-9458-4afc-97e9-44a7939c064c
ms.openlocfilehash: 01816b5730cf4fda61f1737ce3ce00ab82f57da8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403392"
---
# <a name="value-comparisons-visual-basic"></a>Porovnání hodnot (Visual Basic)
Operátory porovnání lze použít k vytvoření výrazů, které porovnávají hodnoty číselných proměnných. Tyto výrazy vrátí `Boolean` hodnotu na základě toho, zda je porovnání true nebo false. Příklady takového výrazu jsou následující.  
  
 `45 > 26`  
  
 `26 > 45`  
  
 První výraz se vyhodnotí jako `True` , protože 45 je větší než 26. Druhý příklad je vyhodnocen jako `False` , protože 26 není větší než 45.  
  
 Tímto způsobem můžete také porovnat číselné výrazy. Výrazy, které porovnáváte, mohou být složité výrazy, jako v následujícím příkladu.  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 Předchozí složitý výraz zahrnuje literály, proměnné a volání funkcí. Výrazy na obou stranách operátoru porovnání jsou vyhodnoceny a výsledné hodnoty jsou pak porovnány pomocí `>=` operátoru porovnání. Pokud je hodnota výrazu na levé straně větší než nebo rovna hodnotě výrazu na pravé straně, celý výraz se vyhodnotí jako `True` . v opačném případě se vyhodnotí jako `False` .  
  
 Výrazy, které porovnávají hodnoty, jsou nejčastěji používány v `If...Then` konstrukcích, jako v následujícím příkladu.  
  
 [!code-vb[VbVbalrOperators#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#84)]  
  
 `=`Znaménkem je operátor porovnání a operátor přiřazení. Při použití jako operátor porovnání vyhodnotí, zda je hodnota vlevo rovna hodnotě na pravé straně, jak je znázorněno v následujícím příkladu.  
  
 [!code-vb[VbVbalrOperators#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#85)]  
  
 Můžete také použít výraz porovnání kdekoli `Boolean` , kde je požadována hodnota, například v `If` `While` příkazu,, `Loop` nebo `ElseIf` , nebo při přiřazení hodnoty k proměnné nebo jejímu předání `Boolean` . V následujícím příkladu je hodnota vrácená výrazem porovnání přiřazena k `Boolean` proměnné.  
  
 [!code-vb[VbVbalrOperators#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#86)]  
  
## <a name="see-also"></a>Viz také

- [Logické výrazy](boolean-expressions.md)
- [Operátory a výrazy](index.md)
- [Operátory porovnání v jazyce Visual Basic](comparison-operators.md)
- [Postupy: Výpočet numerických hodnot](how-to-calculate-numeric-values.md)
- [Priorita operátorů v jazyce Visual Basic](../../../language-reference/operators/operator-precedence.md)
