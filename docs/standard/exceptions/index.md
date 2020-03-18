---
title: Zpracování a vyvolání výjimek v rozhraní .NET
ms.date: 06/19/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions [.NET], handling
- runtime, exceptions
- filtering exceptions
- errors [.NET], exceptions
- exceptions [.NET], throwing
- exceptions [.NET]
- common language runtime, exceptions
ms.assetid: f99a1d29-a2a8-47af-9707-9909f9010735
ms.openlocfilehash: 8e78b2a8d7a815637e143eeb88bcfb51ded33771
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75741352"
---
# <a name="handling-and-throwing-exceptions-in-net"></a>Zpracování a vyvolání výjimek v rozhraní .NET

Aplikace musí být schopen zpracovat chyby, ke kterým dochází během provádění konzistentním způsobem. .NET poskytuje model pro upozorňování aplikací chyb jednotným způsobem: Operace .NET označují selhání vyvoláním výjimek.

## <a name="exceptions"></a>Výjimky

Výjimkou je jakýkoli chybový stav nebo neočekávané chování, ke kterému dochází při spuštění programu. Výjimky mohou být vyvolány z důvodu chyby v kódu nebo v kódu, který voláte (například sdílené knihovny), nedostupné prostředky operačního systému, neočekávané podmínky, které runtime narazí (například kód, který nelze ověřit) a tak dále. Vaše aplikace lze obnovit z některé z těchto podmínek, ale ne z jiných. I když můžete obnovit z většiny výjimek aplikace, nelze obnovit z většiny výjimek runtime.

V rozhraní .NET je výjimka objekt, <xref:System.Exception?displayProperty=nameWithType> který dědí z třídy. Výjimka je vyvolána z oblasti kódu, kde došlo k problému. Výjimka je předána do zásobníku, dokud ji aplikace nezpracuje nebo dokud program neukončí.

## <a name="exceptions-vs-traditional-error-handling-methods"></a>Výjimky vs. tradiční metody zpracování chyb

Model zpracování chyb jazyka tradičně spoléhal na jedinečný způsob zjišťování chyb a vyhledání obslužných rutin jazyka nebo na mechanismus zpracování chyb poskytovaný operačním systémem. Způsob, jakým rozhraní .NET implementuje zpracování výjimek, poskytuje následující výhody:

- Vyvolání a zpracování výjimek funguje stejně pro programovací jazyky .NET.

- Nevyžaduje žádnou syntaxi konkrétního jazyka pro zpracování výjimek, ale umožňuje každému jazyku definovat vlastní syntaxi.

- Výjimky mohou být vyvolány přes hranice procesu a dokonce i počítače.

- Kód zpracování výjimek lze přidat do aplikace pro zvýšení spolehlivosti programu.

Výjimky nabízejí výhody oproti jiným metodám oznámení o chybě, jako jsou například návratové kódy. Chyby nepřecházejí bez povšimnutí, protože pokud je vyvolána výjimka a nezpracováváte ji, runtime ukončí vaši aplikaci. Neplatné hodnoty nebudou nadále šířit prostřednictvím systému v důsledku kódu, který nedokáže zkontrolovat návratový kód selhání.

## <a name="common-exceptions"></a>Běžné výjimky

V následující tabulce jsou uvedeny některé běžné výjimky s příklady toho, co je může způsobit.

| Typ výjimky | Popis | Příklad |
| -------------- | ----------- | ------- |
| <xref:System.Exception> | Základní třída pro všechny výjimky. | Žádné (použijte odvozenou třídu této výjimky). |
| <xref:System.IndexOutOfRangeException> | Vyvolána za běhu pouze v případě, že pole je indexována nesprávně. | Indexování pole mimo jeho platný rozsah: <br /> `arr[arr.Length+1]` |
| <xref:System.NullReferenceException> | Vyvolána za běhu pouze v případě, že je odkazováno na objekt null. | `object o = null;` <br /> `o.ToString();` |
| <xref:System.InvalidOperationException> | Vyvolána metodami v neplatném stavu. | Volání `Enumerator.MoveNext()` po odebrání položky z podkladové kolekce. |
| <xref:System.ArgumentException> | Základní třída pro všechny výjimky argumentů. | Žádné (použijte odvozenou třídu této výjimky). |
| <xref:System.ArgumentNullException> | Vyvolána metodami, které neumožňují argument být null. | `String s = null;` <br /> `"Calculate".IndexOf(s);`|
| <xref:System.ArgumentOutOfRangeException> | Vyvolána metodami, které ověřují, že argumenty jsou v daném rozsahu. | `String s = "string";` <br /> `s.Substring(s.Length+1);` |

## <a name="see-also"></a>Viz také

- [Třída a vlastnosti výjimky](exception-class-and-properties.md)
- [Postupy: Používání bloku Try/Catch k zachycování výjimek](how-to-use-the-try-catch-block-to-catch-exceptions.md)
- [Postupy: Používání specifických výjimek v bloku Catch](how-to-use-specific-exceptions-in-a-catch-block.md)
- [Postupy: Explicitní generování výjimek](how-to-explicitly-throw-exceptions.md)
- [Postupy: Vytváření uživatelsky definovaných výjimek](how-to-create-user-defined-exceptions.md)
- [Používání obslužných rutin uživatelsky filtrovaných výjimek](using-user-filtered-exception-handlers.md)
- [Postupy: Používání bloků Finally](how-to-use-finally-blocks.md)
- [Zpracování výjimek vzájemné spolupráce COM](handling-com-interop-exceptions.md)
- [Doporučené postupy pro výjimky](best-practices-for-exceptions.md)
- [Co každý dev potřebuje vědět o výjimkách v runtime](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/exceptions.md)
