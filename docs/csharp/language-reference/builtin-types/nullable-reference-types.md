---
title: Typy odkazů s možnou hodnotou Null – odkaz jazyka C#
description: Informace o typech odkazů s možnou hodnotou C# s možnou hodnotou null a jejich použití
ms.date: 04/06/2020
ms.openlocfilehash: cbc7397ac76b43b79a4168f4c61fe2c631b4a46b
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888314"
---
# <a name="nullable-reference-types-c-reference"></a>Typy odkazů s možnou hodnotou Null (odkaz jazyka C#)

> [!NOTE]
> Tento článek popisuje referenční typy s možnou hodnotou null. Můžete také deklarovat [typy hodnot s možnou hodnotou.](nullable-value-types.md)

Nulllze typy odkazů jsou k dispozici počínaje C# 8.0, v kódu, který se přihlásil do *kontextu s platností null*. Typy odkazů s možnou hodnotou Null, upozornění na statickou analýzu null a [operátor odpouštějící nulu](../operators/null-forgiving.md) jsou volitelné funkce jazyka. Všechny jsou ve výchozím nastavení vypnuty. Kontext *s možnou hodnotou null* je řízen na úrovni projektu pomocí nastavení sestavení nebo v kódu pomocí pragmas.

 V kontextu s výhodami, které lze uznat s platností:

- Proměnná typu `T` odkazu musí být inicializována s hodnotou non-null `null`a nesmí jí být nikdy přiřazena hodnota, která může být .
- Proměnná referenčního `T?` typu může být `null` inicializována nebo `null`přiřazena `null` , ale musí být před zrušením odkazování zkontrolována.
- Proměnná `m` typu `T?` je považována za non-null při použití operátoru null `m!`odpouštějící, jako v .

Rozdíl mezi typ `T` odkazu s nemožnou hodnotou `T?` null a typ odkazu s možnou hodnotou null jsou vynuceny interpretací předchozích pravidel kompilátorem. Proměnná typu `T` a proměnná `T?` typu jsou reprezentovány stejným typem .NET. Následující příklad deklaruje řetězec s nulovou hodnotou a řetězec s hodnotou null a poté použije operátor null-forgiving k přiřazení hodnoty řetězci, který nelze utajit s nulou:

:::code language="csharp" source="snippets/NullableReferenceTypes.cs" id="SnippetCoreSyntax":::

Proměnné `notNull` a `nullable` jsou reprezentovány <xref:System.String> typem. Vzhledem k tomu, že typy s možnou hodnotou null a null lze uložit jako stejný typ, existuje několik umístění, kde není povoleno použití typu odkazu s možnou hodnotou null. Obecně platí, že typ odkazu s možnou hodnotou null nelze použít jako základní třídu nebo implementované rozhraní. Typ odkazu s možnou hodnotou null nelze použít při žádném výrazu pro vytváření objektů nebo testování typu. Typ odkazu s možnou hodnotou null nemůže být typem výrazu přístupu člena. Následující příklady ukazují tyto konstrukce:

```csharp
public MyClass : System.Object? // not allowed
{
}

var nullEmpty = System.String?.Empty; // Not allowed
var maybeObject = new object?(); // Not allowed
try
{
    if (thing is string? nullableString) // not allowed
        Console.WriteLine(nullableString);
} catch (Exception? e) // Not Allowed
{
    Console.WriteLine("error");
}
```

## <a name="nullable-references-and-static-analysis"></a>Odkazy s možnou hodnotou null a statická analýza

Příklady v předchozí části ilustrují povahu typů odkazů s možnou hodnotou null. Typy odkazů s možnou hodnotou Null nejsou nové typy tříd, ale spíše poznámky na existující chod odkazů. Kompilátor používá tyto poznámky, které vám pomohou najít potenciální chyby odkazu null ve vašem kódu. Neexistuje žádný rozdíl za běhu mezi typ odkazu s hodnotou nes holých hodnot a typ odkazu s možnou hodnotou null. Kompilátor nepřidá žádnou kontrolu za běhu pro typy odkazů s nulou. Výhody jsou v analýze kompilace. Kompilátor generuje upozornění, která vám pomohou najít a opravit potenciální chyby null ve vašem kódu. Deklarujete svůj záměr a kompilátor vás upozorní, když váš kód tento záměr poruší.

