---
title: this (Referenční dokumentace jazyka C#)
description: Toto klíčové slovo (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
ms.openlocfilehash: df1bf6a3e6d24b231bf5e3c7a960f49084c4e53a
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2018
ms.locfileid: "46485821"
---
# <a name="this-c-reference"></a>this (Referenční dokumentace jazyka C#)
`this` – Klíčové slovo odkazuje na aktuální instanci třídy a slouží také jako modifikátor první parametr metody rozšíření.  
  
> [!NOTE]
>  Tento článek popisuje způsob používání `this` instancemi třídy. Další informace o jeho použití v metodách rozšíření naleznete v tématu [rozšiřující metody](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).  
  
 Tady jsou běžné způsoby použití `this`:  
  
-   K získání způsobilosti členy skryta podobnými názvy, například:  
  
 [!code-csharp[csrefKeywordsAccess#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_1.cs)]  
  
-   K předání objektu jako parametr do jiné metody, například:  
  
    ```csharp  
    CalcTax(this);  
    ```  
  
-   Chcete-li deklarovat indexery, například:  
  
 [!code-csharp[csrefKeywordsAccess#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_2.cs)]  
  
 Statické členské funkce, protože existují na úrovni třídy, nikoli jako součást objektu, není nutné `this` ukazatele. Jedná se o chybu k odkazování na `this` uvnitř statické metody.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `this` se použijí pro kvalifikaci `Employee` členy, třídy `name` a `alias`, které jsou skryté, podobně jako názvy. Používá se také k objektu předat metodě `CalcTax`, který patří do jiné třídy.  
  
 [!code-csharp[csrefKeywordsAccess#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_3.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
- [base](../../../csharp/language-reference/keywords/base.md)  
- [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)
