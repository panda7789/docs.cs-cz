---
title: using statement - C# Reference using statement - C# Reference using statement - C# Reference using statement
ms.date: 10/15/2019
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: 52cde99fd029ce50f159b2a87fbfbf47fc79dccc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712959"
---
# <a name="using-statement-c-reference"></a>using příkaz (C# Reference)

Poskytuje pohodlnou syntaxi, která <xref:System.IDisposable> zajišťuje správné použití objektů.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak `using` použít příkaz.

[!code-csharp[csrefKeywordsNamespace#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#4)]

Počínaje C# 8.0, můžete použít následující alternativní `using` syntaxe pro příkaz, který nevyžaduje závorky:

[!code-csharp[csrefKeywordsNamespace#New](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#ModernUsing)]

## <a name="remarks"></a>Poznámky

<xref:System.IO.File>a <xref:System.Drawing.Font> jsou příklady spravovaných typů, které přistupují k nespravovaným prostředkům (v tomto případě popisovače souborů a kontexty zařízení). Existuje mnoho dalších druhů nespravovaných prostředků a typů knihovny tříd, které je zapouzdřují. Všechny tyto typy <xref:System.IDisposable> musí implementovat rozhraní.

Pokud je životnost `IDisposable` objektu omezena na jednu metodu, měli byste `using` deklarovat a konkretizovat v příkazu. Příkaz `using` volá <xref:System.IDisposable.Dispose%2A> metodu na objekt správným způsobem a (při použití, jak je uvedeno výše) také způsobí, <xref:System.IDisposable.Dispose%2A> že samotný objekt přejít mimo rozsah, jakmile je volána. V `using` rámci bloku je objekt jen pro čtení a nelze jej změnit ani znovu přiřadit.

Příkaz `using` zajišťuje, <xref:System.IDisposable.Dispose%2A> že je volána i v `using` případě, že dojde k výjimce v rámci bloku. Můžete dosáhnout stejného výsledku vložením `try` objektu <xref:System.IDisposable.Dispose%2A> do `finally` bloku a následným voláním bloku; ve skutečnosti je to, jak je `using` příkaz přeložen kompilátorem. Příklad kódu dříve rozbalí na následující kód v době kompilace (všimněte si extra složené závorky k vytvoření omezeného oboru pro objekt):

[!code-csharp[csrefKeywordsNamespace#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#5)]

Syntaxe `using` novějšího příkazu se překládá na velmi podobný kód. Blok `try` se otevře tam, kde je proměnná deklarována. Blok `finally` je přidán na konci ohraničující blok, obvykle na konci metody.

Další informace o `try` - `finally` příkazu naleznete v tématu [try-finally.](try-finally.md)

Více instancí typu lze deklarovat v příkazu, `using` jak je znázorněno v následujícím příkladu:

[!code-csharp[csrefKeywordsNamespace#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#6)]

Můžete kombinovat více deklarací stejného typu pomocí nové syntaxe zavedené s C# 8 také. To je znázorněno v následujícím příkladu:

[!code-csharp[csrefKeywordsNamespace#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#MultipleUsing)]

Můžete vytvořit instanci objektu prostředku a potom `using` předat proměnnou příkazu, ale to není osvědčený postup. V tomto případě po `using` ovládací prvek opustí blok, objekt zůstane v oboru, ale pravděpodobně nemá přístup k jeho nespravované prostředky. Jinými slovy, už to není úplně inicializováno. Pokud se pokusíte použít `using` objekt mimo blok, riskujete, že dojde k vyvolání výjimky. Z tohoto důvodu je obecně lepší vytvořit instanci `using` objektu v příkazu `using` a omezit jeho rozsah na blok.

[!code-csharp[csrefKeywordsNamespace#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#7)]

Další informace o likvidaci `IDisposable` objektů naleznete v tématu [Použití objektů, které implementují IDisposable](../../../standard/garbage-collection/using-objects.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

For more information, see [The using statement](~/_csharplang/spec/statements.md#the-using-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](index.md)
- [using – direktiva](using-directive.md)
- [Kolekce paměti](../../../standard/garbage-collection/index.md)
- [Použití objektů, které implementují IDisposable](../../../standard/garbage-collection/using-objects.md)
- [IJednorázové rozhraní](xref:System.IDisposable)
- [using statement in C# 8.0](~/_csharplang/proposals/csharp-8.0/using.md)
