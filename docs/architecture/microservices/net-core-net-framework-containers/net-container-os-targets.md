---
title: Operační systém, na který mají cílit kontejnery .NET
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Na jaký operační systém se má zaměřit pomocí kontejnerů .NET
ms.date: 01/30/2020
ms.openlocfilehash: a09e3981ece478a9795c0f27acc98d604864cdd5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77501866"
---
# <a name="what-os-to-target-with-net-containers"></a>Operační systém, na který mají cílit kontejnery .NET

Vzhledem k rozmanitosti operačních systémů podporovaných dockerem a rozdílům mezi rozhraním .NET Framework a .NET Core byste měli cílit na konkrétní operační systém a konkrétní verze v závislosti na rozhraní, které používáte.

V systému Windows můžete použít Windows Server Core nebo Windows Nano Server. Tyto verze systému Windows poskytují různé charakteristiky (Služba IIS v systému Windows Server Core versus webový server hostovaný samostatně, jako je Kestrel na Nano Serveru), které mohou být potřebné rozhraním .NET Framework nebo .NET Core.

Pro Linux je k dispozici více distribucí a podporováno v oficiálních obrázcích .NET Docker (jako debian).

Na obrázku 3-1 můžete vidět možnou verzi operačního systému v závislosti na použitém rozhraní .NET.

![Diagram znázorňující, jaký operační režim použít s kontejnery .NET.](./media/net-container-os-targets/targeting-operating-systems.png)

**Obrázek 3-1.** Operační systémy, na které se má cílit v závislosti na verzích rozhraní .NET Framework

Při nasazování starších aplikací rozhraní .NET Framework je třeba cílit na jádro systému Windows Server Core, kompatibilní se staršími aplikacemi a službou IIS, ale má větší bitovou kopii. Při nasazování aplikací .NET Core můžete cílit na Windows Nano Server, který je optimalizovaný v cloudu, používá Kestrel a je menší a začíná rychleji. Můžete také cílit na Linux, podporující Debian, Alpine a další. Také používá Kestrel, je menší, a začíná rychleji.

Můžete také vytvořit vlastní image Dockeru v případech, kdy chcete použít jinou distro Linuxu nebo kde chcete bitovou kopii s verzemi, které nejsou poskytovány společností Microsoft. Můžete například vytvořit bitovou kopii s ASP.NET Core spuštěným na tradiční rozhraní .NET Framework a Windows Server Core, což je pro Docker netakběžný scénář.

> [!IMPORTANT]
> Při použití bitových kopií jádra systému Windows Server můžete zjistit, že některé knihovny DLL chybí ve srovnání s úplnými bitovými kopiemi systému Windows. Tento problém můžete vyřešit vytvořením vlastní bitové kopie jádra serveru a přidáním chybějících souborů v době sestavení bitové kopie, jak je uvedeno v tomto [komentáři Kihovat](https://github.com/microsoft/dotnet-framework-docker/issues/299#issuecomment-511537448).

Když přidáte název obrázku do souboru Dockerfile, můžete vybrat operační systém a verzi v závislosti na značce, kterou používáte, jako v následujících příkladech:

| Image | Komentáře |
|-------|----------|
| mcr.microsoft.com/dotnet/core/runtime:3.1 | Vícearchitektura .NET Core 3.1: Podporuje Linux a Windows Nano Server v závislosti na hostiteli Dockeru. |
| mcr.microsoft.com/dotnet/core/aspnet:3.1 | ASP.NET core 3.1 multi-architecture: Podporuje Linux a Windows Nano Server v závislosti na hostiteli Dockeru. <br/> Obraz aspnetcore má několik optimalizací pro ASP.NET Core. |
| mcr.microsoft.com/dotnet/core/aspnet:3.1-buster-slim | Pouze runtimetimem rozhraní .NET Core 3.1 na distro LinuxDebian |
| mcr.microsoft.com/dotnet/core/aspnet:3.1-nanoserver-1809 | Pouze runtime rozhraní .NET Core 3.1 na Windows Nano Server (Windows Server verze 1809) |

## <a name="additional-resources"></a>Další zdroje

- **BitmapDecoder selže z důvodu chybějící windowscsext.dll (problém GitHub)**  
  <https://github.com/microsoft/dotnet-framework-docker/issues/299>

> [!div class="step-by-step"]
> [Předchozí](container-framework-choice-factors.md)
> [další](official-net-docker-images.md)
