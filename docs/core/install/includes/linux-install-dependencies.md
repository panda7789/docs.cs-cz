---
ms.openlocfilehash: b371525c9f4e57c6a09e5bb9232884e5c5e707e0
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84603004"
---

<span data-ttu-id="34705-101">Při instalaci nástroje pomocí Správce balíčků se tyto knihovny nainstalují za vás.</span><span class="sxs-lookup"><span data-stu-id="34705-101">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="34705-102">Pokud ale ručně nainstalujete rozhraní .NET Core nebo publikujete samostatnou aplikaci, musíte se ujistit, že jsou nainstalované tyto knihovny:</span><span class="sxs-lookup"><span data-stu-id="34705-102">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="34705-103">lttng – tým UST</span><span class="sxs-lookup"><span data-stu-id="34705-103">lttng-ust</span></span>
- <span data-ttu-id="34705-104">libcurl</span><span class="sxs-lookup"><span data-stu-id="34705-104">libcurl</span></span>
- <span data-ttu-id="34705-105">OpenSSL – knihovny</span><span class="sxs-lookup"><span data-stu-id="34705-105">openssl-libs</span></span>
- <span data-ttu-id="34705-106">krb5 – knihovny</span><span class="sxs-lookup"><span data-stu-id="34705-106">krb5-libs</span></span>
- <span data-ttu-id="34705-107">libicu</span><span class="sxs-lookup"><span data-stu-id="34705-107">libicu</span></span>
- <span data-ttu-id="34705-108">ZLIB</span><span class="sxs-lookup"><span data-stu-id="34705-108">zlib</span></span>
- <span data-ttu-id="34705-109">libunwind</span><span class="sxs-lookup"><span data-stu-id="34705-109">libunwind</span></span>
- <span data-ttu-id="34705-110">libuuid</span><span class="sxs-lookup"><span data-stu-id="34705-110">libuuid</span></span>

<span data-ttu-id="34705-111">Pokud je verze OpenSSL cílového běhového prostředí 1,1 nebo novější, budete muset nainstalovat **kompatibilní openssl10**.</span><span class="sxs-lookup"><span data-stu-id="34705-111">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="34705-112">Další informace o závislostech najdete v tématu [samostatné aplikace pro Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="34705-112">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="34705-113">Pro aplikace .NET Core, které používají sestavení *System. Drawing. Common* , budete také potřebovat následující závislost:</span><span class="sxs-lookup"><span data-stu-id="34705-113">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="34705-114">libgdiplus (verze 6.0.1 nebo novější)</span><span class="sxs-lookup"><span data-stu-id="34705-114">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="34705-115">Můžete nainstalovat nejnovější verzi *libgdiplus* přidáním úložiště mono do systému.</span><span class="sxs-lookup"><span data-stu-id="34705-115">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="34705-116">Další informace naleznete v tématu <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="34705-116">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>
