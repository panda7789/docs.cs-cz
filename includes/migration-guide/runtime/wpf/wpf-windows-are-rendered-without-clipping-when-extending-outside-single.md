---
ms.openlocfilehash: 2e974d277d6659aaada321b2a7e7a604df78a7bd
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858646"
---
### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a>Vykreslení WPF windows bez oříznutí při rozšiřování mimo jednoho monitoru

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.6 spuštěné v systému Windows 8 a vyšším, je vykreslen celé okno bez oříznutí při rozšiřuje mimo jednotné zobrazení v případě více monitorů. Tím se liší od předchozích verzí rozhraní .NET Framework, které by oříznout WPF windows, které rozšířit nad rámec jednoho zobrazení.|
|Doporučení|Toto chování (jestli se má oříznout nebo ne) lze explicitně nastavit pomocí <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> prvek <code>&lt;appSettings&gt;</code> v konfiguračním souboru aplikace nebo tím, že nastavíte <code>EnableMultiMonitorDisplayClipping</code> vlastnost při spuštění aplikace.|
|Scope|Vedlejší|
|Version|4.6|
|type|Modul runtime|

