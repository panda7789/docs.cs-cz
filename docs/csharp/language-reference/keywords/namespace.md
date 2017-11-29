---
title: "namespace (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
caps.latest.revision: "28"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 76cc1adc21f6cfadc93da58250336705e43e333a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="namespace-c-reference"></a>namespace (Referenční dokumentace jazyka C#)
`namespace` – Klíčové slovo se používá k deklaraci obor, který obsahuje sadu související objekty. Obor názvů můžete použít k uspořádání elementy kódu a vytvoření typů globálně jedinečný.  
  
 [!code-csharp[csrefKeywordsNamespace#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_1.cs)]  
  
## <a name="remarks"></a>Poznámky  
 V oboru názvů můžou deklarovat minimálně jeden z následujících typů:  
  
-   jiný obor názvů  
  
-   [– Třída](../../../csharp/language-reference/keywords/class.md)  
  
-   [rozhraní](../../../csharp/language-reference/keywords/interface.md)  
  
-   [Struktura](../../../csharp/language-reference/keywords/struct.md)  
  
-   [výčet](../../../csharp/language-reference/keywords/enum.md)  
  
-   [Delegát](../../../csharp/language-reference/keywords/delegate.md)  
  
 Zda je explicitně deklarovat obor názvů ve zdrojovém souboru C#, kompilátor přidá výchozí obor názvů. Tento nepojmenované obor názvů, označovaných také jako globální obor názvů, je v každý soubor. Všechny identifikátor v globálním oboru názvů je k dispozici pro použití v s názvem oboru názvů.  
  
 Obory názvů implicitně mít veřejný přístup a nejedná se upravitelnými. Informace o modifikátory přístupu můžete přiřadit k prvkům v oboru názvů, najdete v části [modifikátory přístupu](../../../csharp/language-reference/keywords/access-modifiers.md).  
  
 Je možné definovat ve dvou nebo více deklarace oboru názvů. Například v následujícím příkladu definuje dvě třídy jako součást `MyCompany` obor názvů:  
  
 [!code-csharp[csrefKeywordsNamespace#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_2.cs)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak volat statickou metodu v vnořené oboru názvů.  
  
 [!code-csharp[csrefKeywordsNamespace#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_3.cs)]  
  
## <a name="for-more-information"></a>Další informace  
 Další informace o použití oboru názvů najdete v následujících tématech:  
  
-   [Obory názvů](../../../csharp/programming-guide/namespaces/index.md)  
  
-   [Použití oboru názvů](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [Postupy: použití aliasu globálního Namespace](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Namespace klíčová slova](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [pomocí](../../../csharp/language-reference/keywords/using.md)
