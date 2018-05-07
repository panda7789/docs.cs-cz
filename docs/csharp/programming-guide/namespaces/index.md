---
title: Obory názvů (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: 60e4c6e98ca9e71d1a095a0c7ee1df6be6d13f4b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="namespaces-c-programming-guide"></a>Obory názvů (Průvodce programováním v C#)
Obory názvů výraznou slouží v jazyce C# programování dvěma způsoby. Rozhraní .NET Framework nejprve používá obory názvů pro uspořádání mnoho tříd, následujícím způsobem:  
  
 [!code-csharp[csProgGuide#22](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_1.cs)]  
  
 `System` je obor názvů a `Console` je třída v daném oboru názvů. `using` – Klíčové slovo lze tak, aby úplný název není vyžadována, jako v následujícím příkladu:  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_2.cs)]  
  
 [!code-csharp[csProgGuide#25](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_3.cs)]  
  
 Další informace najdete v tématu [using – direktiva](../../../csharp/language-reference/keywords/using-directive.md).  
  
 Druhý deklarace vlastní oborů názvů vám může pomoct řídit oboru názvů třídy a metody větší programovací projektů. Použití [obor názvů](../../../csharp/language-reference/keywords/namespace.md) – klíčové slovo k deklaraci oboru názvů, jako v následujícím příkladu:  
  
 [!code-csharp[csProgGuideNamespaces#6](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/index_4.cs)]  
  
## <a name="namespaces-overview"></a>Přehled oborů názvů  
 Obory názvů mít následující vlastnosti:  
  
-   Jejich uspořádání projekty velké kódu.  
  
-   Jsou oddělené pomocí `.` operátor.  
  
-   `using directive` Požadavek na zadejte název oboru názvů pro každou třídu, vyloučí.  
  
-   `global` Obor názvů je obor názvů "root": `global::System` bude vždy odkaz na obor názvů rozhraní .NET Framework `System`.  
  
## <a name="related-sections"></a>Související oddíly  
 Najdete další informace o oborech názvů v následujících tématech:  
  
-   [Použití oboru názvů](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [Postupy: Použití aliasu globálního oboru názvů](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
-   [Postupy: Použití oboru názvů My](../../../csharp/programming-guide/namespaces/how-to-use-the-my-namespace.md)  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova oboru názvů](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [using – direktiva](../../../csharp/language-reference/keywords/using-directive.md)  
 [:: – operátor](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [. – operátor](../../../csharp/language-reference/operators/member-access-operator.md)
