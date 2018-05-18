---
title: this (Referenční dokumentace jazyka C#)
description: This – klíčové slovo (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
ms.openlocfilehash: 04496079114be45388926993b67e8f1d3f2e9f15
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
---
# <a name="this-c-reference"></a>this (Referenční dokumentace jazyka C#)
`this` – Klíčové slovo odkazuje na aktuální instanci třídy a také slouží jako modifikátor první parametr metody rozšíření.  
  
> [!NOTE]
>  Tento článek popisuje použití `this` s instancí třídy. Další informace o jeho použití v metody rozšíření najdete v tématu [rozšiřující metody](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).  
  
 Toto jsou běžná použití služby `this`:  
  
-   Aby se dosáhlo nároku členy skryt podobné názvy, například:  
  
 [!code-csharp[csrefKeywordsAccess#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_1.cs)]  
  
-   Chcete-li předat objekt jako parametr jinými metodami, například:  
  
    ```csharp  
    CalcTax(this);  
    ```  
  
-   Chcete-li deklarovat indexery, například:  
  
 [!code-csharp[csrefKeywordsAccess#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_2.cs)]  
  
 Statické členské funkce, protože existují na úrovni třídy a nikoli jako součást objekt, nemají `this` ukazatel. Jedná se o chybu, který bude odkazovat na `this` v statickou metodu.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `this` se použijí pro kvalifikaci `Employee` třídy členy, `name` a `alias`, které jsou podobné názvy skryté. Používá se také předat objekt metodu `CalcTax`, který patří do jiné třídy.  
  
 [!code-csharp[csrefKeywordsAccess#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_3.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [base](../../../csharp/language-reference/keywords/base.md)  
 [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)
