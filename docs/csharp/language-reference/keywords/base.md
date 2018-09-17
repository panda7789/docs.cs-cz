---
title: Base – klíčové slovo (referenční dokumentace jazyka C#)
description: Další informace o základní klíčové slovo, které se používá pro přístup ke členům základní třídy z odvozené třídy v jazyce C#.
ms.date: 07/20/2015
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
helpviewer_keywords:
- base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
ms.openlocfilehash: 8719ab79273701173530760ad1bec837c4f4302d
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45745994"
---
# <a name="base-c-reference"></a>base (Referenční dokumentace jazyka C#)

`base` – Klíčové slovo se používá pro přístup ke členům základní třídy z odvozené třídy:

- Volejte metodu v základní třídě, který se přepsal jinou metodu.

- Zadejte konstruktoru základní třídy, který by měla být volána při vytváření instance odvozené třídy.

Přístup základní třídy je povolený jenom v konstruktoru, metodu instance nebo přistupující objekt vlastnosti instance.

Jedná se o chybu používat `base` – klíčové slovo z v rámci statické metody.

Základní třída, která se využívají je základní třída zadaná v deklaraci třídy. Pokud zadáte například `class ClassB : ClassA`, jsou přístupné členy ClassA od ClassB, bez ohledu na základní třídu ClassA.

## <a name="example"></a>Příklad

V tomto příkladu i základní třídy, `Person`a odvozená třída `Employee`, měl odpovídající metodu s názvem `Getinfo`. S použitím `base` – klíčové slovo, je možné volat `Getinfo` metodu v základní třídě, v rámci odvozené třídy.

[!code-csharp[csrefKeywordsAccess#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#1)]

Další příklady najdete v tématu [nové](../../../csharp/language-reference/keywords/new.md), [virtuální](../../../csharp/language-reference/keywords/virtual.md), a [přepsat](../../../csharp/language-reference/keywords/override.md).

## <a name="example"></a>Příklad

Tento příklad ukazuje, jak určit konstruktor základní třídy, volá se při vytváření instance odvozené třídy.

[!code-csharp[csrefKeywordsAccess#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#2)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
- [this](../../../csharp/language-reference/keywords/this.md)