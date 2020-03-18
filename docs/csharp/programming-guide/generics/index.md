---
title: Obecné typy – programovací příručka jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: c7252180c9c98a8ca99c8cc6b3faaf8b1b8f0749
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79167489"
---
# <a name="generics-c-programming-guide"></a>Obecné typy (Průvodce programováním v C#)

Obecné typy zavést koncept parametrů typu rozhraní .NET Framework, které umožňují navrhnout třídy a metody, které odložit specifikaci jednoho nebo více typů, dokud třída nebo metoda je deklarována a vytvořena pomocí kódu klienta. Například pomocí parametru `T`obecného typu můžete napsat jednu třídu, kterou může použít jiný kód klienta, aniž by vznikly náklady nebo riziko přetypování za běhu nebo operací zabalení, jak je znázorněno zde:

[!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]

Obecné třídy a metody kombinují opětovnou použitelnost, bezpečnost typů a účinnost způsobem, který jejich neobecné protějšky nemohou. Obecné typy se nejčastěji používají s kolekcemi a metodami, které na nich pracují. Obor <xref:System.Collections.Generic> názvů obsahuje několik obecných tříd kolekce. Neobecné kolekce, například <xref:System.Collections.ArrayList> nejsou doporučeny a jsou udržovány pro účely kompatibility. Další informace naleznete [v tématu Generics in .NET](../../../standard/generics/index.md).

Samozřejmě můžete také vytvořit vlastní obecné typy a metody, které poskytují vlastní zobecněná řešení a návrhové vzory, které jsou bezpečné pro daný typ a efektivní. Následující příklad kódu ukazuje jednoduchou obecnou třídu propojeného seznamu pro demonstrační účely. (Ve většině případů byste <xref:System.Collections.Generic.List%601> měli použít třídu poskytovanou knihovnou tříd rozhraní .NET Framework namísto vytváření vlastních.) Parametr `T` type se používá v několika umístěních, kde by se obvykle používal konkrétní typ k označení typu položky uložené v seznamu. Používá se následujícími způsoby:

- Jako typ parametru metody `AddHead` v metodě.
- Jako návratový typ `Data` vlastnosti v `Node` nosné třídě.
- Jako typ soukromého `data` člena v vnořené třídě.

 Všimněte `T` si, že `Node` je k dispozici vnořené třídy. Pokud `GenericList<T>` je vytvořena instance s konkrétním typem, `GenericList<int>`například `T` jako , bude `int`každý výskyt nahrazen .

[!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]

Následující příklad kódu ukazuje, jak `GenericList<T>` kód klienta používá obecnou třídu k vytvoření seznamu celá čísla. Jednoduše změnou argumentu typu lze následující kód snadno upravit tak, aby vytvářel seznamy řetězců nebo jiného vlastního typu:

[!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]

## <a name="generics-overview"></a>Obecný ch od obecně

- Obecné typy slouží k maximalizaci opakovaného použití kódu, bezpečnosti typů a výkonu.
- Nejběžnější použití obecných typů je k vytvoření tříd kolekce.
- Knihovna tříd rozhraní .NET Framework obsahuje <xref:System.Collections.Generic> několik nových obecných tříd kolekce v oboru názvů. Ty by měly být použity <xref:System.Collections.ArrayList> vždy, když je to možné namísto tříd, <xref:System.Collections> například v oboru názvů.
- Můžete vytvořit vlastní obecná rozhraní, třídy, metody, události a delegáty.
- Obecné třídy mohou být omezeny, aby umožnily přístup k metodám na konkrétních datových typech.
- Informace o typech, které se používají v obecném datovém typu, lze získat za běhu pomocí reflexe.

## <a name="related-sections"></a>Související oddíly

- [Parametry obecného typu](generic-type-parameters.md)
- [Omezení parametrů typů](constraints-on-type-parameters.md)
- [Obecné třídy](generic-classes.md)
- [Obecná rozhraní](generic-interfaces.md)
- [Obecné metody](generic-methods.md)
- [Obecní delegáti](generic-delegates.md)
- [Rozdíly mezi šablonami C++ a obecnými typy C#](differences-between-cpp-templates-and-csharp-generics.md)
- [Obecné typy a reflexe](generics-and-reflection.md)
- [Obecné typy v běhovém prostředí](generics-in-the-run-time.md)

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [Specifikace jazyka C#](~/_csharplang/spec/types.md#constructed-types).

## <a name="see-also"></a>Viz také

- <xref:System.Collections.Generic>
- [Programovací příručka jazyka C#](../index.md)
- [Typy](../types/index.md)
- [\<typeparam>](../xmldoc/typeparam.md)
- [\<typeparamref>](../xmldoc/typeparamref.md)
- [Obecné typy v .NET](../../../standard/generics/index.md)
