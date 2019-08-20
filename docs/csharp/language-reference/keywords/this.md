---
title: Toto klíčové slovo C# – referenční informace
ms.custom: seodec18
description: Toto klíčové slovoC# (referenční)
ms.date: 07/20/2015
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
ms.openlocfilehash: 4a3342e73fef3effd54f72e68283eb6085eef5b5
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608446"
---
# <a name="this-c-reference"></a>this (Referenční dokumentace jazyka C#)

`this` Klíčové slovo odkazuje na aktuální instanci třídy a používá se také jako modifikátor prvního parametru metody rozšíření.

> [!NOTE]
> Tento článek popisuje použití `this` s instancemi třídy. Další informace o jeho použití v rozšiřujících metodách naleznete v tématu [metody rozšíření](../../programming-guide/classes-and-structs/extension-methods.md).

Zde jsou běžně používané `this`nástroje:

- Chcete-li kvalifikovat členy skryté podobným názvem, například:

  [!code-csharp[csrefKeywordsAccess#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#4)]  

- Pro předání objektu jako parametru jiným metodám, například:

  ```csharp
  CalcTax(this);
  ```

- Chcete-li deklarovat indexery, například:

  [!code-csharp[csrefKeywordsAccess#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#5)]

Statické členské funkce, protože existují na úrovni třídy a ne jako součást objektu, `this` nemají ukazatel. V případě, že se odkazuje na `this` statickou metodu, se jedná o chybu.

## <a name="example"></a>Příklad

V tomto příkladu `this` se používá k `Employee` kvalifikování členů třídy, `name` a `alias`, které jsou skryté podobnými názvy. Slouží také k předání objektu do metody `CalcTax`, která patří do jiné třídy.

[!code-csharp[csrefKeywordsAccess#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#3)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [base](base.md)
- [Metody](../../programming-guide/classes-and-structs/methods.md)
