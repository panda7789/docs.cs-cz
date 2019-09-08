---
title: Zmírnění Vykreslování oken WPF
ms.date: 03/30/2017
ms.assetid: 28ed6bf8-141b-4b73-a4e3-44a99fae5084
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13091c06561da24d2fc03f810fd8b8687b21d9a4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70789789"
---
# <a name="mitigation-wpf-window-rendering"></a>Zmírnění Vykreslování oken WPF

V .NET Framework 4,6 spuštěném v systému Windows 8 a vyšším se celé okno vykreslí bez oříznutí, když se v případě více monitorů rozšíří mimo jeden displej.

## <a name="impact"></a>Dopad

Obecně platí, že vykreslování celého okna napříč několika monitory bez oříznutí je očekávané chování. V systému Windows 7 a starších verzích se však okna WPF zobrazují, když přesahují rámec jednoho zobrazení, protože vykreslování části okna na druhém monitoru má významný dopad na výkon.

Přesný dopad vykreslování oken WPF napříč monitory ve Windows 8 a novějším není přesně kvantifikovaný, protože závisí na velkém počtu faktorů. V některých případech může stále dodávat nežádoucí dopad na výkon, zejména pro uživatele, kteří spouštějí aplikace náročné na grafiku a mají monitory s podporou systému Windows. V jiných případech může být jednoduché chování v různých .NET Framework verzích.

## <a name="mitigation"></a>Zmírnění

Tuto změnu můžete zakázat a vrátit se k předchozímu chování při vystřihování okna WPF, když se rozšíří nad rámec jednoho zobrazení. Toto lze provést dvěma způsoby:

- Přidáním `<EnableMultiMonitorDisplayClipping>` elementu`<appSettings>` do oddílu konfiguračního souboru aplikace můžete toto chování zakázat nebo povolit pro aplikace spuštěné v systému Windows 8 nebo novějším. Například následující konfigurační oddíl zakáže vykreslování bez omezení:

  ```xml
  <appSettings>
      <add key="EnableMultiMonitorDisplayClipping" value="true"/>
    </appSettings>
  ```

  Nastavení `<EnableMultiMonitorDisplayClipping>` konfigurace může mít jednu ze dvou hodnot:

  - `true`, aby při vykreslování bylo umožněno oříznutí oken sledovat hranice.

  - `false`, chcete-li zakázat oříznutí oken ke sledování hranic během vykreslování.

- Nastavením vlastnosti na `true` při spuštění aplikace. <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A>

## <a name="see-also"></a>Viz také:

- [Změny v modulu runtime](runtime-changes-in-the-net-framework-4-6.md)
