---
title: namespace (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
ms.openlocfilehash: 343cce85dd235532fbe3fc90af0a785f48518db7
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245608"
---
# <a name="namespace-c-reference"></a>namespace (Referenční dokumentace jazyka C#)
`namespace` – Klíčové slovo se používá k deklarování oboru, který obsahuje sadu souvisejících objektů. Obor názvů slouží k uspořádání prvků kódu a vytváření globálně jedinečných typů.  
  
 [!code-csharp[csrefKeywordsNamespace#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_1.cs)]  
  
## <a name="remarks"></a>Poznámky  
 V rámci oboru názvů je možné deklarovat jeden nebo více z následujících typů:  
  
-   jiný obor názvů  
  
-   [class](../../../csharp/language-reference/keywords/class.md)  
  
-   [interface](../../../csharp/language-reference/keywords/interface.md)  
  
-   [struct](../../../csharp/language-reference/keywords/struct.md)  
  
-   [enum](../../../csharp/language-reference/keywords/enum.md)  
  
-   [delegate](../../../csharp/language-reference/keywords/delegate.md)  
  
 Zda explicitně deklarovat oboru názvů do zdrojového souboru jazyka C#, kompilátor přidá výchozí obor názvů. Tato nepojmenovaného oboru názvů, někdy označovány jako globální obor názvů, je k dispozici v každém souboru. Žádný identifikátor v globálním oboru názvů je k dispozici pro použití s názvem oboru názvů.  
  
 Obory názvů mají implicitně veřejný přístup, a to není možné upravit. Informace o přístupu modifikátory přístupu můžete přiřadit na prvky v oboru názvů, naleznete v tématu [modifikátory přístupu](../../../csharp/language-reference/keywords/access-modifiers.md).  
  
 Je možné definovat ve dvou nebo více deklarací oboru názvů. Například následující příklad definuje dvě třídy jako součást `MyCompany` obor názvů:  
  
 [!code-csharp[csrefKeywordsNamespace#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_2.cs)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zavolat statickou metodu ve vnořené oboru názvů.  
  
 [!code-csharp[csrefKeywordsNamespace#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_3.cs)]  
  
## <a name="for-more-information"></a>Další informace  
 Další informace o použití oboru názvů naleznete v následujících tématech:  
  
-   [Obory názvů](../../../csharp/programming-guide/namespaces/index.md)  
  
-   [Použití oboru názvů](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [Postupy: Použití aliasu globálního oboru názvů](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Klíčová slova oboru názvů](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [using](../../../csharp/language-reference/keywords/using.md)
