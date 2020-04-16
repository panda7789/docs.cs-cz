---
title: dotnet help, příkaz
description: Příkaz nápovědy dotnet zobrazuje podrobnější dokumentaci online pro zadaný příkaz.
ms.date: 02/14/2020
ms.openlocfilehash: a59e74a318118b6fd39d1895df02d76daa6fc9e1
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463693"
---
# <a name="dotnet-help-reference"></a><span data-ttu-id="26a2a-103">Odkaz nápovědy dotnet</span><span class="sxs-lookup"><span data-stu-id="26a2a-103">dotnet help reference</span></span>

<span data-ttu-id="26a2a-104">**Tento článek se týká:** ✔️ .NET Core 2.0 SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="26a2a-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="26a2a-105">Název</span><span class="sxs-lookup"><span data-stu-id="26a2a-105">Name</span></span>

<span data-ttu-id="26a2a-106">`dotnet help`- Zobrazuje podrobnější dokumentaci online pro zadaný příkaz.</span><span class="sxs-lookup"><span data-stu-id="26a2a-106">`dotnet help` - Shows more detailed documentation online for the specified command.</span></span>

## <a name="synopsis"></a><span data-ttu-id="26a2a-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="26a2a-107">Synopsis</span></span>

```dotnetcli
dotnet help <COMMAND_NAME> [-h|--help]
```

## <a name="description"></a><span data-ttu-id="26a2a-108">Popis</span><span class="sxs-lookup"><span data-stu-id="26a2a-108">Description</span></span>

<span data-ttu-id="26a2a-109">Příkaz `dotnet help` otevře referenční stránku pro podrobnější informace o zadaném příkazu na docs.microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="26a2a-109">The `dotnet help` command opens up the reference page for more detailed information about the specified command at docs.microsoft.com.</span></span>

## <a name="arguments"></a><span data-ttu-id="26a2a-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="26a2a-110">Arguments</span></span>

- **`COMMAND_NAME`**

  <span data-ttu-id="26a2a-111">Název příkazu rozhraní příkazu .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="26a2a-111">Name of the .NET Core CLI command.</span></span> <span data-ttu-id="26a2a-112">Seznam platných příkazů příkazového příkazu příkazu CLI naleznete v [tématu příkazy příkazu příkazu .](index.md#cli-commands)</span><span class="sxs-lookup"><span data-stu-id="26a2a-112">For a list of the valid CLI commands, see [CLI commands](index.md#cli-commands).</span></span>

## <a name="options"></a><span data-ttu-id="26a2a-113">Možnosti</span><span class="sxs-lookup"><span data-stu-id="26a2a-113">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="26a2a-114">Vytiskne krátkou nápovědu pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="26a2a-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="26a2a-115">Příklady</span><span class="sxs-lookup"><span data-stu-id="26a2a-115">Examples</span></span>

- <span data-ttu-id="26a2a-116">Otevře stránku dokumentace pro nový příkaz [dotnet:](dotnet-new.md)</span><span class="sxs-lookup"><span data-stu-id="26a2a-116">Opens the documentation page for the [dotnet new](dotnet-new.md) command:</span></span>

  ```dotnetcli
  dotnet help new
  ```
