---
title: Obecné typy (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: 638612a0ece8e701b088c97e5dfc49362e6d6419
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506078"
---
# <a name="generics-c-programming-guide"></a>Obecné typy (Průvodce programováním v C#)
Obecné typy byly přidány do verze 2.0 jazyka C# a common language runtime (CLR). Obecné typy rozhraní .NET Framework přinášejí koncept parametry typu, které umožňují návrh tříd a metod, které specifikace jeden nebo více typů odložit, dokud třídy nebo metody je deklarována a vytvořena kódem na straně klienta. Například můžete pomocí parametru obecného typu T napsat jednu třídu, jiný kód klienta můžete použít bez dalších nákladů na náklady nebo rizikem přetypování modulu runtime nebo operace zabalení, jak je znázorněno zde:  
  
 [!code-csharp[csProgGuideGenerics#1](../../../csharp/programming-guide/generics/codesnippet/CSharp/index_1.cs)]  
  
## <a name="generics-overview"></a>Přehled obecných typů  
  
-   Maximalizujte opakované využívání kódu, bezpečnost typů a výkonu pomocí obecných typů.  
  
-   Nejběžnější použití obecných typů je pro vytvoření kolekce tříd.  
  
-   Obsahuje několik nových obecné kolekce tříd v knihovně tříd rozhraní .NET Framework <xref:System.Collections.Generic> oboru názvů. Ty se používají vždy, když je možné namísto třídy, jako <xref:System.Collections.ArrayList> v <xref:System.Collections> oboru názvů.  
  
-   Můžete vytvořit vlastní obecných rozhraní, třídy, metody, události a delegáti.  
  
-   Obecné třídy může být omezený na povolení přístupu k metodám pro konkrétní datové typy.  
  
-   Informace o typech, které se používají v obecného datového typu mohou být získány při spuštění pomocí reflexe.  
  
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
  
-   [Obecné typy v běhovém prostředí](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 Další informace najdete v tématu [Specifikace jazyka C#](../../../csharp/language-reference/language-specification/index.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Collections.Generic>  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Typy](../../../csharp/programming-guide/types/index.md)  
- [\<typeparam >](../../../csharp/programming-guide/xmldoc/typeparam.md)  
- [\<typeparamref >](../../../csharp/programming-guide/xmldoc/typeparamref.md)  
- [Obecné typy v .NET](../../../standard/generics/index.md)  