---
description: použití statické direktivy – Reference jazyka C#
title: použití statické direktivy – Reference jazyka C#
ms.date: 03/10/2017
helpviewer_keywords:
- using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
ms.openlocfilehash: a10c315a05c28bce9b5ddb65af67dde6446d031d
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141917"
---
# <a name="using-static-directive-c-reference"></a>using static – direktiva (Referenční dokumentace jazyka C#)

Tato `using static` direktiva určuje typ, jehož statické členy a vnořené typy mají přístup bez zadání názvu typu. Jeho syntaxe je:

```csharp
using static <fully-qualified-type-name>;
```

kde *název plně kvalifikovaného typu* je název typu, jehož statické členy a vnořené typy mohou být odkazovány bez zadání názvu typu. Pokud nezadáte plně kvalifikovaný název typu (úplný název oboru názvů spolu s názvem typu), C# generuje chybu kompilátoru [CS0246](../compiler-messages/cs0246.md): "typ nebo obor názvů ' Type/namespace ' nebyl nalezen (nechybí Direktiva using nebo odkaz na sestavení?)".

`using static`Direktiva se vztahuje na libovolný typ, který má statické členy (nebo vnořené typy), i když má také členy instance. Členy instance lze však vyvolat pouze prostřednictvím instance typu.

`using static`Direktiva byla představena v C# 6.

## <a name="remarks"></a>Poznámky

Obvykle při volání statického členu zadáte název typu společně s názvem člena. Opakované zadání stejného názvu typu pro vyvolání členů typu může mít za následek verbose, zakrytí kódu. Například následující definice `Circle` třídy odkazuje na určitý počet členů <xref:System.Math> třídy.

[!code-csharp[using-static#1](~/samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]

Zrušením nutnosti explicitního odkazování na <xref:System.Math> třídu pokaždé, když na člena je odkazováno, tato `using static` direktiva vytvoří mnohem čisticí kód:

[!code-csharp[using-static#2](~/samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]

`using static` importuje pouze dostupné statické členy a vnořené typy deklarované v zadaném typu.  Zděděné členy nejsou naimportovány.  Můžete importovat z libovolného pojmenovaného typu pomocí statické direktivy using, včetně Visual Basicch modulů.  Pokud jsou funkce nejvyšší úrovně F # zobrazeny v metadatech jako statické členy pojmenovaného typu, jehož název je platný identifikátor jazyka C#, mohou být importovány funkce jazyka F #.

 `using static` Zpřístupňuje metody rozšíření deklarované v zadaném typu k dispozici pro vyhledávání rozšiřující metody.  Názvy metod rozšíření však nejsou importovány do oboru pro nekvalifikované odkazy v kódu.

 Metody se stejným názvem importované z různých typů podle různých `using static` direktiv ve stejné kompilační jednotce nebo oboru názvů tvoří skupinu metod.  Rozlišení přetížení v rámci těchto skupin metod sleduje normální pravidla jazyka C#.

## <a name="example"></a>Příklad

V následujícím příkladu je použita `using static` direktiva k tomu, aby byly statické <xref:System.Console> členy <xref:System.Math> tříd, a <xref:System.String> dostupné bez nutnosti zadat jejich název typu.

[!code-csharp[using-static#3](~/samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]

V tomto příkladu `using static` byla direktiva také použita pro <xref:System.Double> typ. To by mělo být umožněno volání <xref:System.Double.TryParse(System.String,System.Double@)> metody bez zadání názvu typu. Tím se však vytvoří méně čitelný kód, protože je nutné ověřit `using static` direktivy, abyste zjistili, která metoda číselného typu `TryParse` je volána.

## <a name="see-also"></a>Viz také

- [using – direktiva](using-directive.md)
- [Reference jazyka C#](../index.md)
- [Klíčová slova jazyka C#](index.md)
- [Používání oborů názvů](../../programming-guide/namespaces/using-namespaces.md)
- [Jmenné prostory](../../programming-guide/namespaces/index.md)
