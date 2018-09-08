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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 263e6394a57ec3e7ef00eb79671d9b8ac47e724f
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44177232"
---
# <a name="handling-and-throwing-exceptions-in-net"></a>Zpracování a vyvolání výjimek v rozhraní .NET

Aplikace musí být schopna zpracovávat chyby, ke kterým dochází při provádění konzistentním způsobem. .NET poskytuje model pro oznamování chyb aplikace jednotným způsobem: operace .NET označení selhání vyvoláním výjimky.

## <a name="exceptions"></a>Výjimky

Výjimka je libovolný chybový stav nebo neočekávané chování, na kterou narazí prováděnému programu. Výjimky mohou být vyvolány z důvodu chyby v kódu nebo v kódu, který voláte (jako jsou sdílené knihovny), prostředky operačního systému není k dispozici, neočekávané podmínky, které modul runtime, zaznamená (například kód, který nelze ověřit) a tak dále. Aplikaci můžete obnovit z některé z těchto podmínek, ale ne od ostatních. I když můžete obnovit z většina výjimek aplikace, nebude možné obnovit z většiny výjimky modulu CLR.

V .NET, je výjimka, která dědí z objektu <xref:System.Exception?displayProperty=nameWithType> třídy. Výjimka je vyvolána z oblasti kódu, kde došlo k problému. Výjimka je předána na vrcholu zásobníku, dokud aplikace zvládne nebo program se ukončí.

## <a name="exceptions-vs-traditional-error-handling-methods"></a>Výjimky vs. tradiční metody zpracování chyb

Tradičně spoléhal jazykový model zpracování chyb jazyka jedinečný způsob zjišťování chyb a vyhledání obslužné rutiny pro ně nebo mechanismus zpracování chyb v operačním systému k dispozici. Způsob zpracování výjimek implementuje .NET nabízí následující výhody:

- Vyvolávání a zpracování výjimek funguje stejně v případě programovacích jazycích rozhraní .NET.

- Nevyžaduje žádnou konkrétní jazykovou syntaxi pro zpracování výjimek, ale umožňuje definovat svou vlastní syntaxi jednotlivé jazyky.

- Výjimky mohou být vyvolány v procesu a dokonce i počítač hranice.

- Kód zpracování výjimek lze přidat do aplikace pro zvýšení spolehlivosti programu.

Výjimky nabízí výhody oproti jiným metodám oznamování chyb, jako je například návratové kódy. Selhání není povšimnutí, protože pokud dojde k výjimce a nechcete ji zpracovat, modul runtime ukončí aplikaci. Neplatné hodnoty není nadále šířit prostřednictvím systému jako výsledek kódu, které se nedaří vyhledat návratový kód chyby.

## <a name="common-exceptions"></a>Běžné výjimky

Následující tabulka uvádí některé běžné výjimky s příklady, co může způsobit.

| Typ výjimky | Popis | Příklad |
| -------------- | ----------- | ------- |
| <xref:System.Exception> | Základní třída pro všechny výjimky. | Žádný (použijte odvozené třídy této výjimky). |
| <xref:System.IndexOutOfRangeException> | Vyvolané modulem runtime jenom v případě, že pole jsou indexována, nesprávně. | Došlo k indexování pole mimo platný rozsah: <br /> `arr[arr.Length+1]` |
| <xref:System.NullReferenceException> | Vyvolané modulem runtime pouze v případě, že se odkazuje objekt s hodnotou null. | `object o = null;` <br /> `o.ToString();` |
| <xref:System.InvalidOperationException> | Vyvolání metody v neplatném stavu. | Volání `Enumerator.MoveNext()` po odebrání položky ze zdrojové kolekce. |
| <xref:System.ArgumentException> | Základní třída pro všechny výjimky argumentu. | Žádný (použijte odvozené třídy této výjimky). |
| <xref:System.ArgumentNullException> | Vyvolání metody, které nepovolují argument mít hodnotu null. | `String s = null;` <br /> `"Calculate".IndexOf(s);`|
| <xref:System.ArgumentOutOfRangeException> | Vyvolání metody, které ověřují, že argumenty jsou v dané oblasti. | `String s = "string";` <br /> `s.Substring(s.Length+1);` |

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
- [Co každých vývoj je potřeba vědět o výjimky v modulu Runtime](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/exceptions.md).
