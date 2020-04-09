---
title: using statement - C# Reference using statement - C# Reference using statement - C# Reference using statement
ms.date: 04/07/2020
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: a237a90b4782e0460857c3d5d887771bcc8ccaaf
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989178"
---
# <a name="using-statement-c-reference"></a>using příkaz (C# Reference)

Poskytuje pohodlnou syntaxi, která <xref:System.IDisposable> zajišťuje správné použití objektů. Počínaje C# `using` 8.0, příkaz zajišťuje správné <xref:System.IAsyncDisposable> použití objektů.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak `using` použít příkaz.

:::code language="csharp" source="snippets/usings.cs" id="SnippetFirstExample":::

Počínaje C# 8.0, můžete použít následující alternativní `using` syntaxe pro příkaz, který nevyžaduje závorky:

:::code language="csharp" source="snippets/usings.cs" id="SnippetModernUsing":::

## <a name="remarks"></a>Poznámky

<xref:System.IO.File>a <xref:System.Drawing.Font> jsou příklady spravovaných typů, které přistupují k nespravovaným prostředkům (v tomto případě popisovače souborů a kontexty zařízení). Existuje mnoho dalších druhů nespravovaných prostředků a typů knihovny tříd, které je zapouzdřují. Všechny tyto typy <xref:System.IDisposable> musí implementovat <xref:System.IAsyncDisposable> rozhraní nebo rozhraní.

Pokud je životnost `IDisposable` objektu omezena na jednu metodu, měli byste `using` deklarovat a konkretizovat v příkazu. Příkaz `using` volá <xref:System.IDisposable.Dispose%2A> metodu na objekt správným způsobem a (při použití, jak je uvedeno výše) také způsobí, <xref:System.IDisposable.Dispose%2A> že samotný objekt přejít mimo rozsah, jakmile je volána. V `using` rámci bloku je objekt jen pro čtení a nelze jej změnit ani znovu přiřadit. `IAsyncDisposable` Pokud objekt implementuje `IDisposable`místo `using` , <xref:System.IAsyncDisposable.DisposeAsync%2A> příkaz `awaits` volá <xref:System.Threading.Tasks.Task>a vrácené .

Příkaz `using` zajišťuje, <xref:System.IDisposable.Dispose%2A> že <xref:System.IAsyncDisposable.DisposeAsync%2A>(nebo ) je volána i `using` v případě, že dojde k výjimce v rámci bloku. Můžete dosáhnout stejného výsledku vložením `try` objektu <xref:System.IDisposable.Dispose%2A> do <xref:System.IAsyncDisposable.DisposeAsync%2A> bloku `finally` a pak volání (nebo `using` v bloku; ve skutečnosti je to, jak je příkaz přeložen kompilátorem. Příklad kódu dříve rozbalí na následující kód v době kompilace (všimněte si extra složené závorky k vytvoření omezeného oboru pro objekt):

:::code language="csharp" source="snippets/usings.cs" id="SnippetTryFinallyExample":::

Syntaxe `using` novějšího příkazu se překládá na podobný kód. Blok `try` se otevře tam, kde je proměnná deklarována. Blok `finally` je přidán na konci ohraničující blok, obvykle na konci metody.

Další informace o `try` - `finally` příkazu naleznete v článku [try-finally.](try-finally.md)

Více instancí typu lze deklarovat v jednom `using` příkazu, jak je znázorněno v následujícím příkladu. Všimněte si, že nelze použít implicitně`var`zadané proměnné ( ) při deklarování více proměnných v jednom příkazu:

:::code language="csharp" source="snippets/usings.cs" id="SnippetDeclareMultipleVariables":::

Můžete kombinovat více deklarací stejného typu pomocí nové syntaxe zavedené s C# 8 také, jak je znázorněno v následujícím příkladu:

:::code language="csharp" source="snippets/usings.cs" id="SnippetModernMultipleVariables":::

Můžete vytvořit instanci objektu prostředku a pak `using` předat proměnnou příkazu, ale to není osvědčený postup. V tomto případě po `using` ovládací prvek opustí blok, objekt zůstane v oboru, ale pravděpodobně nemá přístup k jeho nespravované prostředky. Jinými slovy, už to není úplně inicializováno. Pokud se pokusíte použít `using` objekt mimo blok, riskujete, že dojde k vyvolání výjimky. Z tohoto důvodu je lepší vytvořit instanci objektu v příkazu `using` `using` a omezit jeho rozsah na blok.

:::code language="csharp" source="snippets/usings.cs" id="SnippetDeclareBeforeUsing":::

Další informace o likvidaci `IDisposable` objektů naleznete v tématu [Použití objektů, které implementují IDisposable](../../../standard/garbage-collection/using-objects.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

For more information, see [The using statement](~/_csharplang/spec/statements.md#the-using-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](index.md)
- [using – direktiva](using-directive.md)
- [Uvolněné](../../../standard/garbage-collection/index.md)
- [Použití objektů, které implementují IDisposable](../../../standard/garbage-collection/using-objects.md)
- [IJednorázové rozhraní](xref:System.IDisposable)
- [using statement in C# 8.0](~/_csharplang/proposals/csharp-8.0/using.md)
