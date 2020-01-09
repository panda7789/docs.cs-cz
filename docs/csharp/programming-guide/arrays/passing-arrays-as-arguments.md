---
title: Předávání polí jako argumentů – C# Průvodce programováním
ms.date: 07/05/2018
helpviewer_keywords:
- arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
ms.openlocfilehash: 2e53008910a9062ada25680eb4b8e54a225fd226
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705688"
---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a>Předávání polí jako argumentů (C# Průvodce programováním)

Pole mohou být předána jako argumenty parametrům metody. Vzhledem k tomu, že pole jsou odkazové typy, metoda může změnit hodnotu prvků.

## <a name="passing-single-dimensional-arrays-as-arguments"></a>Předávání jednorozměrného pole jako argumentů

Do metody můžete předat inicializované jednorozměrné pole. Například následující příkaz odešle pole do metody Print.

[!code-csharp[csProgGuideArrays#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#34)]

Následující kód ukazuje částečnou implementaci metody Print.

[!code-csharp[csProgGuideArrays#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#33)]

Můžete inicializovat a předat nové pole v jednom kroku, jak je znázorněno v následujícím příkladu.

[!code-csharp[CsProgGuideArrays#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#35)]

### <a name="example"></a>Příklad

V následujícím příkladu je pole řetězců inicializováno a předáno jako argument metodě `DisplayArray` pro řetězce. Metoda zobrazí prvky pole. Dále metoda `ChangeArray` obrátí prvky pole a poté metoda `ChangeArrayElements` upraví první tři prvky pole. Po vrácení každé metody metoda `DisplayArray` ukazuje, že předání pole hodnotou nezabrání změnám prvků pole.

[!code-csharp[csProgGuideArrays#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/ArrayExample.cs)]

## <a name="passing-multidimensional-arrays-as-arguments"></a>Předávání multidimenzionálních polí jako argumentů

Inicializované multidimenzionální pole do metody předáte stejným způsobem jako jednorozměrné pole.

[!code-csharp[csProgGuideArrays#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#41)]

Následující kód ukazuje částečnou deklaraci metody Print, která přijímá dvojrozměrné pole jako argument.

[!code-csharp[csProgGuideArrays#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#36)]

Můžete inicializovat a předat nové pole v jednom kroku, jak je znázorněno v následujícím příkladu:

[!code-csharp[csProgGuideArrays#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#32)]

### <a name="example"></a>Příklad

V následujícím příkladu je inicializováno dvojrozměrné pole celých čísel a předáno do metody `Print2DArray`. Metoda zobrazí prvky pole.

[!code-csharp[csProgGuideArrays#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#31)]

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Pole](index.md)
- [Jednorozměrná pole](single-dimensional-arrays.md)
- [Vícerozměrná pole](multidimensional-arrays.md)
- [Vícenásobná pole](jagged-arrays.md)
