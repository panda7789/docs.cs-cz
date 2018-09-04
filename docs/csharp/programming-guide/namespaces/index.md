---
title: Obory názvů (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: 0e678f6577c07e4d56c485e0fd104397eddbd079
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43517452"
---
# <a name="namespaces-c-programming-guide"></a>Obory názvů (Průvodce programováním v C#)
Obory názvů často slouží v jazyce C# programming dvěma způsoby. Nejprve rozhraní .NET Framework používá obory názvů pro uspořádání mnoho tříd, následujícím způsobem:  
  
 [!code-csharp[csProgGuide#22](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_1.cs)]  
  
 `System` obor názvů a `Console` je třída v tomto oboru názvů. `using` – Klíčové slovo je možné tak, že úplný název není povinné, jako v následujícím příkladu:  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_2.cs)]  
  
 [!code-csharp[csProgGuide#25](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_3.cs)]  
  
 Další informace najdete v tématu [direktiva using](../../../csharp/language-reference/keywords/using-directive.md).  
  
 Za druhé deklarující vlastní obory názvů vám může pomoct určit obor názvů třídy a metody do větších programovací projektů. Použití [obor názvů](../../../csharp/language-reference/keywords/namespace.md) – klíčové slovo k deklarování oboru názvů, jako v následujícím příkladu:  
  
 [!code-csharp[csProgGuideNamespaces#6](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/index_4.cs)]  
  
## <a name="namespaces-overview"></a>Přehled názvových prostorů  
 Obory názvů mají následující vlastnosti:  
  
-   Organizují velkých kódových projektů.  
  
-   Jsou oddělené pomocí `.` operátor.  
  
-   `using directive` Požadavku k určení názvu oboru názvů pro každou třídu, vyloučí.  
  
-   `global` "Kořenový" obor názvů je obor názvů: `global::System` bude vždycky odkazovat na obor názvů rozhraní .NET Framework `System`.  
  
## <a name="related-sections"></a>Související oddíly  
 Zobrazit další informace o oborech názvů v následujících tématech:  
  
-   [Použití oboru názvů](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [Postupy: Použití aliasu globálního oboru názvů](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
-   [Postupy: Použití oboru názvů My](../../../csharp/programming-guide/namespaces/how-to-use-the-my-namespace.md)  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Klíčová slova oboru názvů](../../../csharp/language-reference/keywords/namespace-keywords.md)  
- [using – direktiva](../../../csharp/language-reference/keywords/using-directive.md)  
- [:: – operátor](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
- [. – operátor](../../../csharp/language-reference/operators/member-access-operator.md)
