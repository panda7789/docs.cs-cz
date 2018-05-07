---
title: Předávání polí jako argumentů (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
ms.openlocfilehash: d863cdc33a8a1a844aabbea9ba5876614e6e8dba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a>Předávání polí jako argumentů (Průvodce programováním v C#)
Pole může být předán jako argumenty pro parametry metody. Vzhledem k tomu, že pole jsou odkazové typy, metodu můžete změnit hodnotu elementy.  
  
## <a name="passing-single-dimensional-arrays-as-arguments"></a>Jednorozměrná předávání polí jako argumentů  
 Metodu lze předat inicializovaného jednorozměrná pole. Následující příkaz například odešle pole tiskové metodě.  
  
 [!code-csharp[csProgGuideArrays#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_1.cs)]  
  
 Následující kód ukazuje částečnou implementaci metodu tisku.  
  
 [!code-csharp[csProgGuideArrays#33](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_2.cs)]  
  
 Můžete inicializovat a předat nové pole v jednom kroku, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[CsProgGuideArrays#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_3.cs)]  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 V následujícím příkladu je pole řetězců inicializovat a předat jako argument k `PrintArray` metoda pro řetězce. Metoda zobrazí elementy pole. Dále metody `ChangeArray` a `ChangeArrayElement` se nazývají prokázat, že odesílání argument pole hodnotou nebrání změny na elementy pole.  
  
### <a name="code"></a>Kód  
 [!code-csharp[csProgGuideArrays#30](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_4.cs)]  
  
## <a name="passing-multidimensional-arrays-as-arguments"></a>Vícerozměrná pole předání jako argumentů  
 Inicializovaného multidimenzionálního pole můžete předat metodě stejným způsobem, že předáváte jednorozměrné pole.  
  
 [!code-csharp[csProgGuideArrays#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_5.cs)]  
  
 Následující kód ukazuje částečné deklaraci tiskové metodu, která přijímá dvourozměrná pole jako její argument.  
  
 [!code-csharp[csProgGuideArrays#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_6.cs)]  
  
 Můžete inicializovat a předat nové pole v jednom kroku, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideArrays#32](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_7.cs)]  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 V následujícím příkladu je inicializován a předaný dvourozměrná pole celých čísel `Print2DArray` metoda. Metoda zobrazí elementy pole.  
  
### <a name="code"></a>Kód  
 [!code-csharp[csProgGuideArrays#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_8.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Pole](../../../csharp/programming-guide/arrays/index.md)  
 [Jednorozměrná pole](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [Vícerozměrná pole](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [Vícenásobná pole](../../../csharp/programming-guide/arrays/jagged-arrays.md)
