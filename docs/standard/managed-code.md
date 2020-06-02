---
title: Co je spravovaný kód?
description: Přečtěte si, jak spravovaný kód je kód, jehož provádění je spravováno modulem CLR (Common Language Runtime).
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 20bb7ea8-192e-4a96-8ef3-e10e1950fd3d
ms.openlocfilehash: 2d89fd48e4c05dc7ec7c27846a3580ee36b1886f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290081"
---
# <a name="what-is-managed-code"></a>Co je spravovaný kód?

Při práci se .NET Framework se často setkáte s termínem "spravovaný kód". Tento dokument vysvětluje, co tento pojem znamená a jaké jsou další informace.

Aby byl spravovaný kód velmi jednoduchý, je pouze ten, který: kód, jehož spuštění je spravováno modulem runtime. V tomto případě se za modul runtime říká modul CLR ( **Common Language Runtime** ) nebo CLR bez ohledu na implementaci ([mono](https://www.mono-project.com/) nebo .NET Framework nebo .NET Core). CLR má za následek přebírání spravovaného kódu, kompilování do strojového kódu a jeho následné spuštění. Na základě toho modul runtime poskytuje několik důležitých služeb, jako je automatická správa paměti, hranice zabezpečení, bezpečnost typů atd.

Na rozdíl od toho, jak byste spustili program jazyka C/C++, označovaný také jako "nespravovaný kód". V nespravovaném světě je programátor v platně hodně všeho. Skutečný program je v podstatě binární soubor, který operační systém (OS) načte do paměti a spustí se. Všechno ostatní, od správy paměti až po požadavky na zabezpečení, jsou režie programátora.

Spravovaný kód je napsán v jednom z jazyků vysoké úrovně, které lze spustit nad .NET, jako je C#, Visual Basic, F # a dalších. Při kompilaci kódu napsaného v těchto jazycích pomocí příslušného kompilátoru nezískáte kód počítače. Získáte kód **zprostředkujícího jazyka** , který modul runtime pak zkompiluje a spustí. C++ je jedinou výjimkou z tohoto pravidla, protože může také vydávat nativní nespravované binární soubory, které běží ve Windows.

## <a name="intermediate-language--execution"></a>Provádění zprostředkujícího jazyka &

Co je "zprostředkující jazyk" (nebo IL pro krátké)? Jedná se o produktovou kompilaci kódu napsaného v jazycích .NET na vysoké úrovni. Po zkompilování kódu napsaného v jednom z těchto jazyků získáte binární soubor, který se stane z IL. Je důležité si uvědomit, že IL je nezávislý na konkrétním jazyku, který běží nad modulem runtime; pro něj je k dispozici i samostatná specifikace, kterou si můžete přečíst, pokud budete mít na starosti.

Jakmile vytvoříte IL z vašeho kódu na nejvyšší úrovni, pravděpodobně ho budete chtít spustit. To je místo, kde modul CLR přebírá a spouští proces **kompilace za běhu nebo** **JIT** kódu z Il až po strojový kód, který se dá ve skutečnosti spustit na procesoru. Tímto způsobem CLR ví přesně, co váš kód dělá, a může ho efektivně _Spravovat_ .

Zprostředkující jazyk se někdy také označuje jako Common Intermediate Language (CIL) nebo Microsoft Intermediate Language (MSIL).

## <a name="unmanaged-code-interoperability"></a>Interoperabilita nespravovaného kódu

Modul CLR samozřejmě umožňuje předávat hranice mezi spravovaným a nespravovaným světem a existuje velké množství kódu, který provede i v [knihovnách základních tříd](framework-libraries.md). Tato metoda se nazývá **interoperabilita** nebo se jedná o stručnou **spolupráci** . Tato ustanovení vám umožní například zabalit nespravovanou knihovnu a volat do ní. Je však důležité si uvědomit, že jakmile kód přesáhne hranice modulu runtime, je skutečná správa spuštění znovu v rukou nespravovaného kódu, a proto spadá pod stejné omezení.

Podobně jako v jazyce C# je jeden jazyk, který umožňuje používat nespravované konstrukce, jako jsou ukazatele přímo v kódu, pomocí toho, co je známé jako **nezabezpečený kontext** , který určuje část kódu, pro kterou není modul CLR spravován.

## <a name="more-resources"></a>Další zdroje informací

* [Přehled rozhraní .NET Framework](../framework/get-started/overview.md)
* [Nezabezpečený kód a ukazatele](../csharp/programming-guide/unsafe-code-pointers/index.md)
* [Nativní interoperabilita](./native-interop/index.md)
