---
title: základní klíčové slovo - C# Reference
description: Informace o základní klíčové slovo, které se používá pro přístup k členům základní třídy z v rámci odvozené třídy v C#.
ms.date: 07/20/2015
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
helpviewer_keywords:
- base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
ms.openlocfilehash: a4686fc5d4245a50de5d77dc0e71c231772f40ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713770"
---
# <a name="base-c-reference"></a>base (Referenční dokumentace jazyka C#)

Klíčové `base` slovo se používá pro přístup k členům základní třídy z odvozené třídy:

- Volání metody na základní třídy, která byla přepsána jinou metodou.

- Určete, který konstruktor základní třídy by měl být volán při vytváření instancí odvozené třídy.

Přístup základní třídy je povolen pouze v konstruktoru, metodě instance nebo přistupujícím objektu vlastnosti instance.

Je chyba použít `base` klíčové slovo z v rámci statické metody.

Základní třída, která je přístupná, je základní třída zadaná v deklaraci třídy. Například pokud zadáte `class ClassB : ClassA`, členy ClassA jsou přístupné z ClassB, bez ohledu na základní třídy ClassA.

## <a name="example"></a>Příklad

V tomto příkladu mají `Person`základní třída a odvozená třída `Employee`, `Getinfo`metodu s názvem . Pomocí klíčového `base` slova je možné `Getinfo` volat metodu na základní třídy, z v rámci odvozené třídy.

[!code-csharp[csrefKeywordsAccess#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#1)]

Další příklady naleznete [v tématu new](new-modifier.md), [virtual](virtual.md)a [override](override.md).

## <a name="example"></a>Příklad

Tento příklad ukazuje, jak určit konstruktor základní třídy volaný při vytváření instancí odvozené třídy.

[!code-csharp[csrefKeywordsAccess#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#2)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](./index.md)
- [tohoto provozu](./this.md)
