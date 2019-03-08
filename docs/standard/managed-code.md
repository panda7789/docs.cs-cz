---
title: Co je spravovaný kód?
description: Zjistěte, jak spravovaný kód je kód, jehož spuštění je spravován modulem runtime, Common Language Runtime (CLR).
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 20bb7ea8-192e-4a96-8ef3-e10e1950fd3d
ms.openlocfilehash: 9133859bd9c999e076effcf0d4d631c59db02f33
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57678755"
---
# <a name="what-is-managed-code"></a>Co je "spravovaného kódu"?

Při práci s rozhraním .NET Framework, můžete často narazit termín "spravovaný kód". Tento dokument vysvětluje, co znamená tento termín a další informace o kolem něj.

Velmi jednoduše řečeno, spravovaný kód je přesně to: kódu, jehož spuštění je spravován modulem runtime, který. V takovém případě se nazývá modul runtime dotyčný **Common Language Runtime** nebo CLR, bez ohledu na implementaci ([Mono](https://www.mono-project.com/) nebo rozhraní .NET Framework nebo .NET Core). Má na starosti trvá spravovaného kódu, kompilaci do strojového kódu a pak její provedení CLR. Nad rámec, modul runtime nabízí několik důležitých služeb, jako je například automatická správa paměti, hranice zabezpečení, typ zabezpečení atd.

Porovnejte to způsobu, jakým by spuštění programu jazyka C/C++, nazývané také "nespravovaného kódu". Nespravované světě programátor má na starosti prakticky vše. Skutečný program je v podstatě binární soubor, který načte do paměti operačního systému (OS) a spustí. Všechno ostatní, ze správy paměti na aspekty zabezpečení jsou zátěž programátorovi.

Spravovaný kód je zapsán některým z vyšší úrovně jazyky, které lze spustit na .NET, jako například C#, Visual Basic, F# a další. Při kompilaci kódu napsaného v těchto jazyků s jejich odpovídajících kompilátoru neobdržíte strojového kódu. Získáte **Intermediate Language** kód, který modul runtime pak zkompiluje a spustí. C++ je jedinou výjimkou tohoto pravidla, jak můžete také vytvářet nativní, nespravované binární soubory, které běží na Windows.

## <a name="intermediate-language--execution"></a>Převodní jazyk & spuštění

Co je "Intermediate Language" (nebo IL pro krátké)? Je produkt kompilace kódu napsané v jazycích .NET, vysoké úrovně. Po kompilaci kódu napsané v jednom z těchto jazyků, se zobrazí binární soubor, který se vytvořil mimo IL. Je důležité si uvědomit, že je nezávislá na konkrétní jazyk, který běží na modulu runtime; IL samostatné specifikace, které si můžete přečíst, pokud jste tak sklon ještě neexistuje.

Po vytvoření IL od kódu vysoké úrovně, bude pravděpodobně chcete spustit. Toto je kde CLR má a spustí proces **Just-In-Time** kompilaci, nebo **JIT-ing** kód z IL do strojového kódu, který ve skutečnosti je možné spustit v Procesorem. Tímto způsobem CLR ví přesně co kód dělá a může efektivně _spravovat_ ho.

Převodní jazyk někdy se také nazývá Common Intermediate Language (CIL) nebo Microsoft Intermediate Language (MSIL).

## <a name="unmanaged-code-interoperability"></a>Interoperabilita s nespravovaným kódem

Samozřejmě, modul CLR umožňuje předání hranic mezi spravovaným a nespravovaným world a dochází k mnoha kód, který činí, dokonce i v [knihovny tříd Base](framework-libraries.md). Tento postup se nazývá **interoperability** nebo jen **interop** pro krátké. Tyto předpisy by umožnilo, například zabalit nespravovaná knihovna a volat do něj. Je však potřeba poznamenat, že jakmile to uděláte, když kód předá hranice modulu runtime, samotnou správu provádění znovu v dolním nespravovaného kódu a proto spadá pod stejné omezení.

Podobně jako tento, C# je jeden jazyk, který umožňuje použití nespravovaných konstrukce, jako je například ukazatele přímo v kódu s využitím, která se označuje jako **nezabezpečený kontext** který udává část kódu, pro který není spravován provádění pomocí modulu CLR.

## <a name="more-resources"></a>Další materiály

* [Přehled rozhraní .NET Framework](../framework/get-started/overview.md)
* [Nebezpečný kód a ukazatele](../../docs/csharp/programming-guide/unsafe-code-pointers/index.md)
* [Nativní interoperabilita](./native-interop/index.md)
