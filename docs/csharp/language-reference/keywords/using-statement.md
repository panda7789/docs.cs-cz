---
title: použití odkazu na C# příkaz
ms.custom: seodec18
ms.date: 10/15/2019
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: 7e6d1b663007d430f71f81923f343f1c43f5dd2d
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72579183"
---
# <a name="using-statement-c-reference"></a>using – příkazC# (Referenční dokumentace)

Poskytuje pohodlný syntax, který zajišťuje správné použití <xref:System.IDisposable> objektů.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít příkaz `using`.

[!code-csharp[csrefKeywordsNamespace#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#4)]

Počínaje C# 8,0 můžete použít následující alternativní syntaxi pro příkaz `using`, který nevyžaduje složené závorky:

[!code-csharp[csrefKeywordsNamespace#New](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#ModernUsing)]

## <a name="remarks"></a>Poznámky

Příklady spravovaných typů, které přistupují k nespravovaným prostředkům (v tomto případě popisovače souborů a kontextech zařízení), jsou <xref:System.IO.File> a <xref:System.Drawing.Font>. Existuje mnoho dalších druhů nespravovaných prostředků a typů knihoven tříd, které je zapouzdřují. Všechny tyto typy musí implementovat rozhraní <xref:System.IDisposable>.

Pokud je životnost objektu `IDisposable` omezená na jedinou metodu, měli byste deklarovat a vytvořit jeho instanci v příkazu `using`. Příkaz `using` volá metodu <xref:System.IDisposable.Dispose%2A> objektu správným způsobem a (pokud ji použijete, jak je uvedeno výše), také způsobí, že se objekt sám dostanou mimo rozsah, jakmile se zavolá <xref:System.IDisposable.Dispose%2A>. V rámci `using` bloku je objekt určen jen pro čtení a nelze jej změnit ani znovu přiřadit.

Příkaz `using` zajišťuje, že <xref:System.IDisposable.Dispose%2A> je volána i v případě, že dojde k výjimce v rámci bloku `using`. Stejný výsledek můžete dosáhnout vložením objektu do `try` bloku a následným voláním <xref:System.IDisposable.Dispose%2A> v bloku `finally`; ve skutečnosti je to způsob, jak je příkaz `using` přeložen kompilátorem. Výše uvedený příklad kódu se v době kompilace rozšíří na následující kód (Poznamenejte si nadbytečné složené závorky pro vytvoření omezeného oboru pro objekt):

[!code-csharp[csrefKeywordsNamespace#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#5)]

Novější syntaxe příkazu `using` se překládá na velmi podobný kód. Blok `try` se otevře, kde je proměnná deklarována. Blok `finally` se přidá na konec ohraničujícího bloku, obvykle na konci metody.

Další informace o příkazu `try` - `finally` naleznete v tématu [try-finally](try-finally.md) .

V příkazu `using` lze deklarovat více instancí typu, jak je znázorněno v následujícím příkladu:

[!code-csharp[csrefKeywordsNamespace#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#6)]

Můžete zkombinovat více deklarací stejného typu pomocí nové syntaxe, kterou přináší i C# 8. To je znázorněno v následujícím příkladu:

[!code-csharp[csrefKeywordsNamespace#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#MultipleUsing)]

Můžete vytvořit instanci objektu prostředku a pak předat proměnnou do příkazu `using`, ale to není doporučený postup. V takovém případě, když ovládací prvek opustí blok `using`, objekt zůstane v oboru, ale pravděpodobně nemá přístup k jeho nespravovaným prostředkům. Jinými slovy, již není zcela inicializován. Pokud se pokusíte použít objekt mimo blok `using`, riskujete, že bude vyvolána výjimka. Z tohoto důvodu je obecně lepší vytvořit instanci objektu v příkazu `using` a omezit svůj rozsah na blok `using`.

[!code-csharp[csrefKeywordsNamespace#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#7)]

Další informace o odstraňování `IDisposable` objektů naleznete v tématu [using Objects Implements IDisposable](../../../standard/garbage-collection/using-objects.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete ve [ C# specifikaci jazyka](../language-specification/index.md)v [příkazu Using](~/_csharplang/spec/statements.md#the-using-statement) . Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [using – direktiva](using-directive.md)
- [Uvolňování paměti](../../../standard/garbage-collection/index.md)
- [Použití objektů, které implementují IDisposable](../../../standard/garbage-collection/using-objects.md)
- [Rozhraní IDisposable](xref:System.IDisposable)
- [using – příkaz C# v 8,0](~/_csharplang/proposals/csharp-8.0/using.md)
