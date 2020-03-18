---
title: Spravované ladicí programy - .NET Core
description: Přehled ladicích programů Visual Studio a Visual Studio Code spravované.
ms.date: 08/05/2019
ms.openlocfilehash: 065b1b0fc32eb76b398cb3821c8592a1955c9359
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715557"
---
# <a name="net-core-managed-debuggers"></a><span data-ttu-id="be5d8-103">Ladicí programy spravované jádrem .NET Core</span><span class="sxs-lookup"><span data-stu-id="be5d8-103">.NET Core managed debuggers</span></span>

<span data-ttu-id="be5d8-104">Ladicí programy umožňují pozastavu nebo spuštění programů krok za krokem.</span><span class="sxs-lookup"><span data-stu-id="be5d8-104">Debuggers allow programs to be paused or executed step-by-step.</span></span> <span data-ttu-id="be5d8-105">Po pozastavení lze zobrazit aktuální stav procesu.</span><span class="sxs-lookup"><span data-stu-id="be5d8-105">When paused, the current state of the process can be viewed.</span></span> <span data-ttu-id="be5d8-106">Krokování prostřednictvím klíčových oddílů, získáte pochopení kódu a proč vytváří výsledek, který dělá.</span><span class="sxs-lookup"><span data-stu-id="be5d8-106">By stepping through key sections, you gain understanding of your code and why it produces the result that it does.</span></span>

<span data-ttu-id="be5d8-107">Společnost Microsoft poskytuje ladicí programy spravovaného kódu v **sadě Visual Studio** a Visual Studio **Code**.</span><span class="sxs-lookup"><span data-stu-id="be5d8-107">Microsoft provides debuggers for managed code in **Visual Studio** and **Visual Studio Code**.</span></span>

## <a name="visual-studio-managed-debugger"></a><span data-ttu-id="be5d8-108">Ladicí program spravované houštinou visual studia</span><span class="sxs-lookup"><span data-stu-id="be5d8-108">Visual Studio managed debugger</span></span>

<span data-ttu-id="be5d8-109">**Visual Studio** je integrované vývojové prostředí s nejkomplexnějšíladicí nepřístupnou.</span><span class="sxs-lookup"><span data-stu-id="be5d8-109">**Visual Studio** is an integrated development environment with the most comprehensive debugger available.</span></span> <span data-ttu-id="be5d8-110">Visual Studio je vynikající volbou pro vývojáře pracující v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="be5d8-110">Visual Studio is an excellent choice for developers working on Windows.</span></span>

- [<span data-ttu-id="be5d8-111">Kurz – ladění aplikace .NET Core v systému Windows pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="be5d8-111">Tutorial - Debugging a .NET Core application on Windows with Visual Studio</span></span>](../tutorials/debugging-with-visual-studio.md)

<span data-ttu-id="be5d8-112">Zatímco Visual Studio je aplikace pro Windows, lze ji stále použít k vzdálenéladění aplikací pro Linux a macOS.</span><span class="sxs-lookup"><span data-stu-id="be5d8-112">While Visual Studio is a Windows application, it can still be used to debug Linux and macOS apps remotely.</span></span>

- [<span data-ttu-id="be5d8-113">Ladění aplikace .NET Core v Linuxu/OSX pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="be5d8-113">Debugging a .NET Core application on Linux/OSX with Visual Studio</span></span>](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio)

 <span data-ttu-id="be5d8-114">Ladění ASP.NET aplikace Core vyžadují mírně odlišné pokyny.</span><span class="sxs-lookup"><span data-stu-id="be5d8-114">Debugging ASP.NET Core apps require slightly different instructions.</span></span>

- [<span data-ttu-id="be5d8-115">Ladění aplikací ASP.NET Core ve Visual Studiu</span><span class="sxs-lookup"><span data-stu-id="be5d8-115">Debug ASP.NET Core apps in Visual Studio</span></span>](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications#debug-aspnet-core-apps)

## <a name="visual-studio-code-managed-debugger"></a><span data-ttu-id="be5d8-116">Ladicí program spravovaného kódu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="be5d8-116">Visual Studio Code managed debugger</span></span>

<span data-ttu-id="be5d8-117">**Visual Studio Code** je lehký editor kódu pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="be5d8-117">**Visual Studio Code** is a lightweight cross-platform code editor.</span></span> <span data-ttu-id="be5d8-118">Používá stejnou implementaci ladicího programu .NET Core jako Visual Studio, ale se zjednodušeným uživatelským rozhraním.</span><span class="sxs-lookup"><span data-stu-id="be5d8-118">It uses the same .NET Core debugger implementation as Visual Studio, but with a simplified user interface.</span></span>

- [<span data-ttu-id="be5d8-119">Kurz – ladění aplikace .NET Core pomocí kódu sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="be5d8-119">Tutorial - Debugging a .NET Core application with Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md#debug)
- [<span data-ttu-id="be5d8-120">Ladění v kódu sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="be5d8-120">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/docs/editor/debugging)
