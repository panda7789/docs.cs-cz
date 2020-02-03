---
title: dotnet – příkaz helpu
description: Příkaz dotnet Help zobrazuje podrobnější dokumentaci k uvedenému příkazu v online režimu.
ms.date: 08/08/2019
ms.openlocfilehash: 9bb4e54d2634c000707752edf53b38af43c4344e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734230"
---
# <a name="dotnet-help-reference"></a><span data-ttu-id="77a88-103">Referenční dokumentace k dotnet</span><span class="sxs-lookup"><span data-stu-id="77a88-103">dotnet help reference</span></span>

<span data-ttu-id="77a88-104">**Tento článek se týká:** ✔️ .net Core 2,0 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="77a88-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]
-->

## <a name="name"></a><span data-ttu-id="77a88-105">Název</span><span class="sxs-lookup"><span data-stu-id="77a88-105">Name</span></span>

<span data-ttu-id="77a88-106">`dotnet help` – Zobrazí podrobnější dokumentaci k určitému příkazu online.</span><span class="sxs-lookup"><span data-stu-id="77a88-106">`dotnet help` - Shows more detailed documentation online for the specified command.</span></span>

## <a name="synopsis"></a><span data-ttu-id="77a88-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="77a88-107">Synopsis</span></span>

`dotnet help <COMMAND_NAME> [-h|--help]`

## <a name="description"></a><span data-ttu-id="77a88-108">Popis</span><span class="sxs-lookup"><span data-stu-id="77a88-108">Description</span></span>

<span data-ttu-id="77a88-109">Příkaz `dotnet help` otevře referenční stránku, kde najdete podrobnější informace o zadaném příkazu na adrese docs.microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="77a88-109">The `dotnet help` command opens up the reference page for more detailed information about the specified command at docs.microsoft.com.</span></span>

## <a name="arguments"></a><span data-ttu-id="77a88-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="77a88-110">Arguments</span></span>

* **`COMMAND_NAME`**

  <span data-ttu-id="77a88-111">Název .NET Core CLI příkazu</span><span class="sxs-lookup"><span data-stu-id="77a88-111">Name of the .NET Core CLI command.</span></span> <span data-ttu-id="77a88-112">Seznam platných příkazů rozhraní příkazového řádku najdete v tématu [příkazy rozhraní příkazového řádku](index.md#cli-commands).</span><span class="sxs-lookup"><span data-stu-id="77a88-112">For a list of the valid CLI commands, see [CLI commands](index.md#cli-commands).</span></span>

## <a name="options"></a><span data-ttu-id="77a88-113">Možnosti</span><span class="sxs-lookup"><span data-stu-id="77a88-113">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="77a88-114">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="77a88-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="77a88-115">Příklady</span><span class="sxs-lookup"><span data-stu-id="77a88-115">Examples</span></span>

* <span data-ttu-id="77a88-116">Otevře stránku dokumentace pro příkaz [dotnet New](dotnet-new.md) :</span><span class="sxs-lookup"><span data-stu-id="77a88-116">Opens the documentation page for the [dotnet new](dotnet-new.md) command:</span></span>

  ```dotnetcli
  dotnet help new
  ```
