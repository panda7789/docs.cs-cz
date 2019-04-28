---
title: pomocí příkazu - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: df116a200795fd20405381fd71e82d1d6fe662bc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660343"
---
# <a name="using-statement-c-reference"></a>Using – příkaz (C# odkaz)

Poskytuje pohodlné syntaxe, který zajistí správné použití <xref:System.IDisposable> objekty.

## <a name="example"></a>Příklad

Následující příklad ukazuje způsob použití `using` příkazu.

[!code-csharp[csrefKeywordsNamespace#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#4)]

## <a name="remarks"></a>Poznámky

<xref:System.IO.File> a <xref:System.Drawing.Font> jsou příkladem spravované typy, které přístup k nespravovaným prostředkům (v této obslužné rutiny souborů případu a kontexty zařízení). Existuje mnoho dalších typů nespravované prostředky a typy v knihovně tříd, které provádí zapouzdření je. Všechny tyto typy musí implementovat <xref:System.IDisposable> rozhraní.

Když životnosti `IDisposable` objektu je omezen na jedinou metodu, musí deklarovat a vytvoření instance v `using` příkaz. `using` Příkaz volá <xref:System.IDisposable.Dispose%2A> metodu na objekt správným způsobem a (pokud ji používáte jak je uvedeno výše) navíc způsobí, že objekt samotný dostaly mimo obor co nejdříve <xref:System.IDisposable.Dispose%2A> je volána. V rámci `using` blok, objekt je jen pro čtení a nelze upravovat nebo znovu přiřazen.

`using` Příkaz zajistí, že <xref:System.IDisposable.Dispose%2A> se nazývá i v případě, že dojde k výjimce v rámci `using` bloku. Můžete stejného výsledku dosáhnout vložení objektu uvnitř `try` bloku a následným voláním <xref:System.IDisposable.Dispose%2A> v `finally` blokovat; ve skutečnosti je to způsob, jak `using` příkaz je přeložen kompilátorem. Příklad kódu se dříve rozbalí v následujícím kódu v době kompilace (Všimněte si velmi složené závorky do vytvořit omezený obor pro objekt):

[!code-csharp[csrefKeywordsNamespace#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#5)]

Další informace o `try` - `finally` prohlášení, najdete v článku [try-finally](try-finally.md) tématu.

Více instancí typu mohou být deklarovány v `using` příkaz, jak je znázorněno v následujícím příkladu:

[!code-csharp[csrefKeywordsNamespace#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#6)]

Můžete vytvořit instanci objektu prostředků a pak předejte proměnnou `using` příkazu, ale to není nejvhodnější. V takovém případě po ponechá ovládacího prvku `using` blokovat, objekt zůstane v oboru, ale pravděpodobně nemá přístup k jeho nespravovaných prostředků. Jinými slovy je inicializován není plně zobrazovat. Pokud se pokusíte použít objekt mimo `using` blokovat, riziko způsobuje vyvolání výjimky. Z tohoto důvodu je obecně lepší pro vytvoření instance objektu na `using` příkazu a omezit její obor `using` bloku.

[!code-csharp[csrefKeywordsNamespace#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#7)]

Další informace o uvolnění `IDisposable` objekty, najdete [použití objektů implementujících rozhraní IDisposable](../../../standard/garbage-collection/using-objects.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [příkaz using](~/_csharplang/spec/statements.md#the-using-statement) v [ C# specifikace jazyka](../language-specification/index.md). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [using – direktiva](using-directive.md)
- [Uvolňování paměti](../../../standard/garbage-collection/index.md)
- [Použití objektů implementujících rozhraní IDisposable](../../../standard/garbage-collection/using-objects.md)
- [Rozhraní IDisposable](xref:System.IDisposable)