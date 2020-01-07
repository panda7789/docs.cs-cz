---
title: Články (C# průvodce)
description: Kolekce rychlých tipů a krátkých a podrobných ukázek kódu
ms.date: 12/20/2017
ms.openlocfilehash: e6cb657726b82a1710bbcd596fe48037b5c26352
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75339223"
---
# <a name="how-to-c"></a>Postupy (C#)

V části Postupy v C# příručce můžete najít rychlé odpovědi na běžné otázky. V některých případech mohou být články uvedeny ve více částech. Chtěli bychom snadno najít více cest pro hledání.

## <a name="general-c-concepts"></a>Obecné C# koncepty

K dispozici je několik tipů a rad, C# které představují běžné postupy pro vývojáře:

- [Inicializujte objekty pomocí inicializátoru objektu](../programming-guide/classes-and-structs/how-to-initialize-objects-by-using-an-object-initializer.md).
- [Přečtěte si o rozdílech mezi předáním struktury a třídy metodě](../programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md).
- [Použijte přetížení operátoru](../language-reference/operators/operator-overloading.md).
- [Implementujte a zavolejte vlastní metodu rozšíření](../programming-guide/classes-and-structs/how-to-implement-and-call-a-custom-extension-method.md).
- I C# programátoři mohou chtít [použít `My` obor názvů z Visual Basic](../programming-guide/namespaces/how-to-use-the-my-namespace.md).
- [Vytvořte novou metodu pro `enum` typ pomocí rozšiřujících metod](../programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).

### <a name="class-and-struct-members"></a>Členové třídy a struktury

Vytvoříte třídy a struktury pro implementaci programu. Tyto techniky se běžně používají při psaní tříd nebo struktur.

- [Deklarovat automaticky implementované vlastnosti](../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).
- [Deklarovat a používat vlastnosti pro čtení a zápis](../programming-guide/classes-and-structs/how-to-declare-and-use-read-write-properties.md).
- [Definovat konstanty](../programming-guide/classes-and-structs/how-to-define-constants.md).
- [Přepište metodu `ToString` pro poskytnutí výstupu řetězce](../programming-guide/classes-and-structs/how-to-override-the-tostring-method.md).
- [Definujte abstraktní vlastnosti](../programming-guide/classes-and-structs/how-to-define-abstract-properties.md).
- [Použití funkcí dokumentace XML k dokumentaci kódu](../programming-guide/xmldoc/how-to-use-the-xml-documentation-features.md).
- [Explicitně implementujte členy rozhraní](../programming-guide/interfaces/how-to-explicitly-implement-interface-members.md) , aby se vaše veřejné rozhraní zachovalo jako stručné.
- [Explicitně implementujte členy dvou rozhraní](../programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md).

### <a name="working-with-collections"></a>Práce s kolekcemi

Tyto články vám pomůžou pracovat s kolekcemi dat.

- [Inicializujte slovník pomocí inicializátoru kolekce](../programming-guide/classes-and-structs/how-to-initialize-a-dictionary-with-a-collection-initializer.md).

## <a name="working-with-strings"></a>Práce s řetězci

Řetězce jsou základní datový typ, který slouží k zobrazení nebo manipulaci s textem. Tyto články ukazují běžné postupy s řetězci.

- [Porovnejte řetězce](compare-strings.md).
- [Upravte obsah řetězce](modify-string-contents.md).
- [Určí, zda řetězec představuje číslo](../programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md).
- [K oddělení řetězců použijte `String.Split`](parse-strings-using-split.md).
- [Kombinovat více řetězců do jednoho](concatenate-multiple-strings.md).
- [Hledání textu v řetězci](search-strings.md).

## <a name="convert-between-types"></a>Převod mezi typy

Možná budete muset převést objekt na jiný typ.

- [Určí, zda řetězec představuje číslo](../programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md).
- [Převod mezi řetězci, které reprezentují hexadecimální čísla a číslo](../programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md).
- [Převést řetězec na `DateTime`](../../standard/base-types/parsing-datetime.md).
- [Převést pole bajtů na typ int](../programming-guide/types/how-to-convert-a-byte-array-to-an-int.md).
- [Převede řetězec na číslo](../programming-guide/types/how-to-convert-a-string-to-a-number.md).
- [Použijte porovnávání vzorů, operátory `as` a `is` bezpečně přetypování na jiný typ](../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md).
- [Definujte vlastní převody typů](../language-reference/operators/user-defined-conversion-operators.md).
- [Určí, zda typ představuje typ hodnoty s možnou hodnotou null](../language-reference/builtin-types/nullable-value-types.md#how-to-identify-a-nullable-value-type).
- [Převod mezi typy hodnot s možnou hodnotou null a hodnotami, které](../language-reference/builtin-types/nullable-value-types.md#conversion-from-a-nullable-value-type-to-an-underlying-type)neumožňují hodnotu null

## <a name="equality-and-ordering-comparisons"></a>Porovnání rovnosti a řazení

Můžete vytvořit typy, které definují vlastní pravidla pro rovnost, nebo definovat přirozené řazení mezi objekty daného typu.

- [Testování rovnosti založené na odkazech](../programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md).
- [Definování rovnosti na základě hodnoty pro typ](../programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md).

## <a name="exception-handling"></a>Ošetření výjimek

Programy .NET hlásí, že metody neúspěšně dokončily svou práci vyvoláním výjimek. V těchto článcích se naučíte pracovat s výjimkami.

- [Zpracování výjimek pomocí `try` a `catch`](../programming-guide/exceptions/how-to-handle-an-exception-using-try-catch.md).
- [Vyčistěte prostředky pomocí klauzulí `finally`](../programming-guide/exceptions/how-to-execute-cleanup-code-using-finally.md).
- [Obnovte z výjimek (Common Language Specification) bez specifikace CLS](../programming-guide/exceptions/how-to-catch-a-non-cls-exception.md).

## <a name="delegates-and-events"></a>Delegáti a události

Delegáti a události poskytují možnosti pro strategie, které zahrnují volně spojené bloky kódu.

- [Deklarovat, vytvořit instanci a použít delegáty](../programming-guide/delegates/how-to-declare-instantiate-and-use-a-delegate.md).
- [Kombinovat delegáty vícesměrového vysílání](../programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md).

Události poskytují mechanismus pro publikování oznámení nebo jejich přihlášení k odběru.

- [Přihlášení a odhlášení odběru událostí](../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)
- [Implementujte události deklarované v rozhraních](../programming-guide/events/how-to-implement-interface-events.md).
- [V souladu s pokyny pro .NET Framework, když kód publikuje události](../programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md).
- [Vyvolat události definované v základních třídách z odvozených tříd](../programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md).
- [Implementace vlastních přístupových objektů událostí](../programming-guide/events/how-to-implement-custom-event-accessors.md)

## <a name="linq-practices"></a>Postupy LINQ

LINQ umožňuje napsat kód pro dotazování libovolného zdroje dat, který podporuje vzor výrazu dotazu LINQ. Tyto články vám pomůžou pochopit vzor a pracovat s různými zdroji dat.

- [Dotaz na kolekci](../programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
- [Použití výrazů lambda v dotazu](../programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-in-a-query.md).
- [Ve výrazech dotazů použijte `var`](../programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).
- [Vrátí podmnožinu vlastností elementu z dotazu](../programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md).
- [Zápis dotazů se složitým filtrováním](../programming-guide/concepts/linq/how-to-write-queries-with-complex-filtering.md)
- [Seřadit prvky zdroje dat](../programming-guide/concepts/linq/how-to-sort-elements.md).
- [Seřadit prvky na více klíčů](../programming-guide/concepts/linq/how-to-sort-elements-on-multiple-keys.md).
- [Řízení typu projekce](../programming-guide/concepts/linq/how-to-control-the-type-of-a-projection.md).
- [Spočítá výskyty hodnoty ve zdrojové sekvenci](../programming-guide/concepts/linq/how-to-count-occurrences-of-a-word-in-a-string-linq.md).
- [Vypočítat mezilehlé hodnoty](../programming-guide/concepts/linq/how-to-calculate-intermediate-values.md).
- [Sloučí data z více zdrojů](../programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md).
- [Najde nastavený rozdíl mezi dvěma sekvencemi](../programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md).
- [Ladění prázdných výsledků dotazu](../programming-guide/concepts/linq/how-to-debug-empty-query-results-sets.md).
- [Přidejte vlastní metody do dotazů LINQ](../programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md).

## <a name="multiple-threads-and-async-processing"></a>Více vláken a asynchronní zpracování

Moderní programy často využívají asynchronní operace. Tyto články vám pomůžou se naučit používat tyto techniky.

- [Vylepšete asynchronní výkon pomocí `System.Threading.Tasks.Task.WhenAll`](../programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).
- [Paralelní provádění více webových požadavků pomocí `async` a `await`](../programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md).
- [Použijte fond vláken](../../standard/threading/the-managed-thread-pool.md#using-the-thread-pool).

## <a name="command-line-args-to-your-program"></a>Argumenty příkazového řádku pro program

C# Programy mají obvykle argumenty příkazového řádku. Tyto články vás seznámí s přístupem k argumentům příkazového řádku a jejich zpracování.

- [Načte všechny argumenty příkazového řádku pomocí `for`](../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md).
