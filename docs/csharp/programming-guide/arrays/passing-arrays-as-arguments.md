---
title: Předávání polí jako argumentů – Průvodce programováním jazyka C#
ms.date: 07/05/2018
helpviewer_keywords:
- arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
ms.openlocfilehash: 2e53008910a9062ada25680eb4b8e54a225fd226
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705688"
---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a>Předávání polí jako argumentů (Průvodce programováním jazyka C#)

Pole mohou být předána jako argumenty parametrům metody. Vzhledem k tomu, že pole jsou typy odkazů, metoda může změnit hodnotu prvků.

## <a name="passing-single-dimensional-arrays-as-arguments"></a>Předávání jednorozměrných polí jako argumentů

Metodě můžete předat inicializované jednorozměrné pole. Například následující příkaz odešle pole metodě tisku.

[!code-csharp[csProgGuideArrays#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#34)]

Následující kód ukazuje částečnou implementaci metody tisku.

[!code-csharp[csProgGuideArrays#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#33)]

Můžete inicializovat a předat nové pole v jednom kroku, jak je znázorněno v následujícím příkladu.

[!code-csharp[CsProgGuideArrays#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#35)]

### <a name="example"></a>Příklad

V následujícím příkladu je inicializováno pole řetězců a `DisplayArray` předáno jako argument metodě pro řetězce. Metoda zobrazí prvky pole. Dále `ChangeArray` metoda obrátí prvky pole a `ChangeArrayElements` potom metoda upraví první tři prvky pole. Po každé metoda `DisplayArray` vrátí, metoda ukazuje, že předávání pole podle hodnoty nezabrání změnám prvků pole.

[!code-csharp[csProgGuideArrays#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/ArrayExample.cs)]

## <a name="passing-multidimensional-arrays-as-arguments"></a>Předávání vícerozměrných polí jako argumentů

Inicializované vícerozměrné pole předáte metodě stejným způsobem, jakým předáte jednorozměrné pole.

[!code-csharp[csProgGuideArrays#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#41)]

Následující kód ukazuje částečnou deklaraci metody tisku, která přijímá dvourozměrné pole jako svůj argument.

[!code-csharp[csProgGuideArrays#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#36)]

Můžete inicializovat a předat nové pole v jednom kroku, jak je znázorněno v následujícím příkladu:

[!code-csharp[csProgGuideArrays#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#32)]

### <a name="example"></a>Příklad

V následujícím příkladu je inicializováno dvojrozměrné pole celáčísla a předáno metodě. `Print2DArray` Metoda zobrazí prvky pole.

[!code-csharp[csProgGuideArrays#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#31)]

## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Pole](index.md)
- [Jednorozměrná pole](single-dimensional-arrays.md)
- [Vícerozměrná pole](multidimensional-arrays.md)
- [Vícenásobná pole](jagged-arrays.md)
