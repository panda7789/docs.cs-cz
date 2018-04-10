---
title: Obory názvů (Průvodce programováním v C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
caps.latest.revision: 27
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3eb645f5beb61d3cec97a70a54e660c65be52091
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="namespaces-c-programming-guide"></a>Obory názvů (Průvodce programováním v C#)
Obory názvů výraznou slouží v jazyce C# programování dvěma způsoby. Rozhraní .NET Framework nejprve používá obory názvů pro uspořádání mnoho tříd, následujícím způsobem:  
  
 [!code-csharp[csProgGuide#22](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_1.cs)]  
  
 `System`je obor názvů a `Console` je třída v daném oboru názvů. `using` – Klíčové slovo lze tak, aby úplný název není vyžadována, jako v následujícím příkladu:  
  
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
  
-   [Postupy: použití aliasu globálního Namespace](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
-   [Postupy: použití My Namespace](../../../csharp/programming-guide/namespaces/how-to-use-the-my-namespace.md)  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Namespace klíčová slova](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [Using – direktiva](../../../csharp/language-reference/keywords/using-directive.md)  
 [:: – Operátor](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [. Operátor](../../../csharp/language-reference/operators/member-access-operator.md)
