---
title: Obory C# názvů – Průvodce programováním
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: 8a03baffc17da07ccab14c89dc9f99be2fc5ba1a
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635207"
---
# <a name="namespaces-c-programming-guide"></a>Obory názvů (Průvodce programováním v C#)

Obory názvů jsou v C# programování silně používány dvěma způsoby. Nejprve .NET Framework používá obory názvů k uspořádání svých mnoha tříd následujícím způsobem:  
  
 [!code-csharp[csProgGuide#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#22)]  
  
`System` je obor názvů a `Console` je třída v tomto oboru názvů. Klíčové slovo `using` lze použít, aby se nevyžadovalo úplné jméno, jako v následujícím příkladu:  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 [!code-csharp[csProgGuide#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#25)]  
  
Další informace naleznete v [direktivě using](../../language-reference/keywords/using-directive.md).  
  
Za druhé deklarujete vlastní obory názvů, které vám pomohou řídit obor názvů tříd a metod ve větších programovacích projektech. Použijte klíčové slovo [Namespace](../../language-reference/keywords/namespace.md) k deklarování oboru názvů, jak je uvedeno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideNamespaces#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#6)]

Název oboru názvů musí být platný C# [název identifikátoru](../inside-a-program/identifier-names.md).

## <a name="namespaces-overview"></a>Přehled oborů názvů  

Obory názvů mají následující vlastnosti:  
  
- Organizují velké projekty kódu.  
- Jsou odděleny pomocí operátoru `.`.  
- Direktiva `using` obviates požadavek na zadání názvu oboru názvů pro každou třídu.  
- Obor názvů `global` je kořenovým oborem názvů: `global::System` se vždycky odkazuje na obor názvů .NET <xref:System>.  

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v části [obory názvů](~/_csharplang/spec/namespaces.md) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Použití oboru názvů](using-namespaces.md)
- [Jak používat můj obor názvů](how-to-use-the-my-namespace.md)
- [Názvy identifikátorů](../inside-a-program/identifier-names.md)
- [using – direktiva](../../language-reference/keywords/using-directive.md)
- [:: – operátor](../../language-reference/operators/namespace-alias-qualifier.md)
