---
title: checked (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- checked_CSharpKeyword
- checked
helpviewer_keywords:
- checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
caps.latest.revision: 24
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0ae77894cdc94e41dfa281b92ed3304e0dc25731
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Zaškrtnuto a nezaškrtnuto](../../../csharp/language-reference/keywords/checked-and-unchecked.md)  
 [nezaškrtnuto](../../../csharp/language-reference/keywords/unchecked.md)
