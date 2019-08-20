---
title: základní klíčové slovo C# – referenční informace
ms.custom: seodec18
description: Přečtěte si základní klíčové slovo, které se používá pro přístup ke členům základní třídy v rámci odvozené třídy v C#.
ms.date: 07/20/2015
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
helpviewer_keywords:
- base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
ms.openlocfilehash: b882a8d1e5979ac184d184be379dd76f7bf3600f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602255"
---
# <a name="base-c-reference"></a>base (Referenční dokumentace jazyka C#)

`base` Klíčové slovo se používá pro přístup ke členům základní třídy v rámci odvozené třídy:

- Volejte metodu pro základní třídu, která byla přepsána jinou metodou.

- Určuje, který konstruktor základní třídy by měl být volán při vytváření instancí odvozené třídy.

Přístup ke základní třídě je povolený jenom v konstruktoru, metodě instance nebo přistupujícím objektu vlastnosti instance.

Použití `base` klíčového slova v rámci statické metody je chybné.

Základní třída, která je k dispozici, je základní třída zadaná v deklaraci třídy. Například pokud zadáte `class ClassB : ClassA`, budou k členům třídy Class přicházet z ClassB bez ohledu na základní třídu třídy.

## <a name="example"></a>Příklad

V tomto příkladu mají základní třídu, `Person`i odvozenou `Employee`třídu metodu s názvem `Getinfo`. Pomocí `base` klíčového slova je možné `Getinfo` volat metodu pro základní třídu z odvozené třídy.

[!code-csharp[csrefKeywordsAccess#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#1)]

Další příklady naleznete v tématu [New](new-modifier.md), [Virtual](virtual.md)a [override](override.md).

## <a name="example"></a>Příklad

Tento příklad ukazuje, jak určit konstruktor základní třídy nazvaný při vytváření instancí odvozené třídy.

[!code-csharp[csrefKeywordsAccess#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#2)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](./index.md)
- [this](./this.md)
