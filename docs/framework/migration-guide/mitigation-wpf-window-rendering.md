---
title: 'Omezení rizik: Vykreslování oken ve WPF'
ms.date: 03/30/2017
ms.assetid: 28ed6bf8-141b-4b73-a4e3-44a99fae5084
ms.openlocfilehash: 42d6abf1ba6ed7c17a5a5604e98b5ee46d0c3ac2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457765"
---
# <a name="mitigation-wpf-window-rendering"></a>Omezení rizik: Vykreslování oken ve WPF

V rozhraní .NET Framework 4.6 spuštěné v systému Windows 8 a vyšší, celé okno je vykreslen bez oříznutí, když rozšiřuje mimo jeden displej ve scénáři více monitorů.

## <a name="impact"></a>Dopad

Obecně platí vykreslování celé okno přes více monitorů bez oříznutí je očekávané chování. Však v systému Windows 7 a starší verze WPF okna jsou oříznuty, pokud přesahují jeden displej, protože vykreslování část okna na druhém monitoru má významný vliv na výkon.

Přesný dopad vykreslování wpf oken napříč monitory v systému Windows 8 a vyšším není přesně kvantifikovatelný, protože závisí na velkém počtu faktorů. V některých případech může stále mít nežádoucí dopad na výkon, zejména pro uživatele, kteří spouštějí aplikace náročné na grafiku a mají windows tažné monitory. V ostatních případech můžete jednoduše chtít konzistentní chování napříč verzemi rozhraní .NET Framework.

## <a name="mitigation"></a>Omezení rizik

Tuto změnu můžete zakázat a vrátit se k předchozímu chování oříznutí okna WPF, pokud přesahuje jedno zobrazení. Toto lze provést dvěma způsoby:

- Přidáním `<EnableMultiMonitorDisplayClipping>` prvku do `<appSettings>` části konfiguračního souboru aplikace můžete toto chování zakázat nebo povolit v aplikacích spuštěných ve Windows 8 nebo novějším. Například následující konfigurační část zakáže vykreslování bez oříznutí:

  ```xml
  <appSettings>
      <add key="EnableMultiMonitorDisplayClipping" value="true"/>
    </appSettings>
  ```

  Nastavení `<EnableMultiMonitorDisplayClipping>` konfigurace může mít jednu ze dvou hodnot:

  - `true`, aby oříznutí oken monitorovalo hranice během vykreslování.

  - `false`, chcete-li zakázat oříznutí oken pro sledování hranic během vykreslování.

- Nastavením <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> vlastnosti `true` při spuštění aplikace.

## <a name="see-also"></a>Viz také

- [Kompatibilita aplikací](application-compatibility.md)
