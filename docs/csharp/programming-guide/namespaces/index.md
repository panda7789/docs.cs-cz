---
title: Obory názvů (Průvodce programováním v C#)
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: c5431e5141b1b4b1981f4a1399ca11939fe7dc45
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53151106"
---
# <a name="namespaces-c-programming-guide"></a>Obory názvů (Průvodce programováním v C#)

Obory názvů často slouží v jazyce C# programming dvěma způsoby. Nejprve rozhraní .NET Framework používá obory názvů pro uspořádání mnoho tříd, následujícím způsobem:  
  
[!code-csharp[csProgGuide#22](../inside-a-program/codesnippet/CSharp/index_1.cs)]  
  
`System` obor názvů a `Console` je třída v tomto oboru názvů. `using` – Klíčové slovo je možné tak, že úplný název není povinné, jako v následujícím příkladu:  
  
[!code-csharp[csProgGuide#1](../inside-a-program/codesnippet/CSharp/index_2.cs)]  
  
[!code-csharp[csProgGuide#25](../inside-a-program/codesnippet/CSharp/index_3.cs)]  
  
Další informace najdete v tématu [direktiva using](../../language-reference/keywords/using-directive.md).  
  
Za druhé deklarující vlastní obory názvů vám může pomoct určit obor názvů třídy a metody do větších programovací projektů. Použití [obor názvů](../../language-reference/keywords/namespace.md) – klíčové slovo k deklarování oboru názvů, jako v následujícím příkladu:  
  
[!code-csharp[csProgGuideNamespaces#6](codesnippet/CSharp/index_4.cs)]

Název oboru názvů musí být platný C# [název identifikátoru](../inside-a-program/identifier-names.md).

## <a name="namespaces-overview"></a>Přehled názvových prostorů  

Obory názvů mají následující vlastnosti:  
  
- Organizují velkých kódových projektů.  
- Jsou oddělené pomocí `.` operátor.  
- `using` Směrnice, vyloučí požadavku k určení názvu oboru názvů pro každou třídu.  
- `global` "Kořenový" obor názvů je obor názvů: `global::System` bude vždycky odkazovat na rozhraní .NET <xref:System> oboru názvů.  

## <a name="c-language-specification"></a>Specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Použití oboru názvů](using-namespaces.md)
- [Jak: Použití aliasu globálního Namespace](how-to-use-the-global-namespace-alias.md)
- [Jak: Použití My Namespace](how-to-use-the-my-namespace.md)
- [Průvodce programováním v jazyce C#](../index.md)  
- [Názvy identifikátorů](../inside-a-program/identifier-names.md)
- [Klíčová slova oboru názvů](../../language-reference/keywords/namespace-keywords.md)  
- [using – direktiva](../../language-reference/keywords/using-directive.md)  
- [:: – operátor](../../language-reference/operators/namespace-alias-qualifer.md)  
- [. – operátor](../../language-reference/operators/member-access-operator.md)
