---
title: base (Referenční dokumentace jazyka C#)
description: Další informace o základní klíčové slovo, který se používá pro přístup k členy základní třídy z v odvozené třídě v jazyce C#.
ms.date: 07/20/2015
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
helpviewer_keywords:
- base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
ms.openlocfilehash: 69885ba0b2d05c79f2b7ba9458e7ba8c8b7aa0c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="base-c-reference"></a>base (Referenční dokumentace jazyka C#)

`base` – Klíčové slovo se používá pro přístup členy základní třídy z v odvozené třídě:

- Volání metody na základní třídy, který se přepsal jinou metodou.

- Zadejte, které konstruktor základní třídy by měla být volána při vytváření instance odvozené třídy.

Pro přístup k základní třída je povoleno pouze v konstruktor, metody instance nebo přistupující objekt vlastnosti instance.

Jedná se o chybu používat `base` – klíčové slovo z v rámci statickou metodu.

Základní třídy, které je přístupné je základní třídy zadaný v deklaraci třídy. Pokud zadáte například `class ClassB : ClassA`, členové ClassA jsou k němu přistupovat z ClassB, bez ohledu na základní třídu ClassA.

## <a name="example"></a>Příklad
V tomto příkladu i základní třídy, `Person`a odvozené třídy, `Employee`, obsahovat metodu s názvem `Getinfo`. Pomocí `base` – klíčové slovo, je možné volat `Getinfo` metodu základní třídy, v rámci odvozené třídy.

[!code-csharp[csrefKeywordsAccess#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_1.cs)]

Další příklady najdete v tématu [nové](../../../csharp/language-reference/keywords/new.md), [virtuální](../../../csharp/language-reference/keywords/virtual.md), a [přepsat](../../../csharp/language-reference/keywords/override.md).

## <a name="example"></a>Příklad
Tento příklad ukazuje, jak určit volána při vytváření instance odvozené třídy základní třídy konstruktoru.

[!code-csharp[csrefKeywordsAccess#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_2.cs)]

## <a name="c-language-specification"></a>specifikace jazyka C#
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [this](../../../csharp/language-reference/keywords/this.md)