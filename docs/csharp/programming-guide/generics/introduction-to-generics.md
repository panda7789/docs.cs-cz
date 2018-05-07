---
title: Úvod do obecných typů (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], about generics
ms.assetid: a1ad761e-42f7-41dd-a62f-452a2de26b9d
ms.openlocfilehash: 892b6bfe5cf18bde91221bb8b2fa7ca7a2813870
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="introduction-to-generics-c-programming-guide"></a>Úvod do obecných typů (Průvodce programováním v C#)
Obecné třídy a metody kombinovat – opětovné použití, bezpečnost typů a efektivitu způsobem, který nelze jejich neobecné protějšky. Obecné typy jsou nejčastěji používá s kolekcí a metody, které pracovat s nimi. Knihovna tříd rozhraní .NET Framework verze 2.0 poskytuje nový obor názvů, <xref:System.Collections.Generic>, která obsahuje několik nové třídy kolekcí založených na obecné. Doporučuje se, že všechny aplikace, jejichž cílem rozhraní .NET Framework 2.0 a pozdější použití nové obecnou kolekci třídy místo starší svými protějšky neobecnou, jako <xref:System.Collections.ArrayList>. Další informace najdete v tématu [obecné typy v rozhraní .NET](../../../standard/generics/index.md).  
  
 Samozřejmě můžete také vytvořit vlastní obecné typy a metody, které poskytují vlastní zobecněn řešení a vzory návrhu, které jsou bezpečnost typů a efektivní. Následující příklad kódu ukazuje jednoduchý obecné třídy-list pro demonstrační účely. (Ve většině případů byste měli použít <xref:System.Collections.Generic.List%601> poskytuje knihovna tříd rozhraní .NET Framework místo vytvoření vlastní třídy.) Parametr typu `T` se používá na různých místech, kde na konkrétní typ. by obvykle bylo použito k označení typ položky uložené v seznamu. Použije se následujícími způsoby:  
  
-   Jako typ parametru metody v `AddHead` metoda.  
  
-   Jako návratový typ `Data` vlastnost vnořeného `Node` třídy.  
  
-   Jako typ privátního člena `data` ve vnořené třídy.  
  
 Upozorňujeme, že je k dispozici pro vnořeného T `Node` třídy. Když `GenericList<T>` je vytvořena s konkrétní typu, například jako `GenericList<int>`, každý výskyt `T` nahradí `int`.  
  
 [!code-csharp[csProgGuideGenerics#2](../../../csharp/programming-guide/generics/codesnippet/CSharp/introduction-to-generics_1.cs)]  
  
 Následující příklad kódu ukazuje, jak kód klienta používá obecná `GenericList<T>` třídy můžete vytvořit seznam celých čísel. Jednoduše změnou argument typu následující kód mohl snadno změnit vytvořit seznam řetězců nebo jiných vlastního typu:  
  
 [!code-csharp[csProgGuideGenerics#3](../../../csharp/programming-guide/generics/codesnippet/CSharp/introduction-to-generics_2.cs)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Collections.Generic>  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Obecné typy](../../../csharp/programming-guide/generics/index.md)
