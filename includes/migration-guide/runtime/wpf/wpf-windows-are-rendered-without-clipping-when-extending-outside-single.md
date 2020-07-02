---
ms.openlocfilehash: d276e2bbf24c8b2389a0a8078c62c327c3729d50
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621157"
---
### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a>Okna WPF se vykreslují bez oříznutí, když se rozšíří mimo jeden monitor.

#### <a name="details"></a>Podrobnosti

V .NET Framework 4,6 spuštěném v systému Windows 8 a vyšším se celé okno vykreslí bez oříznutí, když se v případě více monitorů rozšíří mimo jeden displej. To se liší od předchozích verzí .NET Framework, které by mohly oříznout okna WPF, která přesahují rámec jednoho zobrazení.

#### <a name="suggestion"></a>Návrh

Toto chování (bez ohledu na to, jestli se má oříznout), je možné explicitně nastavit pomocí <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> elementu v <code>&lt;appSettings&gt;</code> konfiguračním souboru aplikace nebo nastavením <code>EnableMultiMonitorDisplayClipping</code> vlastnosti při spuštění aplikace.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.6|
|Typ|Modul runtime|
