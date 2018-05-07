---
title: checked (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- checked_CSharpKeyword
- checked
helpviewer_keywords:
- checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
ms.openlocfilehash: b05af798217a4f312bcf134d531135713efa8c66
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="checked-c-reference"></a>checked (Referenční dokumentace jazyka C#)
`checked` – Klíčové slovo se používá k explicitně povolit přetečení kontrola aritmetické operace typu integrální převody.  
  
 Ve výchozím nastavení výraz, který obsahuje pouze konstantní hodnoty v případě, že výraz vytvoří hodnotu, která je mimo rozsah pro cílový typ způsobí chybu kompilátoru. Pokud výraz obsahuje jednu nebo více hodnot nekonstantní, kompilátor nezjistí přetečení. Vyhodnocení výrazu přiřazené `i2` v následujícím příkladu nezpůsobí chybě kompilátoru.  
  
 [!code-csharp[csrefKeywordsChecked#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_1.cs)]  
  
 Ve výchozím nastavení tyto není konstantní výrazy nejsou kontrola přetečení v době běhu buď a vyvolají není přetečení výjimky. Předchozí příklad zobrazí-2,147,483,639 jako součet dvě kladná celá čísla.  
  
 Kontrola přetečení se dá nastavit podle – možnosti kompilátoru, konfigurace prostředí nebo použití `checked` – klíčové slovo. Následující příklady ukazují, jak používat `checked` výraz nebo `checked` bloku ke zjištění přetečení předchozí součet vytvořené v době běhu. Oba příklady vyvolání k výjimce přetečení.  
  
 [!code-csharp[csrefKeywordsChecked#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_2.cs)]  
  
 [Nezaškrtnuté](../../../csharp/language-reference/keywords/unchecked.md) – klíčové slovo lze zabránit kontrola přetečení.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje způsob použití `checked` povolit přetečení kontrola za běhu.  
  
 [!code-csharp[csrefKeywordsChecked#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_3.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Zaškrtnuto a nezaškrtnuto](../../../csharp/language-reference/keywords/checked-and-unchecked.md)  
 [unchecked](../../../csharp/language-reference/keywords/unchecked.md)
