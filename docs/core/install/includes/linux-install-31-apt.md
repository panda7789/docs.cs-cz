---
ms.openlocfilehash: b6f2af7af77398d5e902aae995590b5dde4cf76a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602906"
---

### <a name="install-the-sdk"></a><span data-ttu-id="7fe54-101">Instalace sady SDK</span><span class="sxs-lookup"><span data-stu-id="7fe54-101">Install the SDK</span></span>

<span data-ttu-id="7fe54-102">.NET Core SDK umožňuje vyvíjet aplikace pomocí .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7fe54-102">.NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="7fe54-103">Pokud nainstalujete .NET Core SDK, nemusíte instalovat odpovídající modul runtime.</span><span class="sxs-lookup"><span data-stu-id="7fe54-103">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="7fe54-104">Chcete-li nainstalovat .NET Core SDK, spusťte následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="7fe54-104">To install .NET Core SDK, run the following commands:</span></span>

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y dotnet-sdk-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="7fe54-105">Pokud se zobrazí chybová zpráva podobná té, že se **nepovedlo najít balíček dotnet-SDK-3,1**, přečtěte si část [věnované řešení potíží s apt](#apt-troubleshooting) .</span><span class="sxs-lookup"><span data-stu-id="7fe54-105">If you receive an error message similar to **Unable to locate package dotnet-sdk-3.1**, see the [APT troubleshooting](#apt-troubleshooting) section.</span></span>

### <a name="install-the-runtime"></a><span data-ttu-id="7fe54-106">Instalace modulu runtime</span><span class="sxs-lookup"><span data-stu-id="7fe54-106">Install the runtime</span></span>

<span data-ttu-id="7fe54-107">Modul runtime .NET Core umožňuje spouštět aplikace, které byly vytvořeny pomocí .NET Core, které neobsahovaly modul runtime.</span><span class="sxs-lookup"><span data-stu-id="7fe54-107">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="7fe54-108">Níže uvedené příkazy nainstalují modul runtime ASP.NET Core, což je nejvíce kompatibilní modul runtime pro .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7fe54-108">The commands below install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="7fe54-109">V terminálu spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="7fe54-109">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="7fe54-110">Pokud se zobrazí chybová zpráva podobná té, že **nejde najít Package aspnetcore-runtime-3,1**, přečtěte si část [věnované odstraňování potíží s apt](#apt-troubleshooting) .</span><span class="sxs-lookup"><span data-stu-id="7fe54-110">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-3.1**, see the [APT troubleshooting](#apt-troubleshooting) section.</span></span>

<span data-ttu-id="7fe54-111">Jako alternativu k modulu runtime ASP.NET Core můžete nainstalovat modul runtime .NET Core, který neobsahuje podporu ASP.NET Core: Nahraďte `aspnetcore-runtime-3.1` v příkazu výše `dotnet-runtime-3.1` .</span><span class="sxs-lookup"><span data-stu-id="7fe54-111">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `aspnetcore-runtime-3.1` in the command above with `dotnet-runtime-3.1`.</span></span>

```bash
sudo apt-get install -y dotnet-runtime-3.1
```
