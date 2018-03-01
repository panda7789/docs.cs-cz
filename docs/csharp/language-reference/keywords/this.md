---
title: "this (Referenční dokumentace jazyka C#)"
description: "This – klíčové slovo (referenční dokumentace jazyka C#)"
keywords: "Tato (C#), toto klíčové slovo (C#), toto klíčové slovo (C# odkaz), toto klíčové slovo (C# referenční dokumentace jazyka)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f159967707061481a34e72a97ec8cc8316d982ca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="this-c-reference"></a>this (Referenční dokumentace jazyka C#)
`this` – Klíčové slovo odkazuje na aktuální instanci třídy a také slouží jako modifikátor první parametr metody rozšíření.  
  
> [!NOTE]
>  Tento článek popisuje použití `this` s instancí třídy. Další informace o jeho použití v metody rozšíření najdete v tématu [rozšiřující metody](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).  
  
 Toto jsou běžná použití služby `this`:  
  
-   Aby se dosáhlo nároku členy skryt podobné názvy, například:  
  
 [!code-csharp[csrefKeywordsAccess#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_1.cs)]  
  
-   Chcete-li předat objekt jako parametr jinými metodami, například:  
  
    ```  
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
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [základní](../../../csharp/language-reference/keywords/base.md)  
 [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)
