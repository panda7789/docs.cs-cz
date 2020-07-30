---
title: Používání indexovaných vlastností v programování zprostředkovatele komunikace s objekty COM – Průvodce programováním v C#
description: Přečtěte si, jak indexované vlastnosti zlepšují způsob, jakým se v tomto příkladu jazyka C# spotřebovávají vlastnosti modelu COM, které mají parametry.
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: abd785864bd79d455024cb4501c76a21b349aa91
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303007"
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a>Používání indexovaných vlastností v programování zprostředkovatele komunikace s objekty COM (Průvodce programováním v C#)
*Indexované vlastnosti* zlepšují způsob, jakým jsou vlastnosti modelu COM, které mají parametry spotřebované v programování v jazyce C#. Indexované vlastnosti pracují společně s dalšími funkcemi v jazyce Visual C#, jako jsou [pojmenované a nepovinné argumenty](../classes-and-structs/named-and-optional-arguments.md), nový typ ([dynamický](../../language-reference/builtin-types/reference-types.md)) a [vložené informace o typu](../../../standard/assembly/embed-types-visual-studio.md), aby bylo možné vylepšit systém Microsoft Office programování.  
  
 V dřívějších verzích jazyka C# jsou metody přístupné jako vlastnosti pouze v případě, že `get` metoda nemá žádné parametry a `set` Metoda má jeden a pouze jeden parametr value. Ale ne všechny vlastnosti modelu COM tyto omezení nesplňují. Vlastnost aplikace Excel má například <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> `get` přistupující objekt, který vyžaduje parametr pro název rozsahu. Vzhledem k tomu, že nemůžete získat přístup k `Range` vlastnosti přímo, měli byste `get_Range` místo toho použít metodu, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideIndexedProperties#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#1)]  
  
 Indexované vlastnosti umožňují napsat následující místo:  
  
 [!code-csharp[csProgGuideIndexedProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#2)]  
  
> [!NOTE]
> Předchozí příklad také používá funkci [volitelné argumenty](../classes-and-structs/named-and-optional-arguments.md) , která umožňuje vynechat `Type.Missing` .  
  
 Podobně pro nastavení hodnoty `Value` vlastnosti <xref:Microsoft.Office.Interop.Excel.Range> objektu v C# 3,0 a starší jsou vyžadovány dva argumenty. Jeden zadá argument pro volitelný parametr, který určuje typ hodnoty rozsahu. Druhý zadá hodnotu `Value` Vlastnosti. Následující příklady ilustrují tyto techniky. Nastavte hodnotu buňky a1 na `Name` .
  
 [!code-csharp[csProgGuideIndexedProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#3)]  
  
 Indexované vlastnosti umožňují místo toho napsat následující kód.  
  
 [!code-csharp[csProgGuideIndexedProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#4)]  
  
 Nemůžete vytvořit indexované vlastnosti, které vlastníte. Funkce podporuje jenom spotřebu stávajících indexovaných vlastností.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje kompletní příklad. Další informace o tom, jak nastavit projekt, který přistupuje k rozhraní Office API, najdete v tématu [Jak získat přístup k objektům Interop sady Office pomocí funkcí jazyka C#](./how-to-access-office-onterop-objects.md).
  
 [!code-csharp[csProgGuideIndexedProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#5)]  
  
## <a name="see-also"></a>Viz také:

- [Pojmenované a nepovinné argumenty](../classes-and-structs/named-and-optional-arguments.md)
- [dynamické](../../language-reference/builtin-types/reference-types.md)
- [Použití typu dynamic](../types/using-type-dynamic.md)
- [Jak použít pojmenované a nepovinné argumenty v programování pro sadu Office](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [Jak získat přístup k objektům interoperability Office pomocí funkcí jazyka C#](./how-to-access-office-onterop-objects.md)
- [Návod: programování pro Office](./walkthrough-office-programming.md)
