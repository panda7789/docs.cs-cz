---
title: checked – klíčové slovo (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- checked_CSharpKeyword
- checked
helpviewer_keywords:
- checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
ms.openlocfilehash: e6c28ee0c575bd6010a8aad76fc978062c5fc6a4
ms.sourcegitcommit: ed7b4b9b77d35e94a35a2634e8c874f46603fb2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36948407"
---
# <a name="checked-c-reference"></a>checked (Referenční dokumentace jazyka C#)

`checked` – Klíčové slovo se používá k explicitně povolit přetečení kontrola aritmetické operace typu integrální převody.

Ve výchozím nastavení výraz, který obsahuje pouze konstantní hodnoty v případě, že výraz vytvoří hodnotu, která je mimo rozsah pro cílový typ způsobí chybu kompilátoru. Pokud výraz obsahuje jednu nebo více hodnot nekonstantní, kompilátor nezjistí přetečení. Vyhodnocení výrazu přiřazené `i2` v následujícím příkladu nezpůsobí chybě kompilátoru.

[!code-csharp[csrefKeywordsChecked#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#3)]

Ve výchozím nastavení tyto není konstantní výrazy nejsou kontrola přetečení v době běhu buď a vyvolají není přetečení výjimky. Předchozí příklad zobrazí-2,147,483,639 jako součet dvě kladná celá čísla.

Kontrola přetečení se dá nastavit podle – možnosti kompilátoru, konfigurace prostředí nebo použití `checked` – klíčové slovo. Následující příklady ukazují, jak používat `checked` výraz nebo `checked` bloku ke zjištění přetečení předchozí součet vytvořené v době běhu. Oba příklady vyvolání k výjimce přetečení.

[!code-csharp[csrefKeywordsChecked#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#4)]

[Nezaškrtnuté](../../../csharp/language-reference/keywords/unchecked.md) – klíčové slovo lze zabránit kontrola přetečení.

## <a name="example"></a>Příklad

Tento příklad ukazuje způsob použití `checked` povolit přetečení kontrola za běhu.

[!code-csharp[csrefKeywordsChecked#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#1)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
[Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
[Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
[Zaškrtnuto a nezaškrtnuto](../../../csharp/language-reference/keywords/checked-and-unchecked.md)  
[unchecked](../../../csharp/language-reference/keywords/unchecked.md)
