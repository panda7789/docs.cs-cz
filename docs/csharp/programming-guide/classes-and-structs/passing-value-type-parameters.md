---
title: Předávání parametrů typu hodnoty – programovací příručka Jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- method parameters [C#], value types
- parameters [C#], value
ms.assetid: 193ab86f-5f9b-4359-ac29-7cdf8afad3a6
ms.openlocfilehash: 670af18d4b2b356aa33a0a03a29c05f5ba9bf78f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76744492"
---
# <a name="passing-value-type-parameters-c-programming-guide"></a>Předávání parametrů typu hodnoty (Průvodce programováním v C#)
Proměnná [typu value](../../language-reference/builtin-types/value-types.md) obsahuje svá data přímo na rozdíl od proměnné [typu odkazu,](../../language-reference/keywords/reference-types.md) která obsahuje odkaz na data. Předání proměnné typu hodnoty metodě pomocí hodnoty znamená předání kopie proměnné metodě. Všechny změny parametru, které probíhají uvnitř metody, nemají žádný vliv na původní data uložená v proměnné argumentu. Pokud chcete, aby volaná metoda změnila hodnotu argumentu, musíte ji předat odkazem pomocí klíčového slova [ref](../../language-reference/keywords/ref.md) nebo [out.](../../language-reference/keywords/out-parameter-modifier.md) Můžete také použít [v](../../language-reference/keywords/in-parameter-modifier.md) klíčové slovo předat parametr hodnoty odkazem, aby se zabránilo kopii a zároveň zaručit, že hodnota nebude změněna. Pro jednoduchost používají `ref`následující příklady .  
  
## <a name="passing-value-types-by-value"></a>Předávání typů hodnot podle hodnoty  
 Následující příklad ukazuje předávání parametrů typu hodnoty podle hodnoty. Proměnná `n` je předána hodnotou metodě `SquareIt`. Všechny změny, které probíhají uvnitř metody nemají žádný vliv na původní hodnotu proměnné.  
  
 [!code-csharp[csProgGuideParameters#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#3)]  
  
 Proměnná `n` je typ hodnoty. Obsahuje data, hodnotu `5`. Při `SquareIt` vyvolání `n` je obsah zkopírovány `x`do parametru , který je ve své metodě na druhou. V `Main`, však `n` hodnota je stejná `SquareIt` po volání metody, jak tomu bylo dříve. Změna, která probíhá uvnitř metody, `x`ovlivní pouze místní proměnnou .  
  
## <a name="passing-value-types-by-reference"></a>Předávání typů hodnot podle odkazu  
 Následující příklad je stejný jako v předchozím příkladu s `ref` tím rozdílem, že argument je předán jako parametr. Hodnota podkladového argumentu `n`, se `x` změní při změně metody.  
  
 [!code-csharp[csProgGuideParameters#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#4)]  
  
 V tomto příkladu není hodnota, `n` která je předána; spíše je předán `n` odkaz na. Parametr `x` není [int](../../language-reference/builtin-types/integral-numeric-types.md); jedná se o `int`odkaz na , v `n`tomto případě odkaz na . Proto, `x` když je na druhou uvnitř metody, co `x` je ve `n`skutečnosti na druhou, je to, co odkazuje na , .  
  
## <a name="swapping-value-types"></a>Zaměňování typů hodnot  
 Běžným příkladem změny hodnot argumentů je metoda odkládacího, kde předáte metodě dvě proměnné a metoda zamění jejich obsah. Argumenty je nutné předat metodě odkládacího vztahu odkazem. V opačném případě zaměníte místní kopie parametrů uvnitř metody a v metodě volání nedojde k žádné změně. Následující příklad zamění celé hodnoty.  
  
 [!code-csharp[csProgGuideParameters#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#5)]  
  
 Při volání `SwapByRef` metody použijte `ref` klíčové slovo v volání, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideParameters#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#6)]  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Předávání parametrů](./passing-parameters.md)
- [Předávání parametrů typu odkazu](./passing-reference-type-parameters.md)
