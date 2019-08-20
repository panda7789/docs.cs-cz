---
title: 'Postupy: Použití indexovaných vlastností v programování zprostředkovatele komunikace C# s objekty COM – Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: 29132fa8d788f59178237be2c03adc1de4ac5c4f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589119"
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a>Postupy: Použití indexovaných vlastností v programování zprostředkovatele komunikaceC# s objekty COM (Průvodce programováním)
*Indexované vlastnosti* zlepšují způsob, jakým jsou vlastnosti modelu COM, které mají C# parametry spotřebované při programování. Indexované vlastnosti pracují společně s dalšími funkcemi v vizuálu C#, jako jsou [pojmenované a nepovinné argumenty](../classes-and-structs/named-and-optional-arguments.md), nový typ ([dynamický](../../language-reference/keywords/dynamic.md)) a [vložené informace o typu](../concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md), aby bylo možné vylepšit systém Microsoft Office programování.  
  
 V dřívějších verzích nástroje C#jsou metody přístupné jako vlastnosti pouze v případě `get` , že metoda nemá `set` žádné parametry a metoda má jeden a pouze jeden parametr value. Ale ne všechny vlastnosti modelu COM tyto omezení nesplňují. Vlastnost aplikace Excel <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> `get` má například přistupující objekt, který vyžaduje parametr pro název rozsahu. Vzhledem k tomu, že nemůžete získat přístup `Range` k vlastnosti přímo, měli byste místo toho `get_Range` použít metodu, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideIndexedProperties#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#1)]  
  
 Indexované vlastnosti umožňují napsat následující místo:  
  
 [!code-csharp[csProgGuideIndexedProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#2)]  
  
> [!NOTE]
>  Předchozí příklad také používá funkci [volitelné argumenty](../classes-and-structs/named-and-optional-arguments.md) , která umožňuje vynechat `Type.Missing`.  
  
 Podobně pro nastavení hodnoty `Value` vlastnosti <xref:Microsoft.Office.Interop.Excel.Range> objektu v C# 3,0 a starších verzích jsou vyžadovány dva argumenty. Jeden zadá argument pro volitelný parametr, který určuje typ hodnoty rozsahu. Druhý zadá hodnotu `Value` vlastnosti. Následující příklady ilustrují tyto techniky. Nastavte hodnotu buňky a1 na `Name`.
  
 [!code-csharp[csProgGuideIndexedProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#3)]  
  
 Indexované vlastnosti umožňují místo toho napsat následující kód.  
  
 [!code-csharp[csProgGuideIndexedProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#4)]  
  
 Nemůžete vytvořit indexované vlastnosti, které vlastníte. Funkce podporuje jenom spotřebu stávajících indexovaných vlastností.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje kompletní příklad. Další informace o tom, jak nastavit projekt, který přistupuje k rozhraní Office API, najdete v [tématu How to: Přístup k objektům Interop Office pomocí C# vizuálních funkcí](./how-to-access-office-onterop-objects.md)  
  
 [!code-csharp[csProgGuideIndexedProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#5)]  
  
## <a name="see-also"></a>Viz také:

- [Pojmenované a nepovinné argumenty](../classes-and-structs/named-and-optional-arguments.md)
- [dynamic](../../language-reference/keywords/dynamic.md)
- [Použití typu dynamic](../types/using-type-dynamic.md)
- [Postupy: Použití pojmenovaných a nepovinných argumentů v programování pro Office](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [Postupy: Přístup k objektům Interop Office pomocí C# vizuálních funkcí](./how-to-access-office-onterop-objects.md)
- [Návod: Programování pro Office](./walkthrough-office-programming.md)
