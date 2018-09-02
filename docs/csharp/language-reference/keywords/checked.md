---
title: checked – klíčové slovo (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- checked_CSharpKeyword
- checked
helpviewer_keywords:
- checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
ms.openlocfilehash: 892b24b0283314f5aded0405df55a93069cf91e2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43404026"
---
# <a name="checked-c-reference"></a>checked (Referenční dokumentace jazyka C#)

`checked` – Klíčové slovo se používá explicitně povolit kontroly pro integrálového typu aritmetické operace a převody přetečení.

Ve výchozím nastavení výraz, který obsahuje pouze konstantní hodnoty způsobí chybu kompilátoru, pokud výraz vytvoří hodnotu, která je mimo rozsah cílového typu. Pokud výraz obsahuje jednu nebo více hodnot, která není konstantní, kompilátor nezjistí přetečení. Vyhodnocení výrazu přiřazená `i2` v následujícím příkladu nezpůsobí chybu kompilátoru.

[!code-csharp[csrefKeywordsChecked#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#3)]

Ve výchozím nastavení tyto není konstantní výrazy nejsou zkontrolovat přetečení v době běhu buď a nevyvolávejte výjimky přetečení. Předchozí příklad zobrazuje-2,147,483,639 jako součet hodnot dvě kladná celá čísla.

Kontrola přetečení se dá nastavit možnosti kompilátoru, konfigurace prostředí nebo použití `checked` – klíčové slovo. Následující příklady ukazují, jak používat `checked` výraz nebo `checked` bloku k detekci přetečení, který je vytvořen v době běhu předchozí součet. Oba příklady vyvolat výjimku přetečení.

[!code-csharp[csrefKeywordsChecked#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#4)]

[Nekontrolovaná](../../../csharp/language-reference/keywords/unchecked.md) – klíčové slovo je možné zabránit kontrola přetečení.

## <a name="example"></a>Příklad

Tento příklad ukazuje způsob použití `checked` povolit kontroly za běhu přetečení.

[!code-csharp[csrefKeywordsChecked#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#1)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
- [Zaškrtnuto a nezaškrtnuto](../../../csharp/language-reference/keywords/checked-and-unchecked.md)  
- [unchecked](../../../csharp/language-reference/keywords/unchecked.md)
