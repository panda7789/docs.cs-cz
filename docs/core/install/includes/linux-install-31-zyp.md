---
ms.openlocfilehash: db89539982c1afe0df374027d54826f3265f0fee
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84603011"
---

### <a name="install-the-sdk"></a><span data-ttu-id="511fc-101">Instalace sady SDK</span><span class="sxs-lookup"><span data-stu-id="511fc-101">Install the SDK</span></span>

<span data-ttu-id="511fc-102">.NET Core SDK umožňuje vyvíjet aplikace pomocí .NET Core.</span><span class="sxs-lookup"><span data-stu-id="511fc-102">The .NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="511fc-103">Chcete-li nainstalovat .NET Core SDK, spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="511fc-103">To install the .NET Core SDK, run the following commands.</span></span>

```bash
sudo zypper install dotnet-sdk-3.1
```

### <a name="install-the-runtime"></a><span data-ttu-id="511fc-104">Instalace modulu runtime</span><span class="sxs-lookup"><span data-stu-id="511fc-104">Install the runtime</span></span>

<span data-ttu-id="511fc-105">Modul runtime .NET Core umožňuje spouštět aplikace, které byly vytvořeny pomocí .NET Core, které neobsahovaly modul runtime.</span><span class="sxs-lookup"><span data-stu-id="511fc-105">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="511fc-106">Níže uvedené příkazy nainstalují modul runtime ASP.NET Core, což je nejvíce kompatibilní modul runtime pro .NET Core.</span><span class="sxs-lookup"><span data-stu-id="511fc-106">The commands below install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="511fc-107">V terminálu spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="511fc-107">In your terminal, run the following commands.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.1
```

<span data-ttu-id="511fc-108">Jako alternativu k modulu runtime ASP.NET Core můžete nainstalovat modul runtime .NET Core, který neobsahuje podporu ASP.NET Core: Nahraďte `aspnetcore-runtime-2.1` v příkazu výše `dotnet-runtime-3.1` .</span><span class="sxs-lookup"><span data-stu-id="511fc-108">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `aspnetcore-runtime-2.1` in the command above with `dotnet-runtime-3.1`.</span></span>

```bash
sudo zypper install dotnet-runtime-3.1
```
