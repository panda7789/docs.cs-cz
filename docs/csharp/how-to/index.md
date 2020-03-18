---
title: Jak články (C# Guide)
description: Kolekce rychlých tipů a krátkých, zaměřených vzorků kódu
ms.date: 12/20/2017
ms.openlocfilehash: e6cb657726b82a1710bbcd596fe48037b5c26352
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399320"
---
# <a name="how-to-c"></a>Jak (C#)

V části Jak průvodce C# najdete rychlé odpovědi na běžné otázky. V některých případech mohou být články uvedeny ve více oddílech. Chtěli jsme, aby byly snadno k nalezení pro více vyhledávacích cest.

## <a name="general-c-concepts"></a>Obecné koncepty jazyka C#

Existuje několik tipů a triků, které jsou běžné postupy pro vývojáře jazyka C#:

- [Inicializovat objekty pomocí inicializátoru objektu](../programming-guide/classes-and-structs/how-to-initialize-objects-by-using-an-object-initializer.md).
- [Naučte se rozdíly mezi předáním struktury a třídy metodě](../programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md).
- [Použijte přetížení operátoru](../language-reference/operators/operator-overloading.md).
- [Implementovat a volat vlastní metodu rozšíření](../programming-guide/classes-and-structs/how-to-implement-and-call-a-custom-extension-method.md).
- I programátoři jazyka C# mohou [chtít použít obor `My` názvů z jazyka Visual Basic](../programming-guide/namespaces/how-to-use-the-my-namespace.md).
- [Vytvořte novou `enum` metodu pro typ pomocí rozšiřujících metod](../programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).

### <a name="class-and-struct-members"></a>Členové třídy a struktury

Můžete vytvořit třídy a struktury k implementaci programu. Tyto techniky se běžně používají při psaní tříd nebo struktur.

- [Deklarovat automaticky implementované vlastnosti](../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).
- [Deklarovat a používat vlastnosti čtení a zápisu](../programming-guide/classes-and-structs/how-to-declare-and-use-read-write-properties.md).
- [Definujte konstanty](../programming-guide/classes-and-structs/how-to-define-constants.md).
- [Přepsat metodu `ToString` poskytnout výstup řetězce](../programming-guide/classes-and-structs/how-to-override-the-tostring-method.md).
- [Definujte abstraktní vlastnosti](../programming-guide/classes-and-structs/how-to-define-abstract-properties.md).
- [Pomocí funkcí dokumentace xml můžete dokumentovat kód](../programming-guide/xmldoc/how-to-use-the-xml-documentation-features.md).
- [Explicitně implementovat členy rozhraní,](../programming-guide/interfaces/how-to-explicitly-implement-interface-members.md) aby vaše veřejné rozhraní stručné.
- [Explicitně implementovat členy dvou rozhraní](../programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md).

### <a name="working-with-collections"></a>Práce s kolekcemi

Tyto články vám pomohou pracovat s kolekcemi dat.

- [Inicializovat slovník s inicializátorem kolekce](../programming-guide/classes-and-structs/how-to-initialize-a-dictionary-with-a-collection-initializer.md).

## <a name="working-with-strings"></a>Práce s řetězci

Řetězce jsou základní datový typ používaný k zobrazení textu nebo manipulaci s ním. Tyto články ukazují běžné postupy s řetězci.

- [Porovnat řetězce](compare-strings.md).
- [Upravte obsah řetězce](modify-string-contents.md).
- [Zjistěte, zda řetězec představuje číslo](../programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md).
- [Slouží `String.Split` k oddělení řetězců](parse-strings-using-split.md).
- [Zkombinujte více řetězců do jednoho](concatenate-multiple-strings.md).
- [Vyhledejte text v řetězci](search-strings.md).

## <a name="convert-between-types"></a>Převod mezi typy

Možná budete muset převést objekt na jiný typ.

- [Zjistěte, zda řetězec představuje číslo](../programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md).
- [Převod mezi řetězci, které představují šestnáctková čísla, a číslem](../programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md).
- [Převést řetězec `DateTime`na ](../../standard/base-types/parsing-datetime.md).
- [Převést bajtové pole na int](../programming-guide/types/how-to-convert-a-byte-array-to-an-int.md).
- [Převeďte řetězec na číslo](../programming-guide/types/how-to-convert-a-string-to-a-number.md).
- [Pomocí porovnávání `as` vzorů, a `is` operátory bezpečně přetypovat na jiný typ](../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md).
- [Definujte převody vlastního typu](../language-reference/operators/user-defined-conversion-operators.md).
- [Zjistěte, zda je typ typu s možnou hodnotou s možnou hodnotou .](../language-reference/builtin-types/nullable-value-types.md#how-to-identify-a-nullable-value-type)
- [Převod mezi typy hodnot s možnou hodnotou null a hodnotou, která ji nelze.](../language-reference/builtin-types/nullable-value-types.md#conversion-from-a-nullable-value-type-to-an-underlying-type)

## <a name="equality-and-ordering-comparisons"></a>Rovnost a řazení porovnání

Můžete vytvořit typy, které definují vlastní pravidla pro rovnost nebo definovat přirozené řazení mezi objekty tohoto typu.

- [Test rovnosti založené na referencích](../programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md).
- [Definujte rovnost založenou na hodnotách pro typ](../programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md).

## <a name="exception-handling"></a>Zpracování výjimek

Programy .NET hlásí, že metody úspěšně nedokončily svou práci vyvoláním výjimek. V těchto článcích se naučíte pracovat s výjimkami.

- [Zpracování výjimek `try` `catch`pomocí a ](../programming-guide/exceptions/how-to-handle-an-exception-using-try-catch.md).
- [Vyčištění prostředků `finally` pomocí klauzule](../programming-guide/exceptions/how-to-execute-cleanup-code-using-finally.md).
- [Obnovení z výjimek, které nejsou specifiky než CLS (Common Language Specification).](../programming-guide/exceptions/how-to-catch-a-non-cls-exception.md)

## <a name="delegates-and-events"></a>Delegáti a akce

Delegáti a události poskytují možnost pro strategie, které zahrnují volně vázané bloky kódu.

- [Deklarovat, konkretizovat a používat delegáty](../programming-guide/delegates/how-to-declare-instantiate-and-use-a-delegate.md).
- [Zkombinujte delegáty vícesměrového vysílání](../programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md).

Události poskytují mechanismus pro publikování nebo přihlášení k odběru oznámení.

- [Přihlásit se k odběru a odhlásit se z odběru událostí](../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).
- [Implementujte události deklarované v rozhraních](../programming-guide/events/how-to-implement-interface-events.md).
- Při publikování [událostí kódu dohovejte pokynů rozhraní .NET Framework](../programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md).
- [Vyvolat události definované v základních třídách z odvozených tříd](../programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md).
- [Implementujte vlastní přístupové objekty událostí](../programming-guide/events/how-to-implement-custom-event-accessors.md).

## <a name="linq-practices"></a>Postupy LINQ

LINQ umožňuje psát kód pro dotaz na libovolný zdroj dat, který podporuje vzor výrazu dotazu LINQ. Tyto články vám pomohou pochopit vzor a pracovat s různými zdroji dat.

- [Dotaz na kolekci](../programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md).
- [V dotazu používejte výrazy lambda](../programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-in-a-query.md).
- [Používá `var` se ve výrazech dotazu](../programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).
- [Vrátí podmnožiny vlastností elementu z dotazu](../programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md).
- [Psát dotazy se složitým filtrováním](../programming-guide/concepts/linq/how-to-write-queries-with-complex-filtering.md).
- [Třídit prvky zdroje dat](../programming-guide/concepts/linq/how-to-sort-elements.md).
- [Řazení prvků na více klíčích](../programming-guide/concepts/linq/how-to-sort-elements-on-multiple-keys.md).
- [Ovládejte typ projekce](../programming-guide/concepts/linq/how-to-control-the-type-of-a-projection.md).
- [Počítat výskyty hodnoty ve zdrojové sekvenci](../programming-guide/concepts/linq/how-to-count-occurrences-of-a-word-in-a-string-linq.md).
- [Výpočet mezilehlých hodnot](../programming-guide/concepts/linq/how-to-calculate-intermediate-values.md).
- [Sloučení dat z více zdrojů](../programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md).
- [Najít nastavit rozdíl mezi dvěma sekvencemi](../programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md).
- [Ladění prázdných výsledků dotazu](../programming-guide/concepts/linq/how-to-debug-empty-query-results-sets.md).
- [Přidejte vlastní metody do dotazů LINQ](../programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md).

## <a name="multiple-threads-and-async-processing"></a>Více vláken a asynchronní zpracování

Moderní programy často používají asynchronní operace. Tyto články vám pomohou naučit se používat tyto techniky.

- [Zlepšete `System.Threading.Tasks.Task.WhenAll`asynchronní výkon pomocí ](../programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)aplikace .
- [Vytvořte více webových `async` požadavků `await`paralelně pomocí a ](../programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md).
- [Použijte fond vláken](../../standard/threading/the-managed-thread-pool.md#using-the-thread-pool).

## <a name="command-line-args-to-your-program"></a>Příkazový řádek args do vašeho programu

Programy jazyka C# mají obvykle argumenty příkazového řádku. Tyto články vás naučí přístup a zpracování těchto argumentů příkazového řádku.

- [Načíst všechny argumenty `for`příkazového řádku s . ](../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
