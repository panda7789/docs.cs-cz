---
title: "Postup články (Průvodce C#)"
description: "Kolekce rychlé tipy a krátké, zaměřuje ukázky kódu"
author: billwagner
ms.author: wiwagn
ms.date: 12/20/2017
ms.topic: article
ms.prod: .net
ms.devlang: devlang-csharp
ms.openlocfilehash: 04c780980ef0665b40a0c3a698193fc9fa738424
ms.sourcegitcommit: bf8a3ba647252010bdce86dd914ac6c61b5ba89d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/06/2018
---
# <a name="how-to-c"></a>Postup (C#)

V tom, jak část průvodce C# můžete získat rychlý odpovědi na časté otázky. V některých případech může být uvedena články v několika oddílech. Jsme chtěli, aby byly snadno najít pro více cest hledání. 

## <a name="general-c-concepts"></a>Obecné C# – koncepty

Existuje několik tipy a triky, které jsou obvyklé postupy vývojáře jazyka C#.

- [Inicializace objektů pomocí inicializátoru objektu](../programming-guide/classes-and-structs/how-to-initialize-objects-by-using-an-object-initializer.md).
- [Rozdíly mezi předáním struktury a třídy metody](../programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md).
- [Postup použití výrazů lambda](../programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md).
- [Řešení konfliktů název typu za použití aliasu globálního oboru názvů](../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md).
- [Přetížení operátoru použití](../programming-guide/statements-expressions-operators/how-to-use-operator-overloading-to-create-a-complex-number-class.md).
- [Implementace a volání vlastní metody rozšíření](../programming-guide/classes-and-structs/how-to-implement-and-call-a-custom-extension-method.md).
- Může být vhodné i programátory v jazyce C# [použít `My` oboru názvů z VB](../programming-guide/namespaces/how-to-use-the-my-namespace.md).
- [Vytvoření nové metody pro `enum` zadejte metodami rozšíření](../programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).

### <a name="class-and-struct-members"></a>Členy třídy a struktury

Vytváření tříd a struktur k implementaci vašeho programu. Tyto postupy běžně se používají při zápisu třídy nebo struktury.

- [Automaticky implementované vlastnosti deklarovat](../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).
- [Deklarování a použití vlastností čtení/zápisu](../programming-guide/classes-and-structs/how-to-declare-and-use-read-write-properties.md).
- [Definování konstant](../programming-guide/classes-and-structs/how-to-define-constants.md).
- [Přepsání `ToString` metody můžete zajistit výstupní řetězec](../programming-guide/classes-and-structs/how-to-override-the-tostring-method.md).
- [Definování abstraktních a vlastností](../programming-guide/classes-and-structs/how-to-define-abstract-properties.md).
- [Použití funkcí dokumentace xml do dokumentů kódu](../programming-guide/xmldoc/how-to-use-the-xml-documentation-features.md).
- [Explicitní implementace členů rozhraní](../programming-guide/interfaces/how-to-explicitly-implement-interface-members.md) zachovat stručným veřejné rozhraní.
- [Explicitní implementace členů dvou rozhraní](../programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md).

### <a name="working-with-collections"></a>Práce s kolekcí

Tyto články vám pomohou při práci s kolekcí dat.

- [Inicializace slovníku pomocí inicializátoru kolekce](../programming-guide/classes-and-structs/how-to-initialize-a-dictionary-with-a-collection-initializer.md).
- [Přístup k všechny elementy v kolekci pomocí `foreach` ](../programming-guide/classes-and-structs/how-to-access-a-collection-class-with-foreach.md).

## <a name="strings"></a>řetězce

Řetězce jsou základní datový typ používaný můžete zobrazit nebo upravit text. Tyto články ukazují obvyklé postupy s řetězci.

- [Porovnávání řetězců](../programming-guide/strings/how-to-compare-strings.md).
- [Změna obsahu řetězce](../programming-guide/strings/how-to-modify-string-contents.md).
- [Určení, pokud řetězec reprezentuje číslo](../programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md).
- [Použití <xref:System.String.Split%2A> k oddělení řetězců](../programming-guide/strings/how-to-parse-strings-using-string-split.md).
- [Sloučit více řetězce do jednoho](../programming-guide/strings/how-to-concatenate-multiple-strings.md).
- [Hledání textu v řetězci](../programming-guide/strings/how-to-search-strings-using-string-methods.md).
- [Vyhledávání řetězců pomocí regulárních výrazů](../programming-guide/strings/how-to-search-strings-using-regular-expressions.md).

## <a name="convert-between-types"></a>Převod mezi typy

Musíte převést na jiný typ objektu.

- [Určení, pokud řetězec reprezentuje číslo](../programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md).
- [Převod mezi řetězci, které představují hexadecimální číslice a číslo](../programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md).
- [Převést řetězec na <xref:System.DateTime> ](../programming-guide/strings/how-to-convert-a-string-to-a-datetime.md).
- [Převedení pole bajtů na typ int](../programming-guide/types/how-to-convert-a-byte-array-to-an-int.md).
- [Převést řetězec na číslo](../programming-guide/types/how-to-convert-a-string-to-a-number.md).
- [Použití `as` a `is` bezpečně přetypovat na jiný typ](../programming-guide/types/how-to-safely-cast-by-using-as-and-is-operators.md).
- [Operátory převodu pro definování `struct` typy](../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md).
- [Určit, zda typ je typ s možnou hodnotou Null hodnoty](../programming-guide/nullable-types/how-to-identify-a-nullable-type.md).
- [Převod mezi typy hodnot neumožňující hodnotu Null a s povolenou hodnotou Null](../programming-guide/nullable-types/how-to-safely-cast-from-bool-to-bool.md).

