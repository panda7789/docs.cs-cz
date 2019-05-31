---
title: Obory názvů - C# Průvodce programováním
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: 893ac7bbfcfe159787789238c3142f34ac7ecf35
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423286"
---
# <a name="namespaces-c-programming-guide"></a>Obory názvů (Průvodce programováním v C#)

Obory názvů často slouží v jazyce C# programming dvěma způsoby. Nejprve rozhraní .NET Framework používá obory názvů pro uspořádání mnoho tříd, následujícím způsobem:  
  
 [!code-csharp[csProgGuide#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#22)]  
  
`System` obor názvů a `Console` je třída v tomto oboru názvů. `using` – Klíčové slovo je možné tak, že úplný název není povinné, jako v následujícím příkladu:  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 [!code-csharp[csProgGuide#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#25)]  
  
Další informace najdete v tématu [direktiva using](../../language-reference/keywords/using-directive.md).  
  
Za druhé deklarující vlastní obory názvů vám může pomoct určit obor názvů třídy a metody do větších programovací projektů. Použití [obor názvů](../../language-reference/keywords/namespace.md) – klíčové slovo k deklarování oboru názvů, jako v následujícím příkladu:  
  
 [!code-csharp[csProgGuideNamespaces#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#6)]

Název oboru názvů musí být platný C# [název identifikátoru](../inside-a-program/identifier-names.md).

## <a name="namespaces-overview"></a>Přehled názvových prostorů  

Obory názvů mají následující vlastnosti:  
  
- Organizují velkých kódových projektů.  
- Jsou oddělené pomocí `.` operátor.  
- `using` Směrnice, vyloučí požadavku k určení názvu oboru názvů pro každou třídu.  
- `global` "Kořenový" obor názvů je obor názvů: `global::System` bude vždycky odkazovat na rozhraní .NET <xref:System> oboru názvů.  

## <a name="c-language-specification"></a>Specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Použití oboru názvů](using-namespaces.md)
- [Postupy: Použití aliasu globálního Namespace](how-to-use-the-global-namespace-alias.md)
- [Postupy: Použití My Namespace](how-to-use-the-my-namespace.md)
- [Názvy identifikátorů](../inside-a-program/identifier-names.md)
- [using – direktiva](../../language-reference/keywords/using-directive.md)
- [:: – operátor](../../language-reference/operators/namespace-alias-qualifer.md)
