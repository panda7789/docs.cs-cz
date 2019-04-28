---
title: Úvod do obecných typů - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], about generics
ms.assetid: a1ad761e-42f7-41dd-a62f-452a2de26b9d
ms.openlocfilehash: d09cc686e934f722193cb4671d25671f7f4ef5f7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61679788"
---
# <a name="introduction-to-generics-c-programming-guide"></a>Úvod do obecných typů (Průvodce programováním v C#)
Obecné třídy a metody opětovné použití, bezpečnost typů a efektivitu tak, aby jejich obecné protějšky nelze kombinovat. Obecné typy se nejčastěji používají s kolekcí a metody, které pracují s nimi. Knihovna tříd rozhraní .NET Framework verze 2.0 obsahuje nový obor názvů <xref:System.Collections.Generic>, která obsahuje několik nových obecné kolekce tříd. Doporučuje se, že všechny aplikace, jejichž cílem rozhraní .NET Framework 2.0 a pozdější použití nové obecné kolekce tříd, namísto starší jejich obecné protějšky například <xref:System.Collections.ArrayList>. Další informace najdete v tématu [obecné typy v .NET](../../../standard/generics/index.md).  
  
 Samozřejmě můžete také vytvořit vlastní obecné typy a metody, které poskytují vlastní generalizované řešení a vzorů návrhu, které jsou typově bezpečné a efektivní. Následující příklad kódu ukazuje jednoduchý obecné třídy propojené seznamy pro demonstrační účely. (Ve většině případů byste měli použít <xref:System.Collections.Generic.List%601> poskytovaných knihovnou tříd rozhraní .NET Framework místo vytvoření vlastní třídy.) Parametr typu `T` se používá v několika umístěních, kde konkrétního typu implementujícího typ by obvykle použít k označení typu položky uložené v seznamu. Používá se následujícími způsoby:  
  
- Jako typ parametru metody `AddHead` metody.  
  
- Jako návratový typ `Data` vlastnost ve vnořeném `Node` třídy.  
  
- Jako typ soukromému členu `data` ve vnořené třídě.  
  
 Všimněte si, že je k dispozici ve vnořeném T `Node` třídy. Když `GenericList<T>` je vytvořena instance s konkrétního typu implementujícího typ, třeba jako `GenericList<int>`, každý výskyt `T` bude nahrazena adresou `int`.  
  
 [!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]  
  
 Následující příklad kódu ukazuje, jak kód klienta používá Obecné `GenericList<T>` třídy za účelem vytvoření seznamu celých čísel. Jednoduše tak, že změníte typ argumentu, následující kód by mohl snadno upravit tak, aby vytvořit seznam řetězců nebo jiný vlastní typ:  
  
 [!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Generic>
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Obecné typy](../../../csharp/programming-guide/generics/index.md)
