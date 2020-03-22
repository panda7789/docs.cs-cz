---
title: Jazykové návody
description: Podrobné pokyny pro běžné scénáře ve vývoji jazyka Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, walkthroughs
- examples [Visual Basic]
- Visual Basic code, walkthroughs
- walkthroughs [Visual Basic]
ms.assetid: e4e1f849-e1ce-4cf7-8483-d9b4c4887a8e
ms.openlocfilehash: 76f9b428bc5f613296e24d893f49f124bb13c089
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75636039"
---
# <a name="visual-basic-language-walkthroughs"></a>Návody pro jazyk Visual Basic

Návody poskytují podrobné pokyny pro běžné scénáře, což z nich dělá dobré místo pro zahájení učení o produktu nebo konkrétní oblasti funkcí.

- [Psaní asynchronního programu](./programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 Ukazuje, jak vytvořit asynchronní řešení pomocí [Async](language-reference/modifiers/async.md) a [Await](language-reference/operators/await-operator.md).

- [Deklarace a vyvolávání událostí](programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)  
 Ukazuje, jak jsou události deklarovány a vyvolány v jazyce Visual Basic.

- [Zpracování událostí](programming-guide/language-features/events/walkthrough-handling-events.md)  
 Ukazuje, jak zpracovat události `WithEvents` pomocí standardního klíčového slova nebo nových `AddHandler` / `RemoveHandler` klíčových slov.

- [Vytváření a implementace rozhraní](programming-guide/language-features/interfaces/walkthrough-creating-and-implementing-interfaces.md)  
 Ukazuje, jak jsou deklarovány a implementovány rozhraní v jazyce Visual Basic.

- [Definování tříd](programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)  
 Popisuje, jak deklarovat třídu a její pole, vlastnosti, metody a události.

- [Psaní dotazů v jazyce Visual Basic](programming-guide/concepts/linq/walkthrough-writing-queries.md)  
 Ukazuje, jak můžete pomocí funkcí jazyka Visual Basic psát výrazy dotazu linq (Language Integrated Query).

- [Implementace iEnumerable(Of T) v jazyce Visual Basic](programming-guide/language-features/control-flow/walkthrough-implementing-ienumerable-of-t.md)  
 Ukazuje, jak vytvořit třídu, `IEnumerable(Of String)` která implementuje rozhraní `IEnumerator(Of String)` a třídu, která implementuje rozhraní číst textový soubor po jednom řádku.

- [Volání oken Windows API](programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 Vysvětluje, jak `Declare` používat příkazy a volat windows api. Obsahuje informace o použití atributů pro zařazování řízení pro volání rozhraní API a jak vystavit volání rozhraní API jako metodu třídy.

- [Vytváření objektů MODELU COM pomocí jazyka Visual Basic](programming-guide/com-interop/walkthrough-creating-com-objects.md)  
 Ukazuje, jak vytvořit objekty MODELU COM v jazyce Visual Basic, a to jak se šablonou třídy COM, tak bez ní.

- [Implementace dědičnosti s objekty COM](programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 Ukazuje, jak pomocí jazyka 6.0 vytvořit objekt COM obsahující třídu a potom ji použít jako základní třídu v jazyce Visual Basic.

- [Zjištění, kam objekt My.Application.Log zapisuje informace](developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)  
 Popisuje výchozí `My.Application.Log` nastavení a způsob určení nastavení aplikace.

- [Změna místa, kam objekt My.Application.Log zapisuje informace](developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)  
 Ukazuje, jak přepsat `My.Application.Log` výchozí `My.Log` a nastavení pro protokolování informací o událostech a `Log` způsobit, že objekt zapisovat do jiných posluchačů protokolu.

- [Filtrování výstupu My.Application.Log](developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)  
 Ukazuje, jak změnit výchozí filtrování protokolu `My.Application.Log` pro objekt.

- [Vytváření vlastních součástí naslouchajících protokolům](developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)  
 Ukazuje, jak vytvořit vlastní naslouchací proces protokolu `My.Application.Log` a nakonfigurovat jej tak, aby poslouchat výstup objektu.

- [Vložení typů ze spravovaných sestavení](../standard/assembly/embed-types-visual-studio.md)  
 Popisuje, jak vytvořit sestavení a klientský program, který z něj vloží typy.

- [Ověření, že hesla jsou složitá (Visual Basic)](programming-guide/language-features/strings/walkthrough-validating-that-passwords-are-complex.md)  
 Ukazuje, jak zkontrolovat vlastnosti silného hesla a aktualizovat parametr řetězce s informacemi o tom, které kontroly hesla se nezdaří.

- [Šifrování a dešifrování řetězců v jazyce Visual Basic](programming-guide/language-features/strings/walkthrough-encrypting-and-decrypting-strings.md)  
 Ukazuje, jak <xref:System.Security.Cryptography.DESCryptoServiceProvider> použít třídu k šifrování a dešifrování řetězců.

- [Manipulace se soubory a složkami v jazyce Visual Basic](developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 Ukazuje, jak pomocí funkcí jazyka používat informace o souboru, hledání řetězce v souboru a zápis u souboru.

- [Manipulace se soubory pomocí metod rozhraní .NET Framework](developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)  
 Ukazuje, jak pomocí metod rozhraní .NET Framework určit informace o souboru, vyhledat řetězec v souboru a zapsat do souboru.

- [Trvalé uchování objektu v jazyce Visual Basic](programming-guide/concepts/serialization/walkthrough-persisting-an-object-in-visual-studio.md)  
 Ukazuje, jak vytvořit jednoduchý objekt a zachovat jeho data do souboru.

- [Návod: Podpora včasného testování s funkcí Generování před využitím](/visualstudio/ide/walkthrough-test-first-support-with-the-generate-from-usage-feature)  
 Ukazuje, jak provést vývoj první test, ve kterém nejprve napíšete testy částí a pak napíšete zdrojový kód, aby byly testy úspěšné.
