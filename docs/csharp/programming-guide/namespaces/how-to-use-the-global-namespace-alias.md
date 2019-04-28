---
title: 'Postupy: Použití aliasu globálního Namespace - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- aliases [C#]
- namespaces [C#], global namespace qualifier
- global namespace [C#]
ms.assetid: 98a1d89b-3c5a-44f7-8400-c4a3c0ec22a9
ms.openlocfilehash: 268d40e8d6eb5f5f2a82a5ce3a3346179c886c14
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61710339"
---
# <a name="how-to-use-the-global-namespace-alias-c-programming-guide"></a>Postupy: Použití aliasu globálního Namespace (C# Průvodce programováním v)
Umožňuje přístup ke členu v globální [obor názvů](../../../csharp/language-reference/keywords/namespace.md) je užitečné, když člen může být skryty pomocí jiné entity se stejným názvem.  
  
 Například v následujícím kódu `Console` přeloží na `TestApp.Console` místo na `Console` zadejte <xref:System> oboru názvů.  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 [!code-csharp[csProgGuideNamespaces#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#1)]  
  
 Pomocí `System.Console` stále dojde k chybě, protože `System` obor názvů je skrytý třídou `TestApp.System`:  
  
 [!code-csharp[csProgGuideNamespaces#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#2)]  
  
 Nicméně, můžete alternativně vyřešit tuto chybu pomocí `global::System.Console`, tímto způsobem:  
  
 [!code-csharp[csProgGuideNamespaces#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#3)]  
  
 Pokud je identifikátor levé `global`, vyhledejte správný identifikátor začíná v globálním oboru názvů. Například následující deklaraci odkazuje `TestApp` jako člen globálním prostoru.  
  
 [!code-csharp[csProgGuideNamespaces#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#4)]  
  
 Samozřejmě, vytvářet své vlastní obory názvů volá `System` se nedoporučuje, a nepravděpodobné, narazíte na jakýkoli kód, ve kterém se to stalo. U větších projektů, je však velmi skutečné možnost, duplikace oboru názvů může vyskytovat ve formuláři nebo jiném. Kvalifikátor globálního oboru názvů v těchto situacích je vaše záruku, že můžete určit kořenový obor názvů.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu, obor názvů `System` je použít k zahrnutí třídy `TestClass` proto `global::System.Console` musí být použita na odkaz `System.Console` třídu, která je skrytý `System` oboru názvů. Také, že alias `colAlias` se používá k odkazování na obor názvů `System.Collections`; proto instanci <xref:System.Collections.Hashtable?displayProperty=nameWithType> byl vytvořen pomocí tento alias místo obor názvů.  
  
 [!code-csharp[csProgGuideNamespaces#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#5)]  
  
**A 1**
**B 2**
**C 3**

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Obory názvů](../../../csharp/programming-guide/namespaces/index.md)
- [. – operátor](../../../csharp/language-reference/operators/member-access-operator.md)
- [:: – operátor](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)
- [extern](../../../csharp/language-reference/keywords/extern.md)
