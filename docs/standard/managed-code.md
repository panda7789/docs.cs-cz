---
title: Co je spravovaný kód?
description: Zjistěte, jak je spravovaný kód kód, jehož spuštění je spravováno za běhu, clr (Common Language Runtime).
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 20bb7ea8-192e-4a96-8ef3-e10e1950fd3d
ms.openlocfilehash: 9133859bd9c999e076effcf0d4d631c59db02f33
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "61910114"
---
# <a name="what-is-managed-code"></a>Co je spravovaný kód?

Při práci s rozhraním .NET Framework se často setkáte s termínem "spravovaný kód". Tento dokument vysvětlí, co tento termín znamená, a další informace kolem něj.

Zjednodušeně řečeno velmi jednoduše, spravovaný kód je právě to: kód, jehož spuštění je spravováno za běhu. V tomto případě se daný čas runtime nazývá **Cltime common language runtime** nebo CLR, bez ohledu na implementaci ([Mono](https://www.mono-project.com/) nebo .NET Framework nebo .NET Core). CLR má na starosti převzetí spravovaného kódu, jeho kompilaci do strojového kódu a jeho následné spuštění. Kromě toho runtime poskytuje několik důležitých služeb, jako je automatická správa paměti, hranice zabezpečení, bezpečnost typů atd.

Porovnejte to se způsobem, jakým byste spustit c/c++ program, také volal "nespravovaný kód". V neřízeném světě má programátor na starosti téměř všechno. Skutečný program je v podstatě binární soubor, který operační systém (OS) načte do paměti a spustí. Vše ostatní, od správy paměti až po bezpečnostní aspekty, jsou zátěží programátora.

Spravovaný kód je napsán v jednom z jazyků vysoké úrovně, které lze spustit v horní části rozhraní .NET, například C#, Visual Basic, F# a další. Při kompilaci kódu napsaného v těchto jazycích s jejich příslušný kompilátor, nezískáte strojový kód. Získáte **zprostředkující kód jazyka,** který runtime pak zkompiluje a spustí. C++ je jedinou výjimkou z tohoto pravidla, protože může také vytvářet nativní, nespravované binární soubory spuštěné v systému Windows.

## <a name="intermediate-language--execution"></a>Provedení zprostředkujícího jazyka &

Co je "zprostředkující jazyk" (zkráceně IL)? Jedná se o produkt kompilace kódu napsaného v jazycích .NET vysoké úrovně. Jakmile zkompilujete kód napsaný v jednom z těchto jazyků, získáte binární soubor, který je vyroben z IL. Je důležité si uvědomit, že IL je nezávislý na jakémkoli konkrétním jazyce, který běží nad runtime; tam je dokonce samostatná specifikace pro to, že si můžete přečíst, pokud jste tak nakloněný.

Jakmile vytvoříte IL z kódu vysoké úrovně, budete s největší pravděpodobností chtít spustit. Toto je místo, kde CLR převezme a spustí proces kompilace **Just-In-Time** nebo **JIT-ing** váš kód z IL do strojového kódu, který lze skutečně spustit na procesoru. Tímto způsobem CLR přesně ví, co váš kód dělá a může efektivně _spravovat._

Zprostředkující jazyk se někdy také nazývá společný zprostředkující jazyk (CIL) nebo Microsoft Intermediate Language (MSIL).

## <a name="unmanaged-code-interoperability"></a>Nespravovaná spolupráce kódu

Samozřejmě, CLR umožňuje předávání hranic mezi spravované a nespravované svět, a tam je hodně kódu, který dělá, že i v [knihovnách základní třídy](framework-libraries.md). To se nazývá **interoperabilita** nebo jen **interop** pro krátké. Tato ustanovení by vám například umožnila zabalit nespravovanou knihovnu a zavolat do ní. Je však důležité si uvědomit, že jakmile to uděláte, když kód přejde hranice runtime, skutečná správa provádění je opět v rukou nespravovaného kódu, a proto spadá pod stejná omezení.

Podobně jako to C# je jeden jazyk, který umožňuje používat nespravované konstrukce, jako jsou ukazatele přímo v kódu s využitím co je známé jako **nebezpečný kontext,** který určuje část kódu, pro které provádění není spravovánclr.

## <a name="more-resources"></a>Další zdroje informací

* [Přehled rozhraní .NET Framework](../framework/get-started/overview.md)
* [Nebezpečný kód a ukazatele](../../docs/csharp/programming-guide/unsafe-code-pointers/index.md)
* [Nativní interoperabilita](./native-interop/index.md)
