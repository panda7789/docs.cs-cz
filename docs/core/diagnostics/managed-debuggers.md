---
title: Spravované ladicí programy – .NET Core
description: Přehled sady Visual Studio a Visual Studio Code spravovaných ladicích programů.
author: sdmaclea
ms.author: stmaclea
ms.date: 08/05/2019
ms.openlocfilehash: 8110ecb10ad2e6213e15df8848abab73d07d89b2
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68974132"
---
# <a name="net-core-managed-debuggers"></a><span data-ttu-id="89638-103">Spravované ladicí programy .NET Core</span><span class="sxs-lookup"><span data-stu-id="89638-103">.NET Core managed debuggers</span></span>

<span data-ttu-id="89638-104">Ladicí programy umožňují pozastaví nebo spustit programy krok za krokem.</span><span class="sxs-lookup"><span data-stu-id="89638-104">Debuggers allow programs to be paused or executed step-by-step.</span></span> <span data-ttu-id="89638-105">Při pozastavení lze aktuální stav procesu zobrazit.</span><span class="sxs-lookup"><span data-stu-id="89638-105">When paused, the current state of the process can be viewed.</span></span> <span data-ttu-id="89638-106">Díky krokování v klíčových částech získáte vysvětlení kódu a proč vytvoří výsledek, který dělá.</span><span class="sxs-lookup"><span data-stu-id="89638-106">By stepping through key sections, you gain understanding of your code and why it produces the result that it does.</span></span>

<span data-ttu-id="89638-107">Společnost Microsoft poskytuje ladicí programy pro spravovaný kód v **aplikaci Visual Studio** a **Visual Studio Code**.</span><span class="sxs-lookup"><span data-stu-id="89638-107">Microsoft provides debuggers for managed code in **Visual Studio** and **Visual Studio Code**.</span></span>

## <a name="visual-studio-managed-debugger"></a><span data-ttu-id="89638-108">Spravovaný ladicí program sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="89638-108">Visual Studio managed debugger</span></span>

<span data-ttu-id="89638-109">**Visual Studio** je integrované vývojové prostředí s nejkomplexním ladicím programem, který je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="89638-109">**Visual Studio** is an integrated development environment with the most comprehensive debugger available.</span></span> <span data-ttu-id="89638-110">Visual Studio je vynikající volbou pro vývojáře, kteří pracují na Windows.</span><span class="sxs-lookup"><span data-stu-id="89638-110">Visual Studio is an excellent choice for developers working on Windows.</span></span>
- [<span data-ttu-id="89638-111">Kurz – ladění aplikace .NET Core ve Windows se sadou Visual Studio</span><span class="sxs-lookup"><span data-stu-id="89638-111">Tutorial - Debugging a .NET Core application on Windows with Visual Studio</span></span>](../tutorials/debugging-with-visual-studio.md)

<span data-ttu-id="89638-112">I když je Visual Studio aplikace pro Windows, může se pořád použít k vzdálené ladění aplikací pro Linux a macOS.</span><span class="sxs-lookup"><span data-stu-id="89638-112">While Visual Studio is a Windows application, it can still be used to debug Linux and macOS apps remotely.</span></span>
- [<span data-ttu-id="89638-113">Ladění aplikace .NET Core v systému Linux/OSX pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="89638-113">Debugging a .NET Core application on Linux/OSX with Visual Studio</span></span>](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio)

 <span data-ttu-id="89638-114">Ladění ASP.NET Core aplikací vyžaduje trochu jiné pokyny.</span><span class="sxs-lookup"><span data-stu-id="89638-114">Debugging ASP.NET Core apps require slightly different instructions.</span></span>

- [<span data-ttu-id="89638-115">Ladění aplikací ASP.NET Core v aplikaci Visual Studio</span><span class="sxs-lookup"><span data-stu-id="89638-115">Debug ASP.NET Core apps in Visual Studio</span></span>](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications#debug-aspnet-core-apps)

## <a name="visual-studio-code-managed-debugger"></a><span data-ttu-id="89638-116">Visual Studio Code spravovaný ladicí program</span><span class="sxs-lookup"><span data-stu-id="89638-116">Visual Studio Code managed debugger</span></span>

<span data-ttu-id="89638-117">**Visual Studio Code** je zjednodušený Editor kódu pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="89638-117">**Visual Studio Code** is a lightweight cross-platform code editor.</span></span> <span data-ttu-id="89638-118">Používá stejnou implementaci ladicího programu .NET Core jako Visual Studio, ale má zjednodušené uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="89638-118">It uses the same .NET Core debugger implementation as Visual Studio, but with a simplified user interface.</span></span>

- [<span data-ttu-id="89638-119">Kurz – ladění aplikace .NET Core pomocí Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="89638-119">Tutorial - Debugging a .NET Core application with Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md#debug)
- [<span data-ttu-id="89638-120">Ladění v Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="89638-120">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/docs/editor/debugging)
