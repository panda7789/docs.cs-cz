---
title: "Postupy: Použití aliasu globálního oboru názvů (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- aliases [C#]
- namespaces [C#], global namespace qualifier
- global namespace [C#]
ms.assetid: 98a1d89b-3c5a-44f7-8400-c4a3c0ec22a9
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f2a854d2f963578cb8b89da445af660f3c029fae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-global-namespace-alias-c-programming-guide"></a>Postupy: Použití aliasu globálního oboru názvů (Průvodce programováním v C#)
Umožňuje přístup ke členu v globální [obor názvů](../../../csharp/language-reference/keywords/namespace.md) je užitečné, když se člen může být skrytý na základě jiné entity se stejným názvem.  
  
 Například v následujícím kódu `Console` přeloží na `TestApp.Console` místo na `Console` zadejte <xref:System> oboru názvů.  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-use-the-global-namespace-alias_1.cs)]  
  
 [!code-csharp[csProgGuideNamespaces#1](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_2.cs)]  
  
 Pomocí `System.Console` stále dojde k chybě, protože `System` obor názvů je skrytý na základě třídy `TestApp.System`:  
  
 [!code-csharp[csProgGuideNamespaces#2](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_3.cs)]  
  
 Nicméně, můžete tuto chybu vyřešit pomocí `global::System.Console`, podobné výjimky:  
  
 [!code-csharp[csProgGuideNamespaces#3](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_4.cs)]  
  
 Pokud je identifikátor levém `global`, spustí vyhledávání pro identifikátor vpravo v globálním oboru názvů. Například následující prohlášení odkazuje `TestApp` jako člen globálního místa.  
  
 [!code-csharp[csProgGuideNamespaces#4](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_5.cs)]  
  
 Vytvoření vlastní obory názvů samozřejmě nazývané `System` se nedoporučuje, a pravděpodobně narazíte na kód, ve kterém byla odepřena. V projektech větší, je však velmi reálná možnost, že duplikace oboru názvů, může dojít v jednoho formuláře nebo jiné. V těchto situacích kvalifikátor globálního oboru názvů je vaše záruku, že je možné zadat kořenového oboru názvů.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu, obor názvů `System` se používá k obsahují třídu `TestClass` proto `global::System.Console` se musí použít k odkazu `System.Console` třídy, která je skrytý na základě `System` oboru názvů. Navíc alias `colAlias` slouží k odkazování na obor názvů `System.Collections`; proto instanci <xref:System.Collections.Hashtable?displayProperty=nameWithType> byla vytvořena pomocí tento alias místo obor názvů.  
  
 [!code-csharp[csProgGuideNamespaces#5](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_6.cs)]  
  
 **1**  
**B 2**  
**C 3**   
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Obory názvů](../../../csharp/programming-guide/namespaces/index.md)  
 [. Operátor](../../../csharp/language-reference/operators/member-access-operator.md)  
 [:: – Operátor](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [extern](../../../csharp/language-reference/keywords/extern.md)
