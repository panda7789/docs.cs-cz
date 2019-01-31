---
title: Jaký operační systém mají cílit kontejnery .NET
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Jaký operační systém mají cílit kontejnery .NET
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: bef268a180584c47486a16960ca13fd63201fbe2
ms.sourcegitcommit: dcc8feeff4718664087747529638ec9b47e65234
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/31/2019
ms.locfileid: "55479864"
---
# <a name="what-os-to-target-with-net-containers"></a>Jaký operační systém mají cílit kontejnery .NET

Zadaný spektrum operačních systémech podporovaných produktem rozdíly mezi rozhraní .NET Framework a .NET Core a Docker, by měl cíl konkrétní operační systém a konkrétní verze v závislosti na rozhraní, které používáte.

Pro Windows můžete použít Windows Server Core nebo Windows Nano Server. Tyto verze Windows poskytují různé vlastnosti (služba IIS v systému Windows Server Core a v místním prostředí webového serveru, jako Kestrel na Nano serveru), které může být potřeba pomocí rozhraní .NET Framework nebo .NET Core.

Více distribuce pro Linux, jsou dostupné a podporované v oficiální Image .NET Dockeru (např. Debian).

Obrázek 3-1 se zobrazí možné verze operačního systému v závislosti na rozhraní .NET framework používá.

![Při nasazování starších aplikací rozhraní .NET Framework, které máte na cílová jádra serveru systému Windows, kompatibilní s starší verze aplikace a služby IIS, má větší obrázek. Při nasazování aplikací .NET Core, můžete směrovat Windows Nano Server, což je cloudové prostředí, používá Kestrel a je menší a spouští rychleji. Můžete také směrovat Linux podporuje Debian, nástroj Alpine a další. Také používá Kestrel a je menší a spouští rychleji.](./media/image1.png)

**Obrázek 3-1.** Operační systémy pro cílení v závislosti na verzi rozhraní .NET framework

Můžete také vytvořit vlastní image Dockeru v případech, ve které chcete použít jiné distribuce Linuxu nebo místo bitovou kopii s verzemi, které neposkytuje Microsoft. Například může vytvořit bitovou kopii s ASP.NET Core využívající tradiční rozhraní .NET Framework a Windows Server Core, který je not tak běžné scénáře pro Docker.

Když přidáte název bitové kopie do souboru Dockerfile, můžete vybrat operační systém a verze v závislosti na značku, kterou používáte, stejně jako v následujících příkladech:

<table>
<thead>
<tr class="header">
<th>Image</th>
<th>Komentáře</th>
</tr>
</thead>
<tbody>
<tr>
<td>Microsoft / dotnet:2.2 – modul runtime</td>
<td>Více architektury .NET core 2.2: Podporuje Linux a Windows Nano serveru v závislosti na hostitele Dockeru.</td>
</tr>
<tr class="odd">
<td>Microsoft / dotnet:2.2-aspnetcore-modulu runtime</td>
<td><p>Architektura ASP.NET Core 2.2 více: Podporuje Linux a Windows Nano serveru v závislosti na hostitele Dockeru.</p>
<p>Aspnetcore image má několik optimalizací pro ASP.NET Core.</p></td>
</tr>
<tr class="even">
<td>Microsoft / dotnet:2.2-aspnetcore-runtime – alpine</td>
<td>.NET core 2.2 pouze modul runtime na Alpine distribuce Linuxu</td>
</tr>
<tr class="odd">
<td>microsoft/dotnet:2.2-aspnetcore-runtime-nanoserver-1803</td>
<td>.NET core 2.2 pouze modul runtime Windows Nano Server (Windows Server verze 1803)</td>
</tr>
</tbody>
</table>

>[!div class="step-by-step"]
>[Předchozí](container-framework-choice-factors.md)
>[další](official-net-docker-images.md)