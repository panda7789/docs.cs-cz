---
ms.openlocfilehash: 3d8179c5c0e84f8ff1197cce7790c80a5f5a4f6d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619443"
---

<span data-ttu-id="4699a-101">Při instalaci nástroje pomocí Správce balíčků se tyto knihovny nainstalují za vás.</span><span class="sxs-lookup"><span data-stu-id="4699a-101">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="4699a-102">Pokud ale ručně nainstalujete rozhraní .NET Core nebo publikujete samostatnou aplikaci, musíte se ujistit, že jsou nainstalované tyto knihovny:</span><span class="sxs-lookup"><span data-stu-id="4699a-102">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="4699a-103">krb5 – knihovny</span><span class="sxs-lookup"><span data-stu-id="4699a-103">krb5-libs</span></span>
- <span data-ttu-id="4699a-104">libicu</span><span class="sxs-lookup"><span data-stu-id="4699a-104">libicu</span></span>
- <span data-ttu-id="4699a-105">OpenSSL – knihovny</span><span class="sxs-lookup"><span data-stu-id="4699a-105">openssl-libs</span></span>

<span data-ttu-id="4699a-106">Pokud je verze OpenSSL cílového běhového prostředí 1,1 nebo novější, budete muset nainstalovat **kompatibilní openssl10**.</span><span class="sxs-lookup"><span data-stu-id="4699a-106">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="4699a-107">Další informace o závislostech najdete v tématu [samostatné aplikace pro Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="4699a-107">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="4699a-108">Pro aplikace .NET Core, které používají sestavení *System. Drawing. Common* , budete také potřebovat následující závislost:</span><span class="sxs-lookup"><span data-stu-id="4699a-108">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="4699a-109">libgdiplus (verze 6.0.1 nebo novější)</span><span class="sxs-lookup"><span data-stu-id="4699a-109">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="4699a-110">Můžete nainstalovat nejnovější verzi *libgdiplus* přidáním úložiště mono do systému.</span><span class="sxs-lookup"><span data-stu-id="4699a-110">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="4699a-111">Další informace naleznete v tématu <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="4699a-111">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>
