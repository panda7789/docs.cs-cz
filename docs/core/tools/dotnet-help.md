---
title: dotnet – příkaz helpu
description: Příkaz dotnet Help zobrazuje podrobnější dokumentaci k uvedenému příkazu v online režimu.
ms.date: 08/08/2019
ms.openlocfilehash: 533f2c47fa7ec14d31368538092fec2490234820
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117714"
---
# <a name="dotnet-help-reference"></a><span data-ttu-id="ae862-103">Referenční dokumentace k dotnet</span><span class="sxs-lookup"><span data-stu-id="ae862-103">dotnet help reference</span></span>

<span data-ttu-id="ae862-104">**Tento článek se týká: ✓** .net Core 2,0 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="ae862-104">**This article applies to: ✓** .NET Core 2.0 SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]
-->

## <a name="name"></a><span data-ttu-id="ae862-105">Name</span><span class="sxs-lookup"><span data-stu-id="ae862-105">Name</span></span>

<span data-ttu-id="ae862-106">`dotnet help`– Zobrazí podrobnější dokumentaci k určitému příkazu online.</span><span class="sxs-lookup"><span data-stu-id="ae862-106">`dotnet help` - Shows more detailed documentation online for the specified command.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ae862-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="ae862-107">Synopsis</span></span>

`dotnet help <COMMAND_NAME> [-h|--help]`

## <a name="description"></a><span data-ttu-id="ae862-108">Popis</span><span class="sxs-lookup"><span data-stu-id="ae862-108">Description</span></span>

<span data-ttu-id="ae862-109">`dotnet help` Příkaz otevře referenční stránku, kde najdete podrobnější informace o zadaném příkazu na adrese docs.Microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="ae862-109">The `dotnet help` command opens up the reference page for more detailed information about the specified command at docs.microsoft.com.</span></span>

## <a name="arguments"></a><span data-ttu-id="ae862-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="ae862-110">Arguments</span></span>

* **`COMMAND_NAME`**

  <span data-ttu-id="ae862-111">Název .NET Core CLI příkazu</span><span class="sxs-lookup"><span data-stu-id="ae862-111">Name of the .NET Core CLI command.</span></span> <span data-ttu-id="ae862-112">Seznam platných příkazů rozhraní příkazového řádku najdete v tématu [příkazy rozhraní příkazového řádku](index.md#cli-commands).</span><span class="sxs-lookup"><span data-stu-id="ae862-112">For a list of the valid CLI commands, see [CLI commands](index.md#cli-commands).</span></span>

## <a name="options"></a><span data-ttu-id="ae862-113">Možnosti</span><span class="sxs-lookup"><span data-stu-id="ae862-113">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="ae862-114">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="ae862-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="ae862-115">Příklady</span><span class="sxs-lookup"><span data-stu-id="ae862-115">Examples</span></span>

* <span data-ttu-id="ae862-116">Otevře stránku dokumentace pro příkaz [dotnet New](dotnet-new.md) :</span><span class="sxs-lookup"><span data-stu-id="ae862-116">Opens the documentation page for the [dotnet new](dotnet-new.md) command:</span></span>

  ```dotnetcli
  dotnet help new
  ```
