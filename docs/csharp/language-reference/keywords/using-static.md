---
title: použití statické direktivy C# – reference
ms.custom: seodec18
ms.date: 03/10/2017
helpviewer_keywords:
- using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
ms.openlocfilehash: 1a0e26d8b0a14e0c77b724fc492588e08762e47f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099999"
---
# <a name="using-static-directive-c-reference"></a>using static – direktiva (C# Referenční dokumentace)

Direktiva `using static` označuje typ, jehož statické členy a vnořené typy mají přístup bez zadání názvu typu. Jeho syntaxe je:

```csharp
using static <fully-qualified-type-name>;
```

kde *název plně kvalifikovaného typu* je název typu, jehož statické členy a vnořené typy mohou být odkazovány bez zadání názvu typu. Pokud nezadáte plně kvalifikovaný název typu (úplný název oboru názvů spolu s názvem typu), C# vygeneruje chybu kompilátoru [CS0246](../compiler-messages/cs0246.md): "typ nebo obor názvů ' Type/namespace ' nebyl nalezen (nechybí Direktiva using nebo Assembly odkaz?) ".

Direktiva `using static` se vztahuje na jakýkoli typ, který má statické členy (neboli vnořené typy), i když má také členy instance. Členy instance lze však vyvolat pouze prostřednictvím instance typu.

Direktiva `using static` byla představena C# v 6.

## <a name="remarks"></a>Poznámky

Obvykle při volání statického členu zadáte název typu společně s názvem člena. Opakované zadání stejného názvu typu pro vyvolání členů typu může mít za následek verbose, zakrytí kódu. Například následující definice `Circle` třídy odkazuje na řadu členů <xref:System.Math> třídy.

[!code-csharp[using-static#1](~/samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]

Zrušením nutnosti explicitního odkazování na třídu <xref:System.Math> pokaždé, když na člena odkazuje, direktiva `using static` vytvoří mnohem čisticí kód:

[!code-csharp[using-static#2](~/samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]

`using static` importuje pouze dostupné statické členy a vnořené typy deklarované v zadaném typu.  Zděděné členy nejsou naimportovány.  Můžete importovat z libovolného pojmenovaného typu pomocí statické direktivy using, včetně Visual Basicch modulů.  Pokud F# jsou funkce nejvyšší úrovně zobrazeny v metadatech jako statické členy pojmenovaného typu, jehož název je platný C# identifikátor, lze F# funkce importovat.

 `using static` zpřístupňuje metody rozšíření deklarované v zadaném typu pro vyhledávání rozšiřující metody.  Názvy metod rozšíření však nejsou importovány do oboru pro nekvalifikované odkazy v kódu.

 Metody se stejným názvem importované z různých typů pomocí různých direktiv `using static` ve stejné kompilační jednotce nebo oboru názvů tvoří skupinu metod.  Rozlišení přetížení v rámci těchto skupin metod dodržuje normální C# pravidla.

## <a name="example"></a>Příklad

V následujícím příkladu je použita direktiva `using static` k zpřístupnění statických členů tříd <xref:System.Console>, <xref:System.Math>a <xref:System.String>, aniž by bylo nutné určit jejich název typu.

[!code-csharp[using-static#3](~/samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]

V tomto příkladu by mohla být také použita direktiva `using static` na typ <xref:System.Double>. To by mělo být možné volat metodu <xref:System.Double.TryParse(System.String,System.Double@)> bez zadání názvu typu. To však vytvoří méně čitelný kód, protože je nutné kontrolovat `using static` příkazy k určení, která metoda `TryParse` číselného typu je volána.

## <a name="see-also"></a>Viz také:

- [using – direktiva](using-directive.md)
- [C#Odkaz](../index.md)
- [Klíčová slova jazyka C#](index.md)
- [Použití oboru názvů](../../programming-guide/namespaces/using-namespaces.md)
- [Obory názvů](../../programming-guide/namespaces/index.md)
