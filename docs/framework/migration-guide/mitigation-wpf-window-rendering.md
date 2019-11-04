---
title: 'Omezení rizik: Vykreslování oken ve WPF'
ms.date: 03/30/2017
ms.assetid: 28ed6bf8-141b-4b73-a4e3-44a99fae5084
ms.openlocfilehash: 42d6abf1ba6ed7c17a5a5604e98b5ee46d0c3ac2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457765"
---
# <a name="mitigation-wpf-window-rendering"></a>Omezení rizik: Vykreslování oken ve WPF

V .NET Framework 4,6 spuštěném v systému Windows 8 a vyšším se celé okno vykreslí bez oříznutí, když se v případě více monitorů rozšíří mimo jeden displej.

## <a name="impact"></a>Dopad

Obecně platí, že vykreslování celého okna napříč několika monitory bez oříznutí je očekávané chování. V systému Windows 7 a starších verzích se však okna WPF zobrazují, když přesahují rámec jednoho zobrazení, protože vykreslování části okna na druhém monitoru má významný dopad na výkon.

Přesný dopad vykreslování oken WPF napříč monitory ve Windows 8 a novějším není přesně kvantifikovaný, protože závisí na velkém počtu faktorů. V některých případech může stále dodávat nežádoucí dopad na výkon, zejména pro uživatele, kteří spouštějí aplikace náročné na grafiku a mají monitory s podporou systému Windows. V jiných případech může být jednoduché chování v různých .NET Framework verzích.

## <a name="mitigation"></a>Zmírnění

Tuto změnu můžete zakázat a vrátit se k předchozímu chování při vystřihování okna WPF, když se rozšíří nad rámec jednoho zobrazení. Toto lze provést dvěma způsoby:

- Přidáním prvku `<EnableMultiMonitorDisplayClipping>` do části `<appSettings>` konfiguračního souboru aplikace můžete toto chování zakázat nebo povolit pro aplikace spuštěné v systému Windows 8 nebo novějším. Například následující konfigurační oddíl zakáže vykreslování bez omezení:

  ```xml
  <appSettings>
      <add key="EnableMultiMonitorDisplayClipping" value="true"/>
    </appSettings>
  ```

  Nastavení konfigurace `<EnableMultiMonitorDisplayClipping>` může mít jednu ze dvou hodnot:

  - `true`, aby bylo možné během vykreslování povolit oříznutí oken k monitorování hranic.

  - `false`, chcete-li zakázat oříznutí oken ke sledování hranic během vykreslování.

- Nastavením vlastnosti <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> na `true` při spuštění aplikace.

## <a name="see-also"></a>Viz také:

- [Kompatibilita aplikací](application-compatibility.md)
