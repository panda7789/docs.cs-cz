---
ms.openlocfilehash: 3b7309347c643d89a28331c6ef3cac36085a969a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858646"
---
### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a>WPF okna jsou vykreslovány bez oříznutí při vysazení mimo jeden monitor

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.6 spuštěné v systému Windows 8 a vyšší, celé okno je vykreslen bez oříznutí, když rozšiřuje mimo jeden displej ve scénáři více monitorů. To se liší od předchozích verzí rozhraní .NET Framework, které by klip WPF okna, která rozšířena mimo jeden displej.|
|Návrh|Toto chování (zda klip nebo ne) <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> lze <code>&lt;appSettings&gt;</code> explicitně nastavit pomocí prvku v konfiguračním souboru aplikace nebo nastavením <code>EnableMultiMonitorDisplayClipping</code> vlastnosti při spuštění aplikace.|
|Rozsah|Vedlejší|
|Version|4.6|
|Typ|Modul runtime|
