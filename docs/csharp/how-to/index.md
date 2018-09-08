---
title: Jak článků (Průvodce v C#)
description: Kolekce rychlé tipy a krátký, zaměřuje ukázky kódu
ms.date: 12/20/2017
ms.openlocfilehash: 9326235341ee38e46f4204b7b3d7f67cae2774af
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44191688"
---
# <a name="how-to-c"></a>Jak (C#)

V tom, jak příručce jazyka C# najdete rychlé odpovědi na běžné dotazy. V některých případech může být uvedena články v několika oddílech. Chtěli jsme se je bylo možné snadno najít pro více cesty pro hledání. 

## <a name="general-c-concepts"></a>Obecné C# – koncepce

Existuje několik tipů a triků, které jsou běžné postupy pro vývojáře jazyka C#.

- [Inicializace objektů pomocí inicializátoru objektu](../programming-guide/classes-and-structs/how-to-initialize-objects-by-using-an-object-initializer.md).
- [Další rozdíly mezi předáním struktury a třídy metody](../programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md).
- [Použití výrazů lambda](../programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md).
- [Řešení konfliktů název typu použití aliasu globálního oboru názvů](../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md).
- [Použití přetížení operátoru](../language-reference/keywords/operator.md).
- [Implementace a volání vlastní metody rozšíření](../programming-guide/classes-and-structs/how-to-implement-and-call-a-custom-extension-method.md).
- Dokonce i programátoři v C# může být vhodné [použít `My` obor názvů z VB](../programming-guide/namespaces/how-to-use-the-my-namespace.md).
- [Vytvoření nové metody pro `enum` zadejte pomocí metody rozšíření](../programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).

### <a name="class-and-struct-members"></a>Členy třídy a struktury

Vytváření tříd a struktur k implementaci aplikace. Tyto postupy se běžně používají při psaní třídy nebo struktury.

- [Automaticky implementované vlastnosti deklarovat](../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).
- [Deklarování a použití vlastností čtení/zápisu](../programming-guide/classes-and-structs/how-to-declare-and-use-read-write-properties.md).
- [Definovat konstanty](../programming-guide/classes-and-structs/how-to-define-constants.md).
- [Přepsat `ToString` metodu k dispozici výstupní řetězec](../programming-guide/classes-and-structs/how-to-override-the-tostring-method.md).
- [Definování abstraktních a vlastností](../programming-guide/classes-and-structs/how-to-define-abstract-properties.md).
- [Použití funkcí dokumentace xml pro dokumentaci kódu](../programming-guide/xmldoc/how-to-use-the-xml-documentation-features.md).
- [Explicitní implementace členů rozhraní](../programming-guide/interfaces/how-to-explicitly-implement-interface-members.md) zachovat veřejného rozhraní stručné.
- [Explicitní implementace členů dvou rozhraní](../programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md).

### <a name="working-with-collections"></a>Práce s kolekcemi

Tyto články vám pomohou při práci s kolekcemi dat.

- [Inicializace slovníku pomocí inicializátoru kolekce](../programming-guide/classes-and-structs/how-to-initialize-a-dictionary-with-a-collection-initializer.md).

## <a name="working-with-strings"></a>Práce s řetězci

Řetězce se základní datový typ použít k zobrazení nebo práci s textem. Tyto články ukazují běžné postupy s řetězci.

- [Porovnání řetězců](compare-strings.md).
- [Změna obsahu řetězce](modify-string-contents.md).
- [Určení Pokud řetězec reprezentuje číslo](../programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md).
- [Použití `String.Split` k rozdělení řetězců](parse-strings-using-split.md).
- [Kombinovat více řetězců do jednoho](concatenate-multiple-strings.md).
- [Hledání textu v řetězci](search-strings.md).

## <a name="convert-between-types"></a>Převod mezi typy

Budete muset převést objekt na jiný typ.

- [Určení Pokud řetězec reprezentuje číslo](../programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md).
- [Převod mezi řetězci, které představují šestnáctková čísla a čísla](../programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md).
- [Převést řetězec `DateTime` ](../../standard/base-types/parsing-datetime.md).
- [Převést pole bajtů na typ int](../programming-guide/types/how-to-convert-a-byte-array-to-an-int.md).
- [Převod řetězce na číslo](../programming-guide/types/how-to-convert-a-string-to-a-number.md).
- [Použít porovnávání vzorů, `as` a `is` operátory bezpečně přetypovat na jiný typ](../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md).
- [Definovat operátory převodu pro `struct` typy](../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md).
- [Určení, zda je typ s možnou hodnotou Null typu](../programming-guide/nullable-types/how-to-identify-a-nullable-type.md).
- [Převod mezi typy hodnot s povolenou hodnotou Null a Null](../programming-guide/nullable-types/using-nullable-types.md#conversion-from-a-nullable-type-to-an-underlying-type).

## <a name="equality-and-ordering-comparisons"></a>Porovnání rovnosti a řazení

Můžete vytvořit typy, které definovat vlastní pravidla pro rovnost nebo definovat přirozené řazení mezi objekty daného typu.

- [Testování založené na referenční rovnosti](../programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md).
- [Definování založené na hodnotách rovnosti pro typ](../programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md).

## <a name="exception-handling"></a>Zpracování výjimek

Programy .NET zprávu, že metody nebyla úspěšně dokončena práci vyvoláním výjimky. V těchto článcích se dozvíte, pro práci s výjimky.

- [Zpracování výjimek pomocí `try` a `catch` ](../programming-guide/exceptions/how-to-handle-an-exception-using-try-catch.md).
- [Vyčištění prostředků pomocí `finally` klauzule](../programming-guide/exceptions/how-to-execute-cleanup-code-using-finally.md).
- [Zotavení z výjimky neodpovídající specifikaci CLS (Common Language Specification)](../programming-guide/exceptions/how-to-catch-a-non-cls-exception.md).

## <a name="delegates-and-events"></a>Delegáti a události

Delegáti a události poskytují funkce pro strategií, které se týkají volně vázány bloky kódu.

- [Deklarování, vytváření instancí a používání delegátů](../programming-guide/delegates/how-to-declare-instantiate-and-use-a-delegate.md).
- [Kombinování delegátů vícesměrového vysílání](../programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md).

Události poskytují mechanismus pro publikování nebo přihlášení k odběru oznámení.

- [Přihlášení odběru a zrušit její odběr události](../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).
- [Implementace události deklarované v rozhraních](../programming-guide/events/how-to-implement-interface-events.md).
- [Pokud váš kód publikuje události v souladu s pokyny pro rozhraní .NET Framework](../programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md).
- [Vyvolávání událostí definovaných v základní třídy z odvozené třídy](../programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md).
- [Store instancí událostí ve slovníku](../programming-guide/events/how-to-use-a-dictionary-to-store-event-instances.md).
- [Implementace vlastních přístupových objektů událostí](../programming-guide/events/how-to-implement-custom-event-accessors.md).

## <a name="linq-practices"></a>Postupy pro LINQ

LINQ umožňuje napsat kód k dotazování libovolný zdroj dat, která podporuje vzor výrazu dotazu LINQ. Tyto články vám pomůžou pochopení způsobu a práce s různými datovými zdroji.

- [Dotazování na kolekci](../programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md).
- [Použití výrazů lambda v dotazu](../programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-in-a-query.md).
- [Použití `var` ve výrazech dotazů](../programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).
- [Vrácení podmnožin vlastností elementu v dotazu](../programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md).
- [Vytváření dotazů s komplexním filtrováním](../programming-guide/concepts/linq/how-to-write-queries-with-complex-filtering.md).
- [Řazení elementů zdroje dat](../programming-guide/concepts/linq/how-to-sort-elements.md).
- [Řazení elementů u více klíčů](../programming-guide/concepts/linq/how-to-sort-elements-on-multiple-keys.md).
- [Řízení typu projekce](../programming-guide/concepts/linq/how-to-control-the-type-of-a-projection.md).
- [Počet výskytů hodnoty ve zdrojové sekvence](../programming-guide/concepts/linq/how-to-count-occurrences-of-a-word-in-a-string-linq.md).
- [Výpočet mezilehlých hodnot](../programming-guide/concepts/linq/how-to-calculate-intermediate-values.md).
- [Sloučit data z víc zdrojů](../programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md).
- [Hledání množinových rozdílů mezi dvěma sekvencemi](../programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md).
- [Ladění prázdný dotaz výsledky](../programming-guide/concepts/linq/how-to-debug-empty-query-results-sets.md).
- [Přidání vlastních metod do dotazů LINQ](../programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md).

## <a name="multiple-threads-and-async-processing"></a>Více vláken a asynchronní zpracování

Moderní aplikace často používají asynchronní operace. Tyto články vám informace o použití těchto technik.

- [Vylepšení pomocí asynchronní výkonu `System.Threading.Tasks.Task.WhenAll` ](../programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).
- [Pomocí paralelní provádění vícenásobných webových `async` a `await` ](../programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md).
- [Použití fondu vláken](../../standard/threading/the-managed-thread-pool.md#using-the-thread-pool).

## <a name="command-line-args-to-your-program"></a>Argumenty příkazového řádku pro program

Programy jazyka C# obvykle mít argumenty příkazového řádku. Tyto články vás naučí, přístup a zpracování těchto argumentů příkazového řádku.

- [Načíst všechny argumenty příkazového řádku s `for` ](../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md).
- [Načíst všechny argumenty příkazového řádku s `foreach` ](../programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md).