## <a name="equality-and-ordering-comparisons"></a>Porovnání rovnosti a řazení

Můžete vytvořit typy, které definovat vlastní pravidla pro rovnosti, nebo definujte přirozené řazení mezi objekty daného typu.

- [Testování rovnosti na základě referenční](../programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md).
- [Definování rovnosti na základě hodnoty pro typ](../programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md).

## <a name="exception-handling"></a>Zpracování výjimek

Programy rozhraní .NET hlásit, že metody nebyla úspěšně dokončena práci vyvoláním výjimek. V těchto článcích získáte informace pro práci s výjimkami.

- [Zpracování výjimek pomocí `try` a `catch` ](../programming-guide/exceptions/how-to-handle-an-exception-using-try-catch.md).
- [Vyčištění prostředků pomocí `finally` klauzule](../programming-guide/exceptions/how-to-execute-cleanup-code-using-finally.md).
- [Obnovit z jiných se specifikací CLS (Common Language Specification) výjimek](../programming-guide/exceptions/how-to-catch-a-non-cls-exception.md).

## <a name="delegates-and-events"></a>Delegáti a události

Delegáti a události poskytují funkce pro strategií, které zahrnují volně doplněná bloky kódu.

- [Deklarování, vytváření instancí a používání delegátů](../programming-guide/delegates/how-to-declare-instantiate-and-use-a-delegate.md).
- [Kombinování delegátů vícesměrového vysílání](../programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md).

Události poskytují mechanismus k publikování nebo přihlášení k odběru oznámení.

- [Přihlášení k odběru a odhlášení odběru událostí](../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).
- [Implementovat události deklarované v rozhraní](../programming-guide/events/how-to-implement-interface-events.md).
- [V souladu s pokyny pro rozhraní .NET Framework při kód publikuje události](../programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md).
- [Vyvolávání událostí definovaných v základní třídy z odvozené třídy](../programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md).
- [Ukládání instancí událostí ve slovníku](../programming-guide/events/how-to-use-a-dictionary-to-store-event-instances.md).
- [Implementace vlastních přístupových objektů událostí](../programming-guide/events/how-to-implement-custom-event-accessors.md).

## <a name="linq-practices"></a>Postupy LINQ

LINQ umožňuje napsat kód pro dotaz na libovolný zdroj dat, která podporuje vzor výrazu dotazu LINQ. Tyto články vám pomůžou pochopit vzoru a pracovat s různými datovými zdroji.

- [Dotazování na kolekci](../programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md).
- [Použití výrazů lambda v dotazu](../programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-in-a-query.md).
- [Použití `var` ve výrazech dotazů](../programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).
- [Vrácení podmnožin vlastností elementu z dotazu](../programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md).
- [Zápis dotazů s komplexní filtrování](../programming-guide/concepts/linq/how-to-write-queries-with-complex-filtering.md).
- [Řazení elementů zdroje dat](../programming-guide/concepts/linq/how-to-sort-elements.md).
- [Řazení elementů na více klíčů](../programming-guide/concepts/linq/how-to-sort-elements-on-multiple-keys.md).
- [Řízení typu projekce](../programming-guide/concepts/linq/how-to-control-the-type-of-a-projection.md).
- [Počet výskytů hodnoty ve zdrojové sekvence](../programming-guide/concepts/linq/how-to-count-occurrences-of-a-word-in-a-string-linq.md).
- [Výpočtu pomocných hodnot](../programming-guide/concepts/linq/how-to-calculate-intermediate-values.md).
- [Slučování dat z více zdrojů](../programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md).
- [Hledání množinových rozdílů mezi dvěma pořadí](../programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md).
- [Ladění výsledky dotazu prázdný](../programming-guide/concepts/linq/how-to-debug-empty-query-results-sets.md).
- [Přidání vlastních metod do dotazů LINQ](../programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md).

## <a name="multiple-threads-and-async-processing"></a>Více vláken a asynchronní zpracování

Moderní programy často používají asynchronní operace. Tyto články vám pomůže naučit se používat tyto postupy.

- [Zlepšení asynchronní výkonu pomocí `System.Threading.Tasks.Task.WhenAll` ](../programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).
- [Provádění vícenásobných webových dotazů pomocí paralelní `async` a `await` ](../programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md).
- [Použití fondu vláken](../programming-guide/concepts/threading/how-to-use-a-thread-pool.md).

## <a name="command-line-args-to-your-program"></a>Argumentů příkazového řádku pro program

Programy C# obvykle mají argumenty příkazového řádku. Tyto články naučit, abyste přístup a zpracování těchto argumentů příkazového řádku.

- [Načíst všechny argumenty příkazového řádku s `for` ](../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md).
- [Načíst všechny argumenty příkazového řádku s `foreach` ](../programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md).
