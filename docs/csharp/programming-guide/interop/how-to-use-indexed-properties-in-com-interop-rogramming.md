---
title: "Postupy: Použití indexovaných vlastností při programování zprostředkovatele komunikace s objekty COM (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6ccd4248730d3c89528dad62b3f8ced3b9e42b0f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a>Postupy: Použití indexovaných vlastností při programování zprostředkovatele komunikace s objekty COM (Průvodce programováním v C#)
*Indexované vlastnosti* zlepšit způsob v COM, které se spotřebovávají vlastnosti, které mají parametry v C# – programování. Indexované vlastnosti pracovních společně s další funkce v jazyce Visual C#, jako [pojmenované a nepovinné argumenty](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md), nový typ ([dynamické](../../../csharp/language-reference/keywords/dynamic.md)), a [vložených informací o typu](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)do vylepšení programování pro Microsoft Office.  
  
 V dřívějších verzích jazyka C#, jsou dostupné jako vlastnosti jenom v případě metody `get` metoda nemá žádné parametry a `set` metoda má jeden parametr hodnoty. Ne všechny vlastnosti modelu COM však splňovat tato omezení. Například aplikace Excel [rozsah](http://go.microsoft.com/fwlink/?LinkId=166053) vlastnost má `get` přistupujícího objektu, který vyžaduje parametr pro název oblasti. V minulosti protože nelze získat přístup k `Range` vlastnost přímo, jste museli používat `get_Range` metoda místo toho, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideIndexedProperties#1](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_1.cs)]  
  
 Indexované vlastnosti umožňují zápisu následující místo:  
  
 [!code-csharp[csProgGuideIndexedProperties#2](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_2.cs)]  
  
> [!NOTE]
>  Předchozí příklad používá také [volitelné argumenty](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md) funkci, která umožňuje vynechat `Type.Missing`.  
  
 Podobně se nastavit hodnotu `Value` vlastnost [rozsah](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.aspx) objektů v aplikaci Visual C# 2008 a starší, dva argumenty jsou povinné. Poskytuje jeden argument volitelný parametr, který určuje typ hodnoty rozsahu. Druhá hodnota poskytuje `Value` vlastnost. Následující příklady znázorňují těchto postupů. Jak nastavit hodnotu buňky A1 do `Name`.
  
 [!code-csharp[csProgGuideIndexedProperties#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_3.cs)]  
  
 Indexované vlastnosti umožňují místo zápisu následující kód.  
  
 [!code-csharp[csProgGuideIndexedProperties#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_4.cs)]  
  
 Nelze vytvořit indexované vlastnosti. Tato funkce podporuje jenom spotřeba existující indexované vlastnosti.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje kompletní příklad. Další informace o tom, jak nastavit projekt, který má přístup k rozhraní API Office najdete v tématu [postupy: přístup k objektům zprostředkovatel komunikace s objekty Office pomocí Visual C# funkce](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).  
  
 [!code-csharp[csProgGuideIndexedProperties#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_5.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Pojmenované a nepovinné argumenty](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)  
 [dynamické](../../../csharp/language-reference/keywords/dynamic.md)  
 [Použití typu dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md)  
 [Postupy: použití pojmenovaných a nepovinných argumentů v programování pro Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)  
 [Postupy: přístup k objektům spolupráce sady Office pomocí Visual C# – funkce](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
 [Návod: Programování pro Office](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
