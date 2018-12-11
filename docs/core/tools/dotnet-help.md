---
title: příkaz DotNet nápovědy
description: Příkaz dotnet help Zobrazí podrobnější online dokumentaci pro zadaný příkaz.
ms.date: 12/04/2018
ms.openlocfilehash: 44274b698ed83bd3cdb58787f433eeb5c555bc6d
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53168948"
---
# <a name="dotnet-help-reference"></a><span data-ttu-id="f5ea7-103">odkaz na nápovědu DotNet</span><span class="sxs-lookup"><span data-stu-id="f5ea7-103">dotnet help reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a><span data-ttu-id="f5ea7-104">Název</span><span class="sxs-lookup"><span data-stu-id="f5ea7-104">Name</span></span>

<span data-ttu-id="f5ea7-105">`dotnet help` – Zobrazí podrobnější online dokumentaci pro zadaný příkaz.</span><span class="sxs-lookup"><span data-stu-id="f5ea7-105">`dotnet help` - Shows more detailed documentation online for the specified command.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f5ea7-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="f5ea7-106">Synopsis</span></span>

`dotnet help <COMMAND_NAME> [-h|--help]`

## <a name="description"></a><span data-ttu-id="f5ea7-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f5ea7-107">Description</span></span>

<span data-ttu-id="f5ea7-108">`dotnet help` Příkaz otevře stránku pro odkaz na podrobné informace o zadaném příkazu na webu docs.microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="f5ea7-108">The `dotnet help` command opens up the reference page for more detailed information about the specified command at docs.microsoft.com.</span></span>

## <a name="arguments"></a><span data-ttu-id="f5ea7-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="f5ea7-109">Arguments</span></span>

* **`COMMAND_NAME`**

  <span data-ttu-id="f5ea7-110">Název příkazu rozhraní příkazového řádku .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f5ea7-110">Name of the .NET Core CLI command.</span></span> <span data-ttu-id="f5ea7-111">Seznam platných příkazů rozhraní příkazového řádku najdete v tématu [příkazy rozhraní příkazového řádku](index.md#cli-commands).</span><span class="sxs-lookup"><span data-stu-id="f5ea7-111">For a list of the valid CLI commands, see [CLI commands](index.md#cli-commands).</span></span>

## <a name="options"></a><span data-ttu-id="f5ea7-112">Možnosti</span><span class="sxs-lookup"><span data-stu-id="f5ea7-112">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="f5ea7-113">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="f5ea7-113">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="f5ea7-114">Příklady</span><span class="sxs-lookup"><span data-stu-id="f5ea7-114">Examples</span></span>

* <span data-ttu-id="f5ea7-115">Otevře se stránka dokumentace pro [dotnet nové](dotnet-new.md) příkaz:</span><span class="sxs-lookup"><span data-stu-id="f5ea7-115">Opens the documentation page for the [dotnet new](dotnet-new.md) command:</span></span>

  ```console
  dotnet help new
  ```