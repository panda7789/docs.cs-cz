---
title: Použití indexovaných vlastností v programování mezi opcemi com - Průvodce programováním c#
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: 864e2274f0e0e79b4843e0bb67b5c4384eac8588
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712062"
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a>Použití indexovaných vlastností v programování interop com (C# Programovací průvodce)
*Indexované vlastnosti* zlepšují způsob, jakým jsou vlastnosti COM, které mají parametry, spotřebovány v programování jazyka C#. Indexované vlastnosti spolupracují s dalšími funkcemi v jazyce Visual C#, jako jsou [pojmenované a volitelné argumenty](../classes-and-structs/named-and-optional-arguments.md), nový typ ([dynamický](../../language-reference/builtin-types/reference-types.md)a [vložené informace o typu](../../../standard/assembly/embed-types-visual-studio.md), a vylepšují tak programování sady Microsoft Office.  
  
 V dřívějších verzích jazyka C# jsou metody `get` přístupné jako vlastnosti `set` pouze v případě, že metoda nemá žádné parametry a metoda má jeden a pouze jeden parametr hodnoty. Však ne všechny vlastnosti COM splňují tato omezení. Například vlastnost <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> aplikace Excel `get` má přistupující objekt, který vyžaduje parametr pro název rozsahu. V minulosti, protože jste `Range` nemohli přistupovat přímo k `get_Range` vlastnosti, jste museli použít metodu místo, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideIndexedProperties#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#1)]  
  
 Indexované vlastnosti umožňují místo toho napsat následující:  
  
 [!code-csharp[csProgGuideIndexedProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#2)]  
  
> [!NOTE]
> Předchozí příklad také používá funkci [volitelné argumenty,](../classes-and-structs/named-and-optional-arguments.md) která `Type.Missing`umožňuje vynechat .  
  
 Podobně nastavit hodnotu `Value` vlastnosti objektu <xref:Microsoft.Office.Interop.Excel.Range> v C# 3.0 a starší, jsou požadovány dva argumenty. Jeden poskytuje argument pro volitelný parametr, který určuje typ hodnoty rozsahu. Druhý poskytuje hodnotu vlastnosti. `Value` Následující příklady ilustrují tyto techniky. Obě nastaví hodnotu buňky `Name`A1 na hodnotu .
  
 [!code-csharp[csProgGuideIndexedProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#3)]  
  
 Indexované vlastnosti umožňují místo toho napsat následující kód.  
  
 [!code-csharp[csProgGuideIndexedProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#4)]  
  
 Vlastní indexované vlastnosti nelze vytvořit. Funkce podporuje pouze spotřebu existujících indexovaných vlastností.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje úplný příklad. Další informace o nastavení projektu, který přistupuje k rozhraní API sady Office, naleznete v tématu [Přístup k objektům interop sady Office pomocí funkcí jazyka C#](./how-to-access-office-onterop-objects.md).
  
 [!code-csharp[csProgGuideIndexedProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#5)]  
  
## <a name="see-also"></a>Viz také

- [Pojmenované a nepovinné argumenty](../classes-and-structs/named-and-optional-arguments.md)
- [Dynamické](../../language-reference/builtin-types/reference-types.md)
- [Použití typu dynamic](../types/using-type-dynamic.md)
- [Použití pojmenovaných a volitelných argumentů v programování sady Office](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [Jak získat přístup k objektům interoperability Office pomocí funkcí jazyka C#](./how-to-access-office-onterop-objects.md)
- [Návod: Programování v Office](./walkthrough-office-programming.md)
