---
title: "Úvod do obecných typů (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: generics [C#], about generics
ms.assetid: a1ad761e-42f7-41dd-a62f-452a2de26b9d
caps.latest.revision: "32"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ec4fe9cc9fe7bf868fcc8afe4dc4e4234241e352
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="introduction-to-generics-c-programming-guide"></a>Úvod do obecných typů (Průvodce programováním v C#)
Obecné třídy a metody kombinovat – opětovné použití, bezpečnost typů a efektivitu způsobem, který nelze jejich neobecné protějšky. Obecné typy jsou nejčastěji používá s kolekcí a metody, které pracovat s nimi. Knihovna tříd rozhraní .NET Framework verze 2.0 poskytuje nový obor názvů, <xref:System.Collections.Generic>, která obsahuje několik nové třídy kolekcí založených na obecné. Je doporučeno, všechny aplikace, která cílí [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 2.0 a vyšší použít nové třídy obecnou kolekci místo starší svými protějšky neobecnou například <xref:System.Collections.ArrayList>. Další informace najdete v tématu [obecné typy v knihovně tříd rozhraní .NET Framework](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md).  
  
 Samozřejmě můžete také vytvořit vlastní obecné typy a metody, které poskytují vlastní zobecněn řešení a vzory návrhu, které jsou bezpečnost typů a efektivní. Následující příklad kódu ukazuje jednoduchý obecné třídy-list pro demonstrační účely. (Ve většině případů byste měli použít <xref:System.Collections.Generic.List%601> poskytuje knihovna tříd rozhraní .NET Framework místo vytvoření vlastní třídy.) Parametr typu `T` se používá na různých místech, kde na konkrétní typ. by obvykle bylo použito k označení typ položky uložené v seznamu. Použije se následujícími způsoby:  
  
-   Jako typ parametru metody v `AddHead` metoda.  
  
-   Jako návratový typ veřejná metoda `GetNext` a `Data` vlastnost vnořeného `Node` třídy.  
  
-   Jako typ privátního člena dat ve vnořené třídy.  
  
 Upozorňujeme, že je k dispozici pro vnořeného T `Node` třídy. Když `GenericList<T>` je vytvořena s konkrétní typu, například jako `GenericList<int>`, každý výskyt `T` nahradí `int`.  
  
 [!code-csharp[csProgGuideGenerics#2](../../../csharp/programming-guide/generics/codesnippet/CSharp/introduction-to-generics_1.cs)]  
  
 Následující příklad kódu ukazuje, jak kód klienta používá obecná `GenericList<T>` třídy můžete vytvořit seznam celých čísel. Jednoduše změnou argument typu následující kód mohl snadno změnit vytvořit seznam řetězců nebo jiných vlastního typu:  
  
 [!code-csharp[csProgGuideGenerics#3](../../../csharp/programming-guide/generics/codesnippet/CSharp/introduction-to-generics_2.cs)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Collections.Generic>  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Obecné typy](../../../csharp/programming-guide/generics/index.md)