V kontextu s povolenou hodnotou null kompilátor provádí statickou analýzu proměnných libovolného typu odkazu, a to jak s hodnotou null, tak s hodnotou null. Kompilátor sleduje stav null každé referenční proměnné jako *buď není null* nebo možná *null*. Výchozí stav odkazu, který nelze utnou ta nulu, *nemá hodnotu null*. Výchozí stav odkazu s možnou hodnotou null je *pravděpodobně null*.

Nenulové typy odkazů by měly být vždy bezpečné pro zrušení odkazu, protože jejich stav null *není null*. Chcete-li vynutit toto pravidlo, kompilátor vydá upozornění, pokud typ odkazu, který nelze uvážit, není inicializován na hodnotu bez null. Místní proměnné musí být přiřazeny tam, kde jsou deklarovány. Každý konstruktor musí přiřadit každé pole, buď v jeho těle, volaný konstruktor, nebo pomocí inicializátoru pole. Kompilátor vydává upozornění, pokud je odkaz s nulovou hodnotou přiřazen k odkazu, jehož stav je *možná null*. Však vzhledem k tomu, že odkaz, který nelze hodnotit hodnotu null, *není null*, nejsou vydána žádná upozornění, pokud jsou tyto proměnné de-referenced.

Typy odkazů s možnou hodnotou `null`Null mohou být inicializovány nebo přiřazeny . Proto musí statická analýza určit, že proměnná *není null* před je odkazován. Pokud je odkaz s možnou hodnotou null určen *jako pravděpodobně null*, nelze jej přiřadit k referenční proměnné, na které nelze stanovit hodnotu null. Následující třída ukazuje příklady těchto upozornění:

:::code language="csharp" source="snippets/NullableReferenceTypes.cs" id="SnippetClassWithNullable":::

Následující úryvek ukazuje, kde kompilátor vydává upozornění při použití této třídy:

:::code language="csharp" source="snippets/NullableReferenceTypes.cs" id="SnippetLocalWarnings":::

Předchozí příklady ukazují statické analýzy kompilátoru k určení nulového stavu referenčních proměnných. Kompilátor použije jazyková pravidla pro nulové kontroly a přiřazení, aby informoval svou analýzu.  Kompilátor nemůže dělat předpoklady o sémantiku metod nebo vlastností. Pokud voláte metody, které provádějí nulové kontroly, kompilátor nemůže vědět, tyto metody ovlivňují stav null proměnné. Existuje několik atributů, které můžete přidat do svých api informovat kompilátor o sémantiku argumentů a vrácené hodnoty. Tyto atributy byly použity pro mnoho běžných rozhraní API v knihovnách .NET Core. Například <xref:System.String.IsNullOrEmpty%2A> byla aktualizována a kompilátor správně interpretuje tuto metodu jako kontrolu null. Další informace o atributech, které platí pro statickou analýzu nulového stavu, naleznete v článku [atributů Nullable](../../nullable-attributes.md).

## <a name="setting-the-nullable-context"></a>Nastavení kontextu s možnou hodnotou null

Existují dva způsoby, jak řídit kontext s možnou hodnotou null. Na úrovni projektu můžete přidat `<Nullable>enable</Nullable>` nastavení projektu. Ve zdrojovém souboru C# `#nullable enable` můžete přidat pragma povolit kontext s možnou hodnotou null. Viz článek o [nastavení strategie s možnou hodnotou null](../../nullable-attributes.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v následujících návrzích [specifikace jazyka C#](~/_csharplang/spec/introduction.md):

- [Odkazové typy s možnou hodnotou null](~/_csharplang/proposals/csharp-8.0/nullable-reference-types.md)
- [Návrh specifikace referenčních typů s možnou hodnotou null](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md)

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Typy hodnot s povolenou hodnotou Null](nullable-value-types.md)
