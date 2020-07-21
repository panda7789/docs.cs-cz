---
title: 'Omezení rizik: Vykreslování oken ve WPF'
description: Přečtěte si o dopadu a zmírnění vykreslování oken WPF v .NET Framework 4,6, které běží v systému Windows 8 nebo novějším.
ms.date: 03/30/2017
ms.assetid: 28ed6bf8-141b-4b73-a4e3-44a99fae5084
ms.openlocfilehash: d624478d17a4076107438f71b0a86eeb6d9f3ea4
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475330"
---
# <a name="mitigation-wpf-window-rendering"></a>Omezení rizik: Vykreslování oken ve WPF

V .NET Framework 4,6 spuštěném v systému Windows 8 a vyšším se celé okno vykreslí bez oříznutí, když se v případě více monitorů rozšíří mimo jeden displej.

## <a name="impact"></a>Dopad

Obecně platí, že vykreslování celého okna napříč několika monitory bez oříznutí je očekávané chování. V systému Windows 7 a starších verzích se však okna WPF zobrazují, když přesahují rámec jednoho zobrazení, protože vykreslování části okna na druhém monitoru má významný dopad na výkon.

Přesný dopad vykreslování oken WPF napříč monitory ve Windows 8 a novějším není přesně kvantifikovaný, protože závisí na velkém počtu faktorů. V některých případech může stále dodávat nežádoucí dopad na výkon, zejména pro uživatele, kteří spouštějí aplikace náročné na grafiku a mají monitory s podporou systému Windows. V jiných případech může být jednoduché chování v různých .NET Framework verzích.

## <a name="mitigation"></a>Omezení rizik

Tuto změnu můžete zakázat a vrátit se k předchozímu chování při vystřihování okna WPF, když se rozšíří nad rámec jednoho zobrazení. Toto lze provést dvěma způsoby:

- Přidáním `<EnableMultiMonitorDisplayClipping>` elementu do `<appSettings>` oddílu konfiguračního souboru aplikace můžete toto chování zakázat nebo povolit pro aplikace spuštěné v systému Windows 8 nebo novějším. Například následující konfigurační oddíl zakáže vykreslování bez omezení:

  ```xml
  <appSettings>
      <add key="EnableMultiMonitorDisplayClipping" value="true"/>
    </appSettings>
  ```

  `<EnableMultiMonitorDisplayClipping>`Nastavení konfigurace může mít jednu ze dvou hodnot:

  - `true`, aby při vykreslování bylo umožněno oříznutí oken sledovat hranice.

  - `false`, chcete-li zakázat oříznutí oken ke sledování hranic během vykreslování.

- Nastavením <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> vlastnosti na `true` při spuštění aplikace.

## <a name="see-also"></a>Viz také

- [Kompatibilita aplikací](application-compatibility.md)
