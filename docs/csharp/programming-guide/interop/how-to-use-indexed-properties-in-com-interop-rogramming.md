---
title: Používání indexovaných vlastností v programování zprostředkovatele komunikace s objekty C# com – Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: aa4dc6da520fc58a99a9691aa39e412468aa02b5
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635311"
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a>Používání indexovaných vlastností v programování zprostředkovatele komunikace s objektyC# com (Průvodce programováním)
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
 Následující kód ukazuje kompletní příklad. Další informace o tom, jak nastavit projekt, který přistupuje k rozhraní Office API, najdete v tématu [Jak získat přístup k objektům Interop C# sady Office pomocí funkcí](./how-to-access-office-onterop-objects.md).
  
 [!code-csharp[csProgGuideIndexedProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#5)]  
  
## <a name="see-also"></a>Viz také:

- [Pojmenované a nepovinné argumenty](../classes-and-structs/named-and-optional-arguments.md)
- [dynamic](../../language-reference/builtin-types/reference-types.md)
- [Použití typu dynamic](../types/using-type-dynamic.md)
- [Použití pojmenovaných a nepovinných argumentů v programování pro Office](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [Přístup k objektům Interop sady Office pomocí C# funkcí](./how-to-access-office-onterop-objects.md)
- [Návod: programování pro Office](./walkthrough-office-programming.md)
