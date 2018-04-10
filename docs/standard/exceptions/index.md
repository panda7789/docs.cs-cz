---
title: Zpracování a generování výjimek
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- exceptions [.NET Framework], handling
- runtime, exceptions
- filtering exceptions
- errors [.NET Framework], exceptions
- exceptions [.NET Framework], throwing
- exceptions [.NET Framework]
- common language runtime, exceptions
ms.assetid: f99a1d29-a2a8-47af-9707-9909f9010735
caps.latest.revision: 16
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 82e314dacc9fb2657a3a7088a928b59d00282a5d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="handling-and-throwing-exceptions-in-net"></a>Zpracování a generování výjimek v rozhraní .NET

Aplikace musí být schopen zpracovávat chyby, ke kterým došlo během provádění konzistentním způsobem. Rozhraní .NET poskytuje model pro oznamování chyb aplikace jednotného: operace .NET označují selhání vyvoláním výjimky.

## <a name="exceptions"></a>Výjimky

Výjimkou je libovolná chyba nebo neočekávanému chování, které se vyskytne provádění programu. Výjimky může být vyvolána z důvodu selhání ve vašem kódu nebo kód, který volání (například sdílené knihovny), prostředky operačního systému není k dispozici, neočekávané podmínky, které modul runtime, zaznamená (například kód, který nemůže být ověřen) a tak dále. Aplikace lze obnovit z některé z těchto podmínek, ale ne od ostatních. I když můžete obnovit z většina výjimky aplikací, nelze obnovit z většina výjimky za běhu.

V rozhraní .NET, je objekt, který dědí z výjimka <xref:System.Exception?displayProperty=nameWithType> třídy. Z oblasti kódu, kde došlo k potížím, je vyvolána výjimka. Výjimka je přidána na zásobník dokud ji zpracovává aplikaci nebo program se ukončí.

## <a name="exceptions-vs-traditional-error-handling-methods"></a>Výjimky oproti tradiční metody zpracování chyb

Obvyklým model zpracování chyb jazyk spoléhali na jazyka jedinečný způsob zjišťování chyb a vyhledání obslužné rutiny pro ně nebo na mechanizmus zpracování chyb v operačním systému. Způsob zpracování výjimek implementuje rozhraní .NET poskytuje následující výhody:

- Výjimka vyvolání a zpracování funguje stejně programovacích jazyků .NET.

- Nevyžaduje žádné konkrétní jazykové syntaxe pro zpracování výjimek, ale umožňuje definovat vlastní syntaxe jednotlivé jazyky.

- Výjimky může být vyvolána napříč proces a i počítač hranice.

- Zpracování výjimek lze přidat do aplikace pro zvýšení spolehlivosti programu.

Výjimky nabízejí výhod oproti jiným metodám oznámení o chybě, jako je například návratové kódy. Selhání nedojde vzhledem k tomu, že pokud je vyvolána výjimka, a nemusíte je zpracovávat, modul runtime ukončí aplikaci. Neplatné hodnoty nepokračujte rozšíří v rámci systému v důsledku kód, který se nepodaří vyhledat návratový kód chyby. 

## <a name="common-exceptions"></a>Běžné výjimky

Následující tabulka uvádí některé běžné výjimky s příklady, co může způsobit.

| Typ výjimky | Základní typ | Popis | Příklad |
| -------------- | --------- | ----------- | ------- |
| <xref:System.Exception> | <xref:System.Object> | Základní třída pro všechny výjimky. | Žádný (použijte třídu odvozenou této výjimky). |
| <xref:System.IndexOutOfRangeException> | <xref:System.Exception> | Vyvolána modulem runtime pouze v případě, že pole je indexovaný nesprávně. | Indexování pole mimo platný rozsah:`arr[arr.Length+1]` |
| <xref:System.NullReferenceException> | <xref:System.Exception> | Vyvolána modulem runtime pouze v případě, že se odkazuje objekt s hodnotou null. | `object o = null; o.ToString();` |
| <xref:System.InvalidOperationException> | <xref:System.Exception> | Vyvolána metodami, když je v neplatném stavu. | Volání metody `Enumerator.GetNext()` po odebrání položky ze zdrojové kolekce. |
| <xref:System.ArgumentException> | <xref:System.Exception> | Základní třída pro všechny výjimky argumentu. | Žádný (použijte třídu odvozenou této výjimky). |
| <xref:System.ArgumentNullException> | <xref:System.Exception> | Vyvolané metody, které neumožňují argumentu mít hodnotu null. | `String s = null; "Calculate".IndexOf (s);` |
| <xref:System.ArgumentOutOfRangeException> | <xref:System.Exception> | Vyvolané metody, které ověřte, zda jsou argumenty v zadaném rozsahu. | `String s = "string"; s.Substring(s.Length+1);` |

## <a name="see-also"></a>Viz také

* [Třída a vlastnosti výjimky](exception-class-and-properties.md)
* [Postupy: Používání bloku Try/Catch k zachycování výjimek](how-to-use-the-try-catch-block-to-catch-exceptions.md)
* [Postupy: Používání specifických výjimek v bloku Catch](how-to-use-specific-exceptions-in-a-catch-block.md)
* [Postupy: Explicitní generování výjimek](how-to-explicitly-throw-exceptions.md)
* [Postupy: Vytváření uživatelsky definovaných výjimek](how-to-create-user-defined-exceptions.md)
* [Používání obslužných rutin uživatelsky filtrovaných výjimek](using-user-filtered-exception-handlers.md)
* [Postupy: Používání bloků Finally](how-to-use-finally-blocks.md)
* [Zpracování výjimek vzájemné spolupráce COM](handling-com-interop-exceptions.md)
* [Doporučené postupy pro výjimky](best-practices-for-exceptions.md)

Další informace o fungování výjimek v rozhraní .NET najdete v tématu [každých Dev co potřebujete vědět o výjimky v modulu Runtime](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/exceptions.md).
