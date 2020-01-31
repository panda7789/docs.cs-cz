---
title: Předání parametrů typu hodnoty – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- method parameters [C#], value types
- parameters [C#], value
ms.assetid: 193ab86f-5f9b-4359-ac29-7cdf8afad3a6
ms.openlocfilehash: 670af18d4b2b356aa33a0a03a29c05f5ba9bf78f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744492"
---
# <a name="passing-value-type-parameters-c-programming-guide"></a>Předávání parametrů typu hodnoty (Průvodce programováním v C#)
Proměnná [typu hodnoty](../../language-reference/builtin-types/value-types.md) obsahuje svá data přímo na rozdíl od proměnné [typu odkazu](../../language-reference/keywords/reference-types.md) , která obsahuje odkaz na její data. Předání proměnné typu hodnoty metodě podle hodnoty znamená předání kopie proměnné metodě. Jakékoli změny parametru, které probíhají v metodě, nemají žádný vliv na původní data uložená v proměnné argumentu. Chcete-li, aby volaná metoda změnila hodnotu argumentu, je nutné ji předat odkazem pomocí klíčového slova [ref](../../language-reference/keywords/ref.md) nebo [out](../../language-reference/keywords/out-parameter-modifier.md) . Můžete také použít klíčové slovo [in](../../language-reference/keywords/in-parameter-modifier.md) k předání parametru hodnoty odkazem k tomu, aby se zabránilo kopírování a zároveň zaručeno, že hodnota nebude změněna. Pro zjednodušení následující příklady používají `ref`.  
  
## <a name="passing-value-types-by-value"></a>Předávání typů hodnot podle hodnoty  
 Následující příklad ukazuje předání parametrů typu hodnoty podle hodnoty. Proměnná `n` je předána hodnotou do metody `SquareIt`. Všechny změny, které probíhají v metodě, nemají žádný vliv na původní hodnotu proměnné.  
  
 [!code-csharp[csProgGuideParameters#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#3)]  
  
 Proměnná `n` je typ hodnoty. Obsahuje data, hodnota `5`. Při vyvolání `SquareIt` je obsah `n` zkopírován do parametru `x`, který je v rámci metody čtvercový. V `Main`je však hodnota `n` stejná po volání metody `SquareIt` jako předtím. Změny, které probíhají v rámci metody, ovlivňují pouze místní proměnnou `x`.  
  
## <a name="passing-value-types-by-reference"></a>Předávání typů hodnot odkazem  
 Následující příklad je stejný jako předchozí příklad s tím rozdílem, že argument je předán jako parametr `ref`. Hodnota podkladového argumentu, `n`, se změní, když se v metodě změní `x`.  
  
 [!code-csharp[csProgGuideParameters#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#4)]  
  
 V tomto příkladu není hodnota `n`, která je předána; místo toho se předává odkaz na `n`. Parametr `x` není typu [int](../../language-reference/builtin-types/integral-numeric-types.md); odkaz na `int`, v tomto případě odkaz na `n`. Proto když je v metodě `x` čtverce, co je ve skutečnosti na čtverci, co `x` odkazuje na `n`.  
  
## <a name="swapping-value-types"></a>Výměna hodnotových typů  
 Běžným příkladem změny hodnot argumentů je metoda swap, kde předáváte do metody dvě proměnné a metoda zahodí jejich obsah. Argumenty metody swap je nutné předat odkazem. V opačném případě provedete prohození místních kopií parametrů uvnitř metody a v metodě volání nedojde k žádným změnám. Následující příklad odměňuje celočíselné hodnoty.  
  
 [!code-csharp[csProgGuideParameters#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#5)]  
  
 Při volání metody `SwapByRef` použijte klíčové slovo `ref` v volání, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideParameters#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#6)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Předávání parametrů](./passing-parameters.md)
- [Předávání parametrů typu odkazu](./passing-reference-type-parameters.md)
