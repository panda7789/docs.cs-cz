---
title: toto klíčové slovo – odkaz jazyka C#
description: toto klíčové slovo (Odkaz jazyka C#
ms.date: 07/20/2015
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
ms.openlocfilehash: 2a2c487ad93e6fc75ecf95c541e859b8b60bb5b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715109"
---
# <a name="this-c-reference"></a>this (Referenční dokumentace jazyka C#)

Klíčové `this` slovo odkazuje na aktuální instanci třídy a je také použit jako modifikátor prvníparametr metody rozšíření.

> [!NOTE]
> Tento článek popisuje použití `this` s instancemi třídy. Další informace o jeho použití v rozšiřujících metodách naleznete v [tématu Metody rozšíření](../../programming-guide/classes-and-structs/extension-methods.md).

Toto jsou běžná použití `this`:

- Chcete-li kvalifikovat členy skryté pod podobnými názvy, například:

  [!code-csharp[csrefKeywordsAccess#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#4)]  

- Chcete-li předat objekt jako parametr jiným metodám, například:

  ```csharp
  CalcTax(this);
  ```

- Deklarovat indexery, například:

  [!code-csharp[csrefKeywordsAccess#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#5)]

Statické členské funkce, protože existují na úrovni třídy a nikoli jako `this` součást objektu, nemají ukazatel. Je chyba odkazovat `this` se na ve statické metodě.

## <a name="example"></a>Příklad

V tomto `this` příkladu se `Employee` používá ke `name` `alias`kvalifikaci členy třídy a , které jsou skryté pod podobnými názvy. Používá se také k předání objektu metodě `CalcTax`, která patří do jiné třídy.

[!code-csharp[csrefKeywordsAccess#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#3)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](index.md)
- [base](base.md)
- [Metody](../../programming-guide/classes-and-structs/methods.md)
