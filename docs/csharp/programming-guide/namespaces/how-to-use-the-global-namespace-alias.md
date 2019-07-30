---
title: 'Postupy: Použít globální průvodce C# programováním aliasu oboru názvů'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- aliases [C#]
- namespaces [C#], global namespace qualifier
- global namespace [C#]
ms.assetid: 98a1d89b-3c5a-44f7-8400-c4a3c0ec22a9
ms.openlocfilehash: f44bb1f010f154973fc6982882c9b5a09528da76
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629441"
---
# <a name="how-to-use-the-global-namespace-alias-c-programming-guide"></a>Postupy: Použití aliasu globálního oboru názvůC# (Průvodce programováním)
Možnost přístupu ke členu v globálním [oboru názvů](../../../csharp/language-reference/keywords/namespace.md) je užitečná v případě, že člen může být skrytý jinou entitou se stejným názvem.  
  
 Například v `Console` následujícím kódu se přeloží na `TestApp.Console` místo <xref:System> na `Console` typ v oboru názvů.  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 [!code-csharp[csProgGuideNamespaces#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#1)]  
  
 Použití `System.Console` stále způsobí chybu, `System` protože obor názvů je skrytý třídou `TestApp.System`:  
  
 [!code-csharp[csProgGuideNamespaces#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#2)]  
  
 Tuto chybu však můžete obejít pomocí `global::System.Console`, například takto:  
  
 [!code-csharp[csProgGuideNamespaces#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#3)]  
  
 Když je `global`levý identifikátor, hledání správného identifikátoru začíná na globálním oboru názvů. Například následující deklarace je odkazována `TestApp` jako člen globálního prostoru.  
  
 [!code-csharp[csProgGuideNamespaces#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#4)]  
  
 Nedoporučujeme vytvářet vlastní obory `System` názvů nazvané a je nepravděpodobné, že narazíte na kód, ve kterém k tomu došlo. Ve větších projektech je však velmi reálnou možností, že k duplikaci oboru názvů může dojít v jednom nebo jiném formuláři. V těchto situacích je kvalifikátor globálního oboru názvů vaší zárukou, že můžete zadat kořenový obor názvů.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu je použit obor `System` názvů pro zahrnutí třídy `TestClass` , `global::System.Console` a musí být použit k odkazování `System` na `System.Console` třídu, která je skryta oborem názvů. Alias `colAlias` se také používá pro odkazování na obor názvů `System.Collections`; proto instance <xref:System.Collections.Hashtable?displayProperty=nameWithType> byla vytvořena pomocí tohoto aliasu namísto oboru názvů.  
  
 [!code-csharp[csProgGuideNamespaces#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#5)]  
  
**A 1**
**B 2**
**C 3**

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Obory názvů](../../../csharp/programming-guide/namespaces/index.md)
- [:: – operátor](../../../csharp/language-reference/operators/namespace-alias-qualifier.md)
- [extern](../../../csharp/language-reference/keywords/extern.md)
