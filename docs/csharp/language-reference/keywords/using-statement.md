---
title: using – reference jazyka C#
ms.date: 05/29/2020
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: b889d2fcbdf854dbe8948744810f9b74e9f0dac2
ms.sourcegitcommit: 5280b2aef60a1ed99002dba44e4b9e7f6c830604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/03/2020
ms.locfileid: "84307043"
---
# <a name="using-statement-c-reference"></a>using – příkaz (Referenční dokumentace jazyka C#)

Poskytuje pohodlný syntax, který zajišťuje správné použití <xref:System.IDisposable> objektů. Počínaje jazykem C# 8,0 `using` příkaz zajišťuje správné použití <xref:System.IAsyncDisposable> objektů.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít `using` příkaz.

:::code language="csharp" source="snippets/usings.cs" id="SnippetFirstExample":::

Počínaje jazykem C# 8,0 můžete použít následující alternativní syntaxi pro `using` příkaz, který nevyžaduje složené závorky:

:::code language="csharp" source="snippets/usings.cs" id="SnippetModernUsing":::

## <a name="remarks"></a>Poznámky

<xref:System.IO.File>a <xref:System.Drawing.Font> jsou příklady spravovaných typů, které přistupují k nespravovaným prostředkům (v tomto případě popisovače souborů a kontexty zařízení). Existuje mnoho dalších druhů nespravovaných prostředků a typů knihoven tříd, které je zapouzdřují. Všechny tyto typy musí implementovat <xref:System.IDisposable> rozhraní nebo <xref:System.IAsyncDisposable> rozhraní.

Pokud `IDisposable` je životnost objektu omezena na jedinou metodu, měli byste deklarovat a vytvořit jeho instanci v `using` příkazu. `using`Příkaz volá <xref:System.IDisposable.Dispose%2A> metodu na objekt správným způsobem a (při použití, jak je uvedeno výše), také způsobí, že se objekt sám vrátí do rozsahu, jakmile <xref:System.IDisposable.Dispose%2A> je volán. V rámci `using` bloku je objekt jen pro čtení a nedá se změnit ani znovu přiřadit. Pokud objekt implementuje `IAsyncDisposable` místo `IDisposable` , `using` příkaz zavolá <xref:System.IAsyncDisposable.DisposeAsync%2A> a `awaits` vrátí <xref:System.Threading.Tasks.ValueTask> . Další informace o naleznete v <xref:System.IAsyncDisposable> tématu [Implementing a DisposeAsync Method](../../../standard/garbage-collection/implementing-disposeasync.md).

`using`Příkaz zajistí, že <xref:System.IDisposable.Dispose%2A> (nebo <xref:System.IAsyncDisposable.DisposeAsync%2A> ) je volána i v případě, že v rámci bloku dojde k výjimce `using` . Stejný výsledek lze dosáhnout vložením objektu do `try` bloku a následným voláním <xref:System.IDisposable.Dispose%2A> (nebo <xref:System.IAsyncDisposable.DisposeAsync%2A> ) v `finally` bloku. to je způsob, jakým `using` je příkaz přeložen kompilátorem. Výše uvedený příklad kódu se v době kompilace rozšíří na následující kód (Poznamenejte si nadbytečné složené závorky pro vytvoření omezeného oboru pro objekt):

:::code language="csharp" source="snippets/usings.cs" id="SnippetTryFinallyExample":::

Novější `using` syntaxe příkazu se překládá na podobný kód. `try`Blok se otevře, kde je proměnná deklarována. `finally`Blok se přidá na konec ohraničujícího bloku, obvykle na konci metody.

Další informace o `try` - `finally` příkazu naleznete v článku [try-finally](try-finally.md) .

V jednom příkazu lze deklarovat více instancí typu `using` , jak je znázorněno v následujícím příkladu. Všimněte si, že nemůžete použít implicitní typové proměnné ( `var` ), pokud deklarujete více proměnných v jednom příkazu:

:::code language="csharp" source="snippets/usings.cs" id="SnippetDeclareMultipleVariables":::

Můžete zkombinovat více deklarací stejného typu pomocí nové syntaxe představené v jazyce C# 8, jak je znázorněno v následujícím příkladu:

:::code language="csharp" source="snippets/usings.cs" id="SnippetModernMultipleVariables":::

Můžete vytvořit instanci objektu prostředku a pak předat proměnnou `using` příkazu, ale to není doporučený postup. V takovém případě, když ovládací prvek opustí `using` blok, objekt zůstane v oboru, ale pravděpodobně nemá přístup k nespravovaným prostředkům. Jinými slovy, již není zcela inicializován. Pokud se pokusíte použít objekt mimo `using` blok, riskujete, že bude vyvolána výjimka. Z tohoto důvodu je lepší vytvořit instanci objektu v `using` příkazu a omezit svůj rozsah na `using` blok.

:::code language="csharp" source="snippets/usings.cs" id="SnippetDeclareBeforeUsing":::

Další informace o odstraňování `IDisposable` objektů najdete v tématu [použití objektů, které implementují IDisposable](../../../standard/garbage-collection/using-objects.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete ve [specifikaci jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction)v [příkazu Using](~/_csharplang/spec/statements.md#the-using-statement) . Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [using – direktiva](using-directive.md)
- [Uvolňování paměti](../../../standard/garbage-collection/index.md)
- [Použití objektů, které implementují IDisposable](../../../standard/garbage-collection/using-objects.md)
- [Rozhraní IDisposable](xref:System.IDisposable)
- [using – příkaz v C# 8,0](~/_csharplang/proposals/csharp-8.0/using.md)
