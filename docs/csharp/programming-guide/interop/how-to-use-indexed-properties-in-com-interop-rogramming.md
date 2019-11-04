---
title: 'Postupy: Použití indexovaných vlastností v programování zprostředkovatele komunikace s C# objekty COM – Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: 0d4e85646a1e7f8c4ee9a73fbf7bf5a01b10b14b
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423224"
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a>Postupy: Použití indexovaných vlastností při programování zprostředkovatele komunikace s objekty COM (Průvodce programováním v C#)
*Indexované vlastnosti* zlepšují způsob, jakým jsou vlastnosti modelu COM, které mají C# parametry spotřebované při programování. Indexované vlastnosti pracují společně s dalšími funkcemi v vizuálu C#, jako jsou [pojmenované a nepovinné argumenty](../classes-and-structs/named-and-optional-arguments.md), nový typ ([dynamický](../../language-reference/builtin-types/reference-types.md)) a [vložené informace o typu](../../../standard/assembly/embed-types-visual-studio.md), aby bylo možné vylepšit systém Microsoft Office programování.  
  
 V dřívějších verzích nástroje C#jsou metody přístupné jako vlastnosti pouze v případě, že metoda `get` nemá žádné parametry a metoda `set` má jeden a pouze jeden parametr value. Ale ne všechny vlastnosti modelu COM tyto omezení nesplňují. Například vlastnost Excel <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> má přistupující objekt `get`, který vyžaduje parametr pro název rozsahu. Vzhledem k tomu, že v minulosti jste nezískali přístup k vlastnosti `Range` přímo, museli byste místo toho použít metodu `get_Range`, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideIndexedProperties#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#1)]  
  
 Indexované vlastnosti umožňují napsat následující místo:  
  
 [!code-csharp[csProgGuideIndexedProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#2)]  
  
> [!NOTE]
> Předchozí příklad také používá funkci [volitelné argumenty](../classes-and-structs/named-and-optional-arguments.md) , která umožňuje vynechat `Type.Missing`.  
  
 Podobně pro nastavení hodnoty vlastnosti `Value` objektu <xref:Microsoft.Office.Interop.Excel.Range> v C# 3,0 a starších verzích jsou vyžadovány dva argumenty. Jeden zadá argument pro volitelný parametr, který určuje typ hodnoty rozsahu. Druhý zadá hodnotu vlastnosti `Value`. Následující příklady ilustrují tyto techniky. Nastavte hodnotu buňky a1 na `Name`.
  
 [!code-csharp[csProgGuideIndexedProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#3)]  
  
 Indexované vlastnosti umožňují místo toho napsat následující kód.  
  
 [!code-csharp[csProgGuideIndexedProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#4)]  
  
 Nemůžete vytvořit indexované vlastnosti, které vlastníte. Funkce podporuje jenom spotřebu stávajících indexovaných vlastností.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje kompletní příklad. Další informace o tom, jak nastavit projekt, který přistupuje k rozhraní Office API, naleznete v tématu [How to: Access Office Interop Objects Using C# a Visual Features](./how-to-access-office-onterop-objects.md).  
  
 [!code-csharp[csProgGuideIndexedProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#5)]  
  
## <a name="see-also"></a>Viz také:

- [Pojmenované a nepovinné argumenty](../classes-and-structs/named-and-optional-arguments.md)
- [dynamic](../../language-reference/builtin-types/reference-types.md)
- [Použití typu dynamic](../types/using-type-dynamic.md)
- [Postupy: Použití pojmenovaných a nepovinných argumentů v programování pro sadu Office](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [Postupy: Přístup k objektům Interop sady Office pomocí funkcí Visual C#](./how-to-access-office-onterop-objects.md)
- [Návod: programování pro Office](./walkthrough-office-programming.md)
