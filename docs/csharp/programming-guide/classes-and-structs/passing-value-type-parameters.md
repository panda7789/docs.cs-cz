---
title: Předávání parametrů typu hodnoty (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- method parameters [C#], value types
- parameters [C#], value
ms.assetid: 193ab86f-5f9b-4359-ac29-7cdf8afad3a6
ms.openlocfilehash: b64968a89f010f3f904d3a281d346d2ddf999e2f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="passing-value-type-parameters-c-programming-guide"></a>Předávání parametrů typu hodnoty (Průvodce programováním v C#)
A [typ hodnoty](../../../csharp/language-reference/keywords/value-types.md) proměnná obsahuje jeho data přímo jako naproti tomu [typu odkazu](../../../csharp/language-reference/keywords/reference-types.md) proměnné, která obsahuje odkaz na jeho data. Předání typu hodnoty proměnné na metodu hodnotou znamená předávání kopii proměnnou metodě. Všechny změny na parametr, které provést uvnitř metody mít žádný vliv na původní data uložená v proměnné argument. Pokud chcete zavolat metodu ke změně hodnoty parametru, je nutné předat odkazu, pomocí [ref](../../../csharp/language-reference/keywords/ref.md) nebo [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) – klíčové slovo. Můžete také používat [v](../../../csharp/language-reference/keywords/out-parameter-modifier.md) – klíčové slovo předat hodnotu parametru odkazem předejdete kopie při zaručení, že hodnota nebudou změněny. Pro jednoduchost, použijte následující příklady `ref`.  
  
## <a name="passing-value-types-by-value"></a>Typy hodnot předávání podle hodnoty  
 Následující příklad ukazuje předávání typu hodnoty parametrů hodnotou. Proměnná `n` hodnota předaná metodě `SquareIt`. Veškeré změny, které provést uvnitř metody mít žádný vliv na původní hodnotu proměnné.  
  
 [!code-csharp[csProgGuideParameters#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_1.cs)]  
  
 Proměnná `n` je typ hodnoty. Obsahuje svá data, hodnota `5`. Když `SquareIt` vyvolání obsah `n` se zkopírují do parametr `x`, který je uvnitř metody spolehlivosti. V `Main`, ale hodnota `n` je stejný po volání `SquareIt` způsob, jak byl před. Změna, která probíhá uvnitř metody se týká pouze místní proměnné `x`.  
  
## <a name="passing-value-types-by-reference"></a>Typy hodnot předávání odkazem  
 Následující příklad je stejný jako předchozí příklad, s tím rozdílem, že argument předaný jako `ref` parametr. Hodnota základní argumentu `n`, kdy se změní `x` se změnilo v metodě.  
  
 [!code-csharp[csProgGuideParameters#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_2.cs)]  
  
 V tomto příkladu není hodnota `n` předá; místo toho odkaz na `n` je předán. Parametr `x` není [int](../../../csharp/language-reference/keywords/int.md); je odkaz na `int`, v takovém případě odkaz na `n`. Proto když `x` je spolehlivosti uvnitř metody, co ve skutečnosti je spolehlivosti je co `x` odkazuje, `n`.  
  
## <a name="swapping-value-types"></a>Vzájemná záměna typy hodnot  
 Běžným příkladem změna hodnot argumentů je metoda odkládacího souboru, kde dvě proměnné, které předáte metodě, a metodu prohození jejich obsah. Argumenty, které je nutné předat do metodu swap odkazem. Jinak hodnota prohození místní kopie parametry uvnitř metody, a v metodě volání nedošlo k žádné změně. Následující příklad prohození celočíselné hodnoty.  
  
 [!code-csharp[csProgGuideParameters#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_3.cs)]  
  
 Při volání `SwapByRef` metoda, použijte `ref` – klíčové slovo v volání, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideParameters#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_4.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Předávání parametrů](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)  
 [Předávání parametrů typu odkazu](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)
