---
title: Tabulka rozhodnutí Rozhraní .NET Framework, která se mají použít pro Docker
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Tabulka rozhodnutí, rozhraní .NET Framework, které se má použít pro Docker
ms.date: 09/11/2018
ms.openlocfilehash: 96b2750e52d64b06444b7f87dea624879f37d3d7
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296534"
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a>Tabulka rozhodnutí: Rozhraní .NET Framework, která se mají použít pro Docker

Následující rozhodovací tabulka shrnuje, jestli se má použít .NET Framework nebo .NET Core. Pamatujte na to, že pro kontejnery Linux potřebujete hostitele Docker (virtuální počítače nebo servery) založené na systému Linux a to pro kontejnery Windows, které potřebujete pro hostitele Docker (virtuální počítače nebo servery) založené na Windows serveru.

> [!IMPORTANT]
> Ve vývojových počítačích se spustí jeden hostitel Docker, buď Linux nebo Windows. Související mikroslužby, které chcete spustit a testovat společně v jednom řešení, je potřeba spustit na stejné platformě kontejneru.

<table>
<thead>
<tr class="header">
<th><strong>Architektura/typ aplikace</strong></th>
<th><strong>Kontejnery Linuxu</strong></th>
<th><strong>Kontejnery Windows</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Mikroslužby na kontejnerech</td>
<td>.NET Core</td>
<td>.NET Core</td>
</tr>
<tr class="even">
<td>Aplikace monolitické</td>
<td>.NET Core</td>
<td><p>.NET Framework</p>
<p>.NET Core</p></td>
</tr>
<tr class="odd">
<td>Nejlepší výkon a škálovatelnost ve své třídě</td>
<td>.NET Core</td>
<td>.NET Core</td>
</tr>
<tr class="even">
<td>Migrace do kontejnerů starší verze aplikace ("hnědá-Field") Windows serveru</td>
<td>--</td>
<td>.NET Framework</td>
</tr>
<tr class="odd">
<td>Nový vývoj založený na kontejneru (zelená-Field)</td>
<td>.NET Core</td>
<td>.NET Core</td>
</tr>
<tr class="even">
<td>ASP.NET Core</td>
<td>.NET Core</td>
<td><p>.NET Core (doporučeno)</p>
<p>.NET Framework</p></td>
</tr>
<tr class="odd">
<td>ASP.NET 4 (MVC 5, webové rozhraní API 2 a webové formuláře)</td>
<td>--</td>
<td>.NET Framework</td>
</tr>
<tr class="even">
<td>Služby Signal</td>
<td>Verze .NET Core 2,1 nebo vyšší</td>
<td><p>.NET Framework</p>
<p>Verze .NET Core 2,1 nebo vyšší</p></td>
</tr>
<tr class="odd">
<td>WCF, WF a další starší verze platforem</td>
<td>WCF v .NET Core (jenom knihovna klienta WCF)</td>
<td><p>.NET Framework</p>
<p>WCF v .NET Core (jenom knihovna klienta WCF)</p></td>
</tr>
<tr class="even">
<td>Spotřeba služeb Azure</td>
<td><p>.NET Core</p>
<p>(nakonec všechny služby Azure budou poskytovat klientské sady SDK pro .NET Core)</p></td>
<td><p>.NET Framework</p>
<p>.NET Core</p>
<p>(nakonec všechny služby Azure budou poskytovat klientské sady SDK pro .NET Core)</p></td>
</tr>
</tbody>
</table>

>[!div class="step-by-step"]
>[Předchozí](net-framework-container-scenarios.md)Další
>[](net-container-os-targets.md)
