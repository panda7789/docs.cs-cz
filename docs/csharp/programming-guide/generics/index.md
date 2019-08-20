---
title: Obecné typy – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: 7d212aeaa7d7a8c3f152f8610a7ef3fe5de0fe23
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589604"
---
# <a name="generics-c-programming-guide"></a>Obecné typy (Průvodce programováním v C#)
Obecné typy byly přidány do verze 2,0 C# jazyka a modulu CLR (Common Language Runtime). Obecné typy představují .NET Framework konceptu parametrů typu, který umožňuje navrhovat třídy a metody, které odloží specifikaci jednoho nebo více typů, dokud není deklarována třída nebo metoda a vytvořena instance klientského kódu. Například pomocí obecného typu parametru T můžete napsat jednu třídu, kterou může jiný klientský kód použít, aniž by vznikly náklady nebo riziko přetypování za běhu nebo zabalení, jak je znázorněno zde:  
  
 [!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]  

Obecné třídy a metody kombinují opětovné použitelnost, bezpečnost typů a efektivitu způsobem, že jejich neobecné protějšky nemůžou. Obecné typy se nejčastěji používají s kolekcemi a metodami, které na nich pracují. Verze 2,0 knihovny tříd .NET Framework poskytuje nový obor názvů <xref:System.Collections.Generic>, který obsahuje několik nových obecných tříd kolekcí. Doporučuje se, aby všechny aplikace, které cílí na .NET Framework 2,0 a později používaly nové obecné třídy kolekce namísto starších neobecných protějšků, jako je <xref:System.Collections.ArrayList>. Další informace naleznete v tématu [Obecné typy v rozhraní .NET](../../../standard/generics/index.md).  
  
 Samozřejmě můžete také vytvořit vlastní obecné typy a metody, které poskytují vlastní generalizovaná řešení a vzory návrhu, které jsou typově bezpečné a efektivní. Následující příklad kódu ukazuje jednoduchou obecnou třídu propojených seznamů pro demonstrační účely. (Ve většině případů byste měli použít <xref:System.Collections.Generic.List%601> třídu poskytnutou .NET Framework knihovny tříd namísto vytvoření vlastní.) Parametr `T` typu se používá v několika umístěních, kde konkrétní typ by byl obvykle použit k označení typu položky uložené v seznamu. Používá se následujícími způsoby:  
  
- Jako typ parametru metody v `AddHead` metodě.  
  
- Jako návratový typ `Data` vlastnosti ve vnořené `Node` třídě.  
  
- Jako typ privátního člena `data` ve vnořené třídě.  
  
 Všimněte si, že T je k dispozici pro vnořenou `Node` třídu. Při `GenericList<T>` vytvoření instance se konkrétním typem, například `GenericList<int>`jako, každý výskyt `T` bude nahrazen `int`.  
  
 [!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]  
  
 Následující příklad kódu ukazuje, jak klientský kód používá obecnou `GenericList<T>` třídu k vytvoření seznamu celých čísel. Jednoduše změnou argumentu typu lze následující kód snadno upravit, aby bylo možné vytvořit seznam řetězců nebo jakýkoli jiný vlastní typ:  
  
 [!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]  
  
## <a name="generics-overview"></a>Obecné typy – přehled  
  
- Pomocí obecných typů maximalizujete opětovné použití kódu, bezpečnost typů a výkon.  
  
- Nejběžnějším použitím obecných typů je vytvoření tříd kolekcí.  
  
- Knihovna tříd .NET Framework obsahuje několik nových obecných tříd kolekcí v <xref:System.Collections.Generic> oboru názvů. Ty by měly být použity, kdykoli je to možné, <xref:System.Collections.ArrayList> nikoli třídy <xref:System.Collections> , jako je například v oboru názvů.  
  
- Můžete vytvořit vlastní Obecná rozhraní, třídy, metody, události a delegáty.  
  
- Obecné třídy mohou být omezeny, aby bylo možné povolit přístup k metodám pro konkrétní datové typy.  
  
- Informace o typech, které jsou použity v obecném datovém typu, lze získat za běhu pomocí reflexe.  
  
## <a name="related-sections"></a>Související oddíly  
 Další informace:  
  
- [Parametry obecného typu](./generic-type-parameters.md)  
  
- [Omezení parametrů typů](./constraints-on-type-parameters.md)  
  
- [Obecné třídy](./generic-classes.md)  
  
- [Obecná rozhraní](./generic-interfaces.md)  
  
- [Obecné metody](./generic-methods.md)  
  
- [Obecní delegáti](./generic-delegates.md)  
  
- [Rozdíly mezi šablonami C++ a obecnými typy C#](./differences-between-cpp-templates-and-csharp-generics.md)  
  
- [Obecné typy a reflexe](./generics-and-reflection.md)  
  
- [Obecné typy v běhovém prostředí](./generics-in-the-run-time.md)  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 Další informace najdete v tématu [Specifikace jazyka C#](~/_csharplang/spec/types.md#constructed-types).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Generic>
- [Průvodce programováním v jazyce C#](../index.md)
- [Typy](../types/index.md)
- [\<typeparam >](../xmldoc/typeparam.md)
- [\<typeparamref >](../xmldoc/typeparamref.md)
- [Obecné typy v .NET](../../../standard/generics/index.md)
