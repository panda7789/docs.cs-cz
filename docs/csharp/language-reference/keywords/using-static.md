---
title: Using static – direktiva - C# odkaz
ms.custom: seodec18
ms.date: 03/10/2017
helpviewer_keywords:
- using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4fa8dc3c043665ca2f56facf516cb03e5c6bb9d7
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66421764"
---
# <a name="using-static-directive-c-reference"></a>Using static – direktiva (C# odkaz)

`using static` – Direktiva Určuje typ, jehož statické členy a vnořené typy, které máte přístup bez určení názvu typu. Syntaxe je:

```csharp
using static <fully-qualified-type-name>;
```

kde *plně kvalifikovaný type-name* je název typu, jehož statické členy a vnořené typy může být odkazováno bez zadání názvu typu. Pokud nezadáte plně kvalifikovaného názvu (úplná obor názvů spolu s názvem typu), C# vygeneruje Chyba kompilátoru [CS0246](../compiler-messages/cs0246.md): "Nebyl nalezen typ nebo obor názvů"typ nebo obor názvů. (nechybí using – direktiva nebo odkaz na sestavení?) ".

`using static` – Direktiva se vztahuje na libovolný typ, který má statické členy (nebo vnořené typy), i když má také členy instance. Však můžete členy instance volat pouze prostřednictvím instance typu.

`using static` – Direktiva byla zavedena v jazyce C# 6.

## <a name="remarks"></a>Poznámky

Při volání statického člena, který je obvykle zadat název typu spolu s názvem člena. Opakovaně zadávat název typu pro vyvolání členy typu může mít za následek verbose, skrytého kódu. Například následující definice `Circle` třídy odkazuje na počet členů <xref:System.Math> třídy.

[!code-csharp[using-static#1](~/samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]

Že eliminuje nutnost explicitně odkazovat <xref:System.Math> třídy pokaždé, když se odkazuje člen, `using static` – direktiva vytvoří, jaká část čisticího modulu kódu:

[!code-csharp[using-static#2](~/samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]

`using static` Importuje pouze přístupné statické členy a vnořené typy deklarované v zadaném typu.  Zděděné členy nejsou naimportovány.  Můžete importovat z libovolný typ s názvem using static – direktiva, včetně modulů jazyka Visual Basic.  Pokud F# nejvyšší úrovně funkce se zobrazí v metadatech jako statické členy pojmenovaného typu, jehož název je platný C# identifikátor, pak bude F# funkce lze importovat.

 `using static` Díky rozšiřující metody deklarované v zadaném typu, který je k dispozici pro vyhledávání v metodě rozšíření.  Nicméně názvy metod rozšíření nejsou naimportovány do oboru pro nekvalifikovaný odkaz v kódu.

 Metody se stejným názvem importován z různých typů podle různých `using static` direktivy ve stejné jednotce kompilace nebo obor názvů tvoří skupinu metod.  Řešení přetížení v rámci těchto skupin metody následuje běžných pravidel jazyka C#.

## <a name="example"></a>Příklad

V následujícím příkladu `using static` směrnice statické členy třídy <xref:System.Console>, <xref:System.Math>, a <xref:System.String> třídy, které jsou k dispozici bez nutnosti zadávat název jejich typu.

[!code-csharp[using-static#3](~/samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]

V tomto příkladu `using static` směrnice může také se použily <xref:System.Double> typu. To by provedly to lze zavolat <xref:System.Double.TryParse(System.String,System.Double@)> metody bez určení názvu typu. To však znamená méně čitelné kódu, protože bude nutné ke kontrole `using static` příkazy k určení číselného typu `TryParse` metoda je volána.

## <a name="see-also"></a>Viz také:

- [Using – direktiva](using-directive.md)
- [Referenční dokumentace jazyka C#](../index.md)
- [Klíčová slova jazyka C#](index.md)
- [Použití oboru názvů](../../programming-guide/namespaces/using-namespaces.md)
- [Obory názvů](../../programming-guide/namespaces/index.md)
