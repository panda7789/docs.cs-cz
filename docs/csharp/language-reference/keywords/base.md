---
title: základní klíčové slovo C# – referenční informace
description: Přečtěte si základní klíčové slovo, které se používá pro přístup ke členům základní třídy v rámci odvozené třídy v C#.
ms.date: 07/20/2015
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
helpviewer_keywords:
- base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
ms.openlocfilehash: a4686fc5d4245a50de5d77dc0e71c231772f40ef
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713770"
---
# <a name="base-c-reference"></a>base (Referenční dokumentace jazyka C#)

Klíčové slovo `base` se používá pro přístup ke členům základní třídy v rámci odvozené třídy:

- Volejte metodu pro základní třídu, která byla přepsána jinou metodou.

- Určuje, který konstruktor základní třídy by měl být volán při vytváření instancí odvozené třídy.

Přístup ke základní třídě je povolený jenom v konstruktoru, metodě instance nebo přistupujícím objektu vlastnosti instance.

Použití klíčového slova `base` v rámci statické metody je chybné.

Základní třída, která je k dispozici, je základní třída zadaná v deklaraci třídy. Například pokud zadáte `class ClassB : ClassA`, jsou k členům třídy Class přistup z ClassB bez ohledu na základní třídu třídy.

## <a name="example"></a>Příklad

V tomto příkladu má základní třída, `Person`a odvozená třída `Employee`, metodu s názvem `Getinfo`. Pomocí klíčového slova `base` lze volat metodu `Getinfo` v základní třídě z odvozené třídy.

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
