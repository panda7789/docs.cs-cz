---
title: Obecné typy - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: e32eb7c60e01ca72824ffb3a1e1269cf34650f5a
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423400"
---
# <a name="generics-c-programming-guide"></a>Obecné typy (Průvodce programováním v C#)
Obecné typy byly přidány do verze 2.0 jazyka C# a common language runtime (CLR). Obecné typy rozhraní .NET Framework přinášejí koncept parametry typu, které umožňují návrh tříd a metod, které specifikace jeden nebo více typů odložit, dokud třídy nebo metody je deklarována a vytvořena kódem na straně klienta. Například můžete pomocí parametru obecného typu T napsat jednu třídu, jiný kód klienta můžete použít bez dalších nákladů na náklady nebo rizikem přetypování modulu runtime nebo operace zabalení, jak je znázorněno zde:  
  
 [!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]  

Obecné třídy a metody opětovné použití, bezpečnost typů a efektivitu tak, aby jejich obecné protějšky nelze kombinovat. Obecné typy se nejčastěji používají s kolekcí a metody, které pracují s nimi. Knihovna tříd rozhraní .NET Framework verze 2.0 obsahuje nový obor názvů <xref:System.Collections.Generic>, která obsahuje několik nových obecné kolekce tříd. Doporučuje se, že všechny aplikace, jejichž cílem rozhraní .NET Framework 2.0 a pozdější použití nové obecné kolekce tříd, namísto starší jejich obecné protějšky například <xref:System.Collections.ArrayList>. Další informace najdete v tématu [obecné typy v .NET](../../../standard/generics/index.md).  
  
 Samozřejmě můžete také vytvořit vlastní obecné typy a metody, které poskytují vlastní generalizované řešení a vzorů návrhu, které jsou typově bezpečné a efektivní. Následující příklad kódu ukazuje jednoduchý obecné třídy propojené seznamy pro demonstrační účely. (Ve většině případů byste měli použít <xref:System.Collections.Generic.List%601> poskytovaných knihovnou tříd rozhraní .NET Framework místo vytvoření vlastní třídy.) Parametr typu `T` se používá v několika umístěních, kde konkrétního typu implementujícího typ by obvykle použít k označení typu položky uložené v seznamu. Používá se následujícími způsoby:  
  
- Jako typ parametru metody `AddHead` metody.  
  
- Jako návratový typ `Data` vlastnost ve vnořeném `Node` třídy.  
  
- Jako typ soukromému členu `data` ve vnořené třídě.  
  
 Všimněte si, že je k dispozici ve vnořeném T `Node` třídy. Když `GenericList<T>` je vytvořena instance s konkrétního typu implementujícího typ, třeba jako `GenericList<int>`, každý výskyt `T` bude nahrazena adresou `int`.  
  
 [!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]  
  
 Následující příklad kódu ukazuje, jak kód klienta používá Obecné `GenericList<T>` třídy za účelem vytvoření seznamu celých čísel. Jednoduše tak, že změníte typ argumentu, následující kód by mohl snadno upravit tak, aby vytvořit seznam řetězců nebo jiný vlastní typ:  
  
 [!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]  
  
## <a name="generics-overview"></a>Přehled obecných typů  
  
- Maximalizujte opakované využívání kódu, bezpečnost typů a výkonu pomocí obecných typů.  
  
- Nejběžnější použití obecných typů je pro vytvoření kolekce tříd.  
  
- Obsahuje několik nových obecné kolekce tříd v knihovně tříd rozhraní .NET Framework <xref:System.Collections.Generic> oboru názvů. Ty se používají vždy, když je možné namísto třídy, jako <xref:System.Collections.ArrayList> v <xref:System.Collections> oboru názvů.  
  
- Můžete vytvořit vlastní obecných rozhraní, třídy, metody, události a delegáti.  
  
- Obecné třídy může být omezený na povolení přístupu k metodám pro konkrétní datové typy.  
  
- Informace o typech, které se používají v obecného datového typu mohou být získány při spuštění pomocí reflexe.  
  
## <a name="related-sections"></a>Související oddíly  
 Další informace:  
  
- [Parametry obecného typu](../../../csharp/programming-guide/generics/generic-type-parameters.md)  
  
- [Omezení parametrů typů](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
  
- [Obecné třídy](../../../csharp/programming-guide/generics/generic-classes.md)  
  
- [Obecná rozhraní](../../../csharp/programming-guide/generics/generic-interfaces.md)  
  
- [Obecné metody](../../../csharp/programming-guide/generics/generic-methods.md)  
  
- [Obecní delegáti](../../../csharp/programming-guide/generics/generic-delegates.md)  
  
- [Rozdíly mezi šablonami C++ a obecnými typy C#](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)  
  
- [Obecné typy a reflexe](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
- [Obecné typy v běhovém prostředí](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 Další informace najdete v tématu [Specifikace jazyka C#](~/_csharplang/spec/types.md#constructed-types).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Generic>
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Typy](../../../csharp/programming-guide/types/index.md)
- [\<typeparam >](../../../csharp/programming-guide/xmldoc/typeparam.md)
- [\<typeparamref>](../../../csharp/programming-guide/xmldoc/typeparamref.md)
- [Obecné typy v .NET](../../../standard/generics/index.md)
