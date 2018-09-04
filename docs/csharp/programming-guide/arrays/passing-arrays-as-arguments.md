---
title: Předávání polí jako argumentů (C# Programming Guide)
ms.date: 07/05/2018
helpviewer_keywords:
- arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
ms.openlocfilehash: b2e6c0134af3b5814e9c9321e1486820311aa5c6
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43556188"
---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a>Předávání polí jako argumentů (C# Programming Guide)

Pole může být předány jako argumenty na parametry metod. Protože pole jsou typy odkazů, metodu můžete změnit hodnotu prvků.

## <a name="passing-single-dimensional-arrays-as-arguments"></a>Jednorozměrná předávání polí jako argumentů

Metodu můžete předat inicializované jednorozměrné pole. Například následující příkaz odešle pole tisku metodě.

[!code-csharp[csProgGuideArrays#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#34)]

Následující kód ukazuje částečnou implementaci metody tisku.

[!code-csharp[csProgGuideArrays#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#33)]

Můžete inicializovat a předat nové pole v jednom kroku, jak je znázorněno v následujícím příkladu.

[!code-csharp[CsProgGuideArrays#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#35)]

### <a name="example"></a>Příklad

V následujícím příkladu je pole řetězců inicializován a předat jako argument `DisplayArray` metodu pro řetězce. Metoda zobrazí prvků pole. Dále `ChangeArray` metoda obrátí prvků pole a pak `ChangeArrayElements` metoda upraví první tři prvky pole. Poté, co každá metoda vrací výsledek, `DisplayArray` metoda ukazuje, že předá podle hodnoty pole nezabrání změny k prvkům pole.

[!code-csharp[csProgGuideArrays#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/ArrayExample.cs)]

## <a name="passing-multidimensional-arrays-as-arguments"></a>Předání vícerozměrných polí jako argumentů

Inicializované vícerozměrná pole můžete předat metodě stejným způsobem, který předáte jednorozměrné pole.

[!code-csharp[csProgGuideArrays#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#41)]

Následující kód znázorňuje deklaraci částečné tisku metody, která přijímá jako svůj argument dvourozměrné pole.

[!code-csharp[csProgGuideArrays#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#36)]

Můžete inicializovat a předejte nové pole v jednom kroku, jak je znázorněno v následujícím příkladu:

[!code-csharp[csProgGuideArrays#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#32)]

### <a name="example"></a>Příklad

V následujícím příkladu je inicializován a předat dvourozměrné pole celých čísel `Print2DArray` metody. Metoda zobrazí prvků pole.

[!code-csharp[csProgGuideArrays#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#31)]

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)  
- [Pole](index.md)  
- [Jednorozměrná pole](single-dimensional-arrays.md)  
- [Vícerozměrná pole](multidimensional-arrays.md)  
- [Vícenásobná pole](jagged-arrays.md)  