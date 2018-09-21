---
title: Rozhodovací tabulky. Rozhraní .NET Framework pro Docker
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Tabulka rozhodnutí, rozhraní .NET Framework pro Docker
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/11/2018
ms.openlocfilehash: 74b3749077fdb375f84ddacd98221aa4afcf2f67
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2018
ms.locfileid: "46477987"
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a>Tabulka rozhodnutí: rozhraní .NET Framework pro Docker

Následující rozhodnutí tabulka shrnuje, jestli chcete používat rozhraní .NET Framework nebo .NET Core. Nezapomeňte, že pro kontejnery Linuxu, budete potřebovat hostitele Dockeru založených na Linuxu (virtuální počítače nebo servery) a že pro kontejnery Windows je třeba Windows Server na základě hostitelů Docker (virtuální počítače nebo servery).

> [!IMPORTANT]
> Vaše vývojové počítače spustí jednoho hostitele Docker, Linux nebo Windows. Související mikroslužeb, kterou chcete spustit a otestovat společně v jednom řešení bude nutné ke spuštění v rámci téže platformy kontejneru.

<table>
<thead>
<tr class="header">
<th><strong>Architektura / typ aplikace</strong></th>
<th><strong>Kontejnery Linuxu</strong></th>
<th><strong>Kontejnery Windows</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Mikroslužby v kontejnerech</td>
<td>.NET Core</td>
<td>.NET Core</td>
</tr>
<tr class="even">
<td>Monolitické aplikace</td>
<td>.NET Core</td>
<td><p>.NET Framework</p>
<p>.NET Core</p></td>
</tr>
<tr class="odd">
<td>Ve své třídě nejlepší výkon a škálovatelnost</td>
<td>.NET Core</td>
<td>.NET Core</td>
</tr>
<tr class="even">
<td>Migrace starších verzí aplikací ("brown – pole") Windows serveru do kontejnerů</td>
<td>--</td>
<td>.NET Framework</td>
</tr>
<tr class="odd">
<td>Vývoj nových založených na kontejnerech ("zelená pole")</td>
<td>.NET Core</td>
<td>.NET Core</td>
</tr>
<tr class="even">
<td>ASP.NET Core</td>
<td>.NET Core</td>
<td><p>.NET core (doporučeno)</p>
<p>.NET Framework</p></td>
</tr>
<tr class="odd">
<td>ASP.NET 4 (MVC 5, webové rozhraní API 2 a webové formuláře)</td>
<td>--</td>
<td>.NET Framework</td>
</tr>
<tr class="even">
<td>Služby SignalR</td>
<td>.NET core 2.1 nebo vyšší verzi rozhraní .NET</td>
<td><p>.NET Framework</p>
<p>.NET core 2.1 nebo vyšší verzi rozhraní .NET</p></td>
</tr>
<tr class="odd">
<td>WCF, WF a jiné starší verze architektury</td>
<td>WCF v .NET Core (pouze klientské knihovny WCF)</td>
<td><p>.NET Framework</p>
<p>WCF v .NET Core (pouze klientské knihovny WCF)</p></td>
</tr>
<tr class="even">
<td>Spotřeba služeb Azure</td>
<td><p>.NET Core</p>
<p>(případně všech služeb Azure bude poskytovat klientské sady SDK pro .NET Core)</p></td>
<td><p>.NET Framework</p>
<p>.NET Core</p>
<p>(případně všech služeb Azure bude poskytovat klientské sady SDK pro .NET Core)</p></td>
</tr>
</tbody>
</table>

>[!div class="step-by-step"]
[Předchozí](net-framework-container-scenarios.md)
[další](net-container-os-targets.md)
