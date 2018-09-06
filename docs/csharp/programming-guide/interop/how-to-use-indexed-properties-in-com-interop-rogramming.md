---
title: 'Postupy: Použití indexovaných vlastností při programování zprostředkovatele komunikace s objekty COM (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: 0169bfa6eb3ba01a9a88c2b247ad3f78da67d59c
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43884523"
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a>Postupy: Použití indexovaných vlastností při programování zprostředkovatele komunikace s objekty COM (Průvodce programováním v C#)
*Indexované vlastnosti* zlepšit způsob, ve které modelu COM jsou vlastnosti, které mají parametry spotřebovány v programování v jazyce C#. Indexované vlastnosti pracují společně pomocí dalších funkcí v jazyce Visual C#, jako například [pojmenované a nepovinné argumenty](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md), nový typ ([dynamické](../../../csharp/language-reference/keywords/dynamic.md)), a [vložené informace o typu](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)do Vylepšete programování pro sadu Microsoft Office.  
  
 V dřívějších verzích jazyka C#, jsou dostupné jako vlastnosti pouze v případě metody `get` metoda nemá žádné parametry a `set` metoda má jeden a pouze jeden parametr hodnoty. Ale ne všechny vlastnosti modelu COM splnění těchto omezení. Například v aplikaci Excel <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> má vlastnost `get` přístupový objekt, který vyžaduje parametr pro název oblasti. V minulosti protože nelze získat přístup k `Range` vlastnost přímo, musíte použít `get_Range` metoda místo toho, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideIndexedProperties#1](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_1.cs)]  
  
 Indexované vlastnosti umožňují také napsat následující místo:  
  
 [!code-csharp[csProgGuideIndexedProperties#2](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_2.cs)]  
  
> [!NOTE]
>  V předchozím příkladu se používá také [volitelné argumenty](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md) funkci, která umožňuje vynechat `Type.Missing`.  
  
 Podobně se nastavit hodnotu `Value` vlastnost <xref:Microsoft.Office.Interop.Excel.Range> objektu v aplikaci Visual C# 2008 a dřívějších verzí se vyžadují dva argumenty. Poskytuje jeden argument pro volitelný parametr, který určuje typ hodnoty rozsahu. Druhá hodnota poskytuje `Value` vlastnost. Následující příklady znázorňují těchto technik. Obě hodnotu buňky A1 do `Name`.
  
 [!code-csharp[csProgGuideIndexedProperties#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_3.cs)]  
  
 Indexované vlastnosti umožňují místo toho zadejte následující kód.  
  
 [!code-csharp[csProgGuideIndexedProperties#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_4.cs)]  
  
 Nelze vytvořit indexované vlastnosti. Tato funkce podporuje pouze využití stávající indexované vlastnosti.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje kompletní příklad. Další informace o tom, jak nastavit projekt, který má přístup k rozhraní API pro Office naleznete v tématu [postupy: přístup k objektům Interop Office pomocí Visual C# pro funkce](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).  
  
 [!code-csharp[csProgGuideIndexedProperties#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_5.cs)]  
  
## <a name="see-also"></a>Viz také

- [Pojmenované a nepovinné argumenty](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)  
- [dynamic](../../../csharp/language-reference/keywords/dynamic.md)  
- [Použití typu dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md)  
- [Postupy: Použití pojmenovaných a nepovinných argumentů v programování pro sadu Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)  
- [Postupy: Přístup k objektům Interop sady Office pomocí funkcí Visual C#](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
- [Postupy: Programování pro systém Office](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
