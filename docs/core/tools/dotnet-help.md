---
title: dotnet – příkaz helpu
description: Příkaz dotnet Help zobrazuje podrobnější dokumentaci k uvedenému příkazu v online režimu.
ms.date: 02/14/2020
ms.openlocfilehash: f5d9221ae18653451a3bf97dc82fae396ae4e288
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503727"
---
# <a name="dotnet-help-reference"></a><span data-ttu-id="6d36d-103">Referenční dokumentace k dotnet</span><span class="sxs-lookup"><span data-stu-id="6d36d-103">dotnet help reference</span></span>

<span data-ttu-id="6d36d-104">**Tento článek se týká:** ✔️ .net Core 2,0 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="6d36d-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="6d36d-105">Název</span><span class="sxs-lookup"><span data-stu-id="6d36d-105">Name</span></span>

<span data-ttu-id="6d36d-106">`dotnet help` – Zobrazí podrobnější dokumentaci k určitému příkazu online.</span><span class="sxs-lookup"><span data-stu-id="6d36d-106">`dotnet help` - Shows more detailed documentation online for the specified command.</span></span>

## <a name="synopsis"></a><span data-ttu-id="6d36d-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="6d36d-107">Synopsis</span></span>

`dotnet help <COMMAND_NAME> [-h|--help]`

## <a name="description"></a><span data-ttu-id="6d36d-108">Popis</span><span class="sxs-lookup"><span data-stu-id="6d36d-108">Description</span></span>

<span data-ttu-id="6d36d-109">Příkaz `dotnet help` otevře referenční stránku, kde najdete podrobnější informace o zadaném příkazu na adrese docs.microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="6d36d-109">The `dotnet help` command opens up the reference page for more detailed information about the specified command at docs.microsoft.com.</span></span>

## <a name="arguments"></a><span data-ttu-id="6d36d-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="6d36d-110">Arguments</span></span>

- **`COMMAND_NAME`**

  <span data-ttu-id="6d36d-111">Název .NET Core CLI příkazu</span><span class="sxs-lookup"><span data-stu-id="6d36d-111">Name of the .NET Core CLI command.</span></span> <span data-ttu-id="6d36d-112">Seznam platných příkazů rozhraní příkazového řádku najdete v tématu [příkazy rozhraní příkazového řádku](index.md#cli-commands).</span><span class="sxs-lookup"><span data-stu-id="6d36d-112">For a list of the valid CLI commands, see [CLI commands](index.md#cli-commands).</span></span>

## <a name="options"></a><span data-ttu-id="6d36d-113">Možnosti</span><span class="sxs-lookup"><span data-stu-id="6d36d-113">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="6d36d-114">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="6d36d-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="6d36d-115">Příklady</span><span class="sxs-lookup"><span data-stu-id="6d36d-115">Examples</span></span>

- <span data-ttu-id="6d36d-116">Otevře stránku dokumentace pro příkaz [dotnet New](dotnet-new.md) :</span><span class="sxs-lookup"><span data-stu-id="6d36d-116">Opens the documentation page for the [dotnet new](dotnet-new.md) command:</span></span>

  ```dotnetcli
  dotnet help new
  ```
