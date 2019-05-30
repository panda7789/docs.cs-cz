---
title: 'Omezení rizik: Vykreslování oken ve WPF'
ms.date: 03/30/2017
ms.assetid: 28ed6bf8-141b-4b73-a4e3-44a99fae5084
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ecf951ecb955a6597757387de1119267ebc58fdc
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301453"
---
# <a name="mitigation-wpf-window-rendering"></a>Omezení rizik: Vykreslování oken ve WPF

V rozhraní .NET Framework 4.6 spuštěné v systému Windows 8 a vyšším, je vykreslen celé okno bez oříznutí při rozšiřuje mimo jednotné zobrazení v případě více monitorů.

## <a name="impact"></a>Dopad

Obecně platí vykreslování celé okno bez oříznutí víc monitorů je očekávané chování. Ve Windows 7 a starších verzích se ale WPF windows oříznut, pokud rozšířit nad rámec jednoho zobrazení protože vykreslování část okna na druhém monitoru mají dopad výkonu.

Přesné dopadu vykreslování WPF windows na monitorech v systému Windows 8 a vyšším není přesně vyčíslitelný, protože závisí na velký počet faktorů. V některých případech ji stále může způsobit nežádoucí vliv na výkon, hlavně pro uživatele, kteří spouštět aplikace náročné na grafiku a mít tažných monitorování systému windows. V ostatních případech můžete jednoduše chtít konzistentní chování ve verzích rozhraní .NET Framework.

## <a name="mitigation"></a>Zmírnění

Můžete zakázat tuto změnu a vrátit k předchozí chování při přesahoval jednotné zobrazení oříznutí okno WPF. Toto lze provést dvěma způsoby:

- Přidáním `<EnableMultiMonitorDisplayClipping>` elementu `<appSettings>` oddílu konfiguračního souboru aplikace, můžete zakázat nebo povolit toto chování na aplikace, které běží v systému Windows 8 nebo novější. Například následující konfigurační oddíl zakáže vykreslování bez omezení:

  ```xml
  <appSettings>
      <add key="EnableMultiMonitorDisplayClipping" value="true"/>
    </appSettings>
  ```

  `<EnableMultiMonitorDisplayClipping>` Nastavení konfigurace může mít jednu ze dvou hodnot:

  - `true`, chcete povolit oříznutí systému windows ke sledování hranice během vykreslování.

  - `false`, chcete-li zakázat systému windows ke sledování hranice během vykreslování.

- Tím, že nastavíte <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> vlastnost `true` při spuštění aplikace.

## <a name="see-also"></a>Viz také:

- [Změny v modulu runtime](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
