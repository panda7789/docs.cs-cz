---
title: použití statické direktivy – odkaz jazyka C#
ms.date: 03/10/2017
helpviewer_keywords:
- using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
ms.openlocfilehash: 55847aceb9fdf032ba533b82ee59be53761fa2c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712946"
---
# <a name="using-static-directive-c-reference"></a>pomocí statické direktivy (C# Reference)

Směrnice `using static` určuje typ, jehož statické členy a vnořené typy můžete přistupovat bez zadání názvu typu. Jeho syntaxe je:

```csharp
using static <fully-qualified-type-name>;
```

kde *plně kvalifikovaný název typu* je název typu, na jehož statické členy a vnořené typy lze odkazovat bez zadání názvu typu. Pokud nezadáte plně kvalifikovaný název typu (úplný název oboru názvů spolu s názvem typu), c# generuje chybu kompilátoru [CS0246](../compiler-messages/cs0246.md): "Typ nebo název oboru názvů 'typ/obor názvů' nebyl nalezen (chybí vám using directive nebo odkaz na sestavení?)".

Směrnice `using static` platí pro všechny typy, které má statické členy (nebo vnořené typy), i v případě, že má také členy instance. Členové instance však mohou být vyvoláni pouze prostřednictvím instance typu.

Směrnice `using static` byla zavedena v C# 6.

## <a name="remarks"></a>Poznámky

Obvykle při volání statického člena zadáte název typu spolu s názvem člena. Opakované zadání stejného názvu typu k vyvolání členů typu může mít za následek podrobný, obskurní kód. Například následující definice `Circle` třídy odkazuje na několik členů <xref:System.Math> třídy.

[!code-csharp[using-static#1](~/samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]

Tím, že eliminuje potřebu <xref:System.Math> explicitně odkazovat na třídu `using static` pokaždé, když je odkazováno na člen, směrnice vytváří mnohem čistší kód:

[!code-csharp[using-static#2](~/samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]

`using static`importuje pouze přístupné statické členy a vnořené typy deklarované v zadaném typu.  Zděděné členy nejsou importovány.  Můžete importovat z libovolného pojmenovaného typu pomocí statické směrnice, včetně modulů jazyka Visual Basic.  Pokud f# funkce nejvyšší úrovně se zobrazí v metadatech jako statické členy pojmenovaného typu, jehož název je platný identifikátor Jazyka C#, pak f# funkce lze importovat.

 `using static`zpřístupní metody rozšíření deklarované v zadaném typu pro vyhledávání metody rozšíření.  Názvy rozšiřujících metod však nejsou importovány do oboru pro neúplný odkaz v kódu.

 Metody se stejným názvem importované z `using static` různých typů různými direktivami ve stejné kompilační jednotce nebo oboru názvů tvoří skupinu metod.  Řešení přetížení v rámci těchto skupin metod se řídí normálními pravidly jazyka C#.

## <a name="example"></a>Příklad

Následující příklad používá `using static` direktivu k <xref:System.Console> <xref:System.Math>zpřístupnění <xref:System.String> statických členů , a tříd bez nutnosti zadávat jejich název typu.

[!code-csharp[using-static#3](~/samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]

V příkladu `using static` směrnice může být také <xref:System.Double> použita na typ. To by umožnilo volat <xref:System.Double.TryParse(System.String,System.Double@)> metodu bez zadání názvu typu. Tím se však vytvoří méně čitelný kód, `using static` protože je nutné zkontrolovat `TryParse` příkazy k určení, která metoda číselného typu je volána.

## <a name="see-also"></a>Viz také

- [pomocí směrnice](using-directive.md)
- [Odkaz jazyka C#](../index.md)
- [C# Klíčová slova](index.md)
- [Použití oborů názvů](../../programming-guide/namespaces/using-namespaces.md)
- [Obory názvů](../../programming-guide/namespaces/index.md)
