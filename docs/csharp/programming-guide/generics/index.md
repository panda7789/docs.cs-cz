---
title: "Obecné typy (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0804ca0fcefcc53e06352accf9a2db19edb31037
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="generics-c-programming-guide"></a>Obecné typy (Průvodce programováním v C#)
Obecné typy byly přidány do verze 2.0 jazyka C# a modul CLR (CLR). Obecné typy představit rozhraní .NET Framework koncept parametry typu, které umožňují provádět návrhu třídy a metody, které odložení specifikace jeden nebo více typů, dokud třída nebo metoda je deklarována a vytvořena kódem na straně klienta. Například můžete pomocí parametr obecného typu T zápisu jednu třídu, která jiný kód klienta můžete použít aniž by docházelo k náklady nebo riziko přetypování runtime nebo zabalení operace, jak je vidět tady:  
  
 [!code-csharp[csProgGuideGenerics#1](../../../csharp/programming-guide/generics/codesnippet/CSharp/index_1.cs)]  
  
## <a name="generics-overview"></a>Přehled obecných typů  
  
-   Použijte obecné typy a maximalizovat tak opakované použití kódu, typ zabezpečení a výkonu.  
  
-   Obecné typy slouží nejčastěji pro vytvoření kolekce tříd.  
  
-   Obsahuje několik nových tříd obecnou kolekci v knihovně tříd rozhraní .NET Framework <xref:System.Collections.Generic> oboru názvů. Tyto by měl použít, kdykoli je možné místo třídy, jako <xref:System.Collections.ArrayList> v <xref:System.Collections> oboru názvů.  
  
-   Můžete vytvořit vlastní obecná rozhraní, tříd, metod, události a delegáti.  
  
-   Obecné třídy může být omezené na povolení přístupu k metodám pro konkrétní datové typy.  
  
-   Informace o typech, které se používají v obecný typ dat může získat za běhu pomocí reflexe.  
  
## <a name="related-sections"></a>Související oddíly  
 Další informace:  
  
-   [Úvod do obecných typů](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
  
-   [Výhody obecných typů](../../../csharp/programming-guide/generics/benefits-of-generics.md)  
  
-   [Parametry obecného typu](../../../csharp/programming-guide/generics/generic-type-parameters.md)  
  
-   [Omezení parametrů typů](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
  
-   [Obecné třídy](../../../csharp/programming-guide/generics/generic-classes.md)  
  
-   [Obecná rozhraní](../../../csharp/programming-guide/generics/generic-interfaces.md)  
  
-   [Obecné metody](../../../csharp/programming-guide/generics/generic-methods.md)  
  
-   [Obecní delegáti](../../../csharp/programming-guide/generics/generic-delegates.md)  
  
-   [Rozdíly mezi šablonami C++ a obecnými typy C#](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)  
  
-   [Obecné typy a reflexe](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
-   [Obecné typy v běhovém prostředí](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)  
  
-   [Obecné typy v knihovně tříd rozhraní .NET Framework](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md)  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 Další informace najdete v tématu [Specifikace jazyka C#](../../../csharp/language-reference/language-specification/index.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Collections.Generic>  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Typy](../../../csharp/programming-guide/types/index.md)  
 [\<typeparam >](../../../csharp/programming-guide/xmldoc/typeparam.md)  
 [\<typeparamref >](../../../csharp/programming-guide/xmldoc/typeparamref.md)
