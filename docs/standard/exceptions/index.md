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
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741352"
---
# <a name="handling-and-throwing-exceptions-in-net"></a>Zpracování a vyvolání výjimek v rozhraní .NET

Aplikace musí být schopné zpracovávat chyby, ke kterým dochází během provádění konzistentním způsobem. .NET poskytuje model pro oznamování chyb aplikacím jednotným způsobem: operace .NET indikují selhání vyvoláním výjimek.

## <a name="exceptions"></a>Výjimky

Výjimka je jakýkoli chybový stav nebo neočekávané chování, které se zjistilo spuštěným programem. Výjimky mohou být vyvolány z důvodu chyby ve vašem kódu nebo v kódu, který zavoláte (například sdílená knihovna), nedostupných prostředků operačního systému, neočekávaných podmínek, které modul runtime narazí (například kódu, který nelze ověřit) a tak dále. Vaše aplikace se může zotavit z některých těchto podmínek, ale ne od ostatních. I když můžete zotavit z většiny výjimek aplikace, nemůžete obnovit z většiny běhových výjimek.

V rozhraní .NET je výjimka objektem, který dědí z třídy <xref:System.Exception?displayProperty=nameWithType>. Výjimka je vyvolána z oblasti kódu, kde došlo k problému. Výjimka předává zásobníku, dokud ji aplikace nezpracuje nebo ukončí program.

## <a name="exceptions-vs-traditional-error-handling-methods"></a>Výjimky vs. tradiční metody zpracování chyb

Tradičně se model zpracování chyb jazyka spoléhal buď na jedinečný způsob zjišťování chyb a hledání obslužných rutin pro tyto účely, nebo na mechanismu zpracování chyb poskytovaný operačním systémem. Způsob, jakým rozhraní .NET implementuje zpracování výjimek, poskytuje následující výhody:

- Vyvolání a zpracování výjimky funguje stejně pro programovací jazyky .NET.

- Nevyžaduje žádnou konkrétní jazykovou syntaxi pro zpracování výjimek, ale umožňuje každému jazyku definovat vlastní syntaxi.

- Výjimky mohou být vyvolány napříč procesem a dokonce i na hranicích počítačů.

- Kód pro zpracování výjimek lze přidat do aplikace pro zvýšení spolehlivosti programu.

Výjimky nabízí výhody proti jiným způsobům chybového oznámení, jako jsou například návratové kódy. Selhání nejdou nepatrné, protože pokud je vyvolána výjimka a nezpracováváte ji, modul runtime ukončí vaši aplikaci. Neplatné hodnoty nejsou dále šířeny v systému jako výsledek kódu, který nedokáže vyhledat návratový kód chyby.

## <a name="common-exceptions"></a>Běžné výjimky

V následující tabulce jsou uvedeny některé běžné výjimky s příklady toho, co můžou způsobit.

| Typ výjimky | Popis | Příklad |
| -------------- | ----------- | ------- |
| <xref:System.Exception> | Základní třída pro všechny výjimky. | Žádný (použijte odvozenou třídu této výjimky). |
| <xref:System.IndexOutOfRangeException> | Vyvolána modulem runtime pouze v případě, že je nesprávně indexováno pole | Indexování pole mimo platný rozsah: <br /> `arr[arr.Length+1]` |
| <xref:System.NullReferenceException> | Vyvolána modulem runtime pouze v případě, že je odkazováno na objekt s hodnotou null. | `object o = null;` <br /> `o.ToString();` |
| <xref:System.InvalidOperationException> | Vyvoláno metodami, pokud je v neplatném stavu. | Volání `Enumerator.MoveNext()` po odebrání položky z podkladové kolekce. |
| <xref:System.ArgumentException> | Základní třída pro všechny výjimky argumentů | Žádný (použijte odvozenou třídu této výjimky). |
| <xref:System.ArgumentNullException> | Vyvoláno metodami, které neumožňují, aby argument byl null. | `String s = null;` <br /> `"Calculate".IndexOf(s);`|
| <xref:System.ArgumentOutOfRangeException> | Vyvoláno metodami, které ověřují, zda jsou argumenty v daném rozsahu. | `String s = "string";` <br /> `s.Substring(s.Length+1);` |

## <a name="see-also"></a>Viz také:

- [Třída a vlastnosti výjimky](exception-class-and-properties.md)
- [Postupy: Používání bloku Try/Catch k zachycování výjimek](how-to-use-the-try-catch-block-to-catch-exceptions.md)
- [Postupy: Používání specifických výjimek v bloku Catch](how-to-use-specific-exceptions-in-a-catch-block.md)
- [Postupy: Explicitní generování výjimek](how-to-explicitly-throw-exceptions.md)
- [Postupy: Vytváření uživatelsky definovaných výjimek](how-to-create-user-defined-exceptions.md)
- [Používání obslužných rutin uživatelsky filtrovaných výjimek](using-user-filtered-exception-handlers.md)
- [Postupy: Používání bloků Finally](how-to-use-finally-blocks.md)
- [Zpracování výjimek vzájemné spolupráce COM](handling-com-interop-exceptions.md)
- [Doporučené postupy pro výjimky](best-practices-for-exceptions.md)
- [Co každá z vývoje potřebuje znát o výjimkách v modulu runtime](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/exceptions.md)
