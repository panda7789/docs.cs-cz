---
title: dotnet help, příkaz
description: Příkaz nápovědy dotnet zobrazuje podrobnější dokumentaci online pro zadaný příkaz.
ms.date: 02/14/2020
ms.openlocfilehash: f5d9221ae18653451a3bf97dc82fae396ae4e288
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503727"
---
# <a name="dotnet-help-reference"></a><span data-ttu-id="9616b-103">Odkaz nápovědy dotnet</span><span class="sxs-lookup"><span data-stu-id="9616b-103">dotnet help reference</span></span>

<span data-ttu-id="9616b-104">**Tento článek se týká:** ✔️ .NET Core 2.0 SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="9616b-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="9616b-105">Name (Název)</span><span class="sxs-lookup"><span data-stu-id="9616b-105">Name</span></span>

<span data-ttu-id="9616b-106">`dotnet help`- Zobrazuje podrobnější dokumentaci online pro zadaný příkaz.</span><span class="sxs-lookup"><span data-stu-id="9616b-106">`dotnet help` - Shows more detailed documentation online for the specified command.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9616b-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="9616b-107">Synopsis</span></span>

`dotnet help <COMMAND_NAME> [-h|--help]`

## <a name="description"></a><span data-ttu-id="9616b-108">Popis</span><span class="sxs-lookup"><span data-stu-id="9616b-108">Description</span></span>

<span data-ttu-id="9616b-109">Příkaz `dotnet help` otevře referenční stránku pro podrobnější informace o zadaném příkazu na docs.microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="9616b-109">The `dotnet help` command opens up the reference page for more detailed information about the specified command at docs.microsoft.com.</span></span>

## <a name="arguments"></a><span data-ttu-id="9616b-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="9616b-110">Arguments</span></span>

- **`COMMAND_NAME`**

  <span data-ttu-id="9616b-111">Název příkazu rozhraní příkazu .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="9616b-111">Name of the .NET Core CLI command.</span></span> <span data-ttu-id="9616b-112">Seznam platných příkazů příkazového příkazu příkazu CLI naleznete v [tématu příkazy příkazu příkazu .](index.md#cli-commands)</span><span class="sxs-lookup"><span data-stu-id="9616b-112">For a list of the valid CLI commands, see [CLI commands](index.md#cli-commands).</span></span>

## <a name="options"></a><span data-ttu-id="9616b-113">Možnosti</span><span class="sxs-lookup"><span data-stu-id="9616b-113">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="9616b-114">Vytiskne krátkou nápovědu pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="9616b-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="9616b-115">Příklady</span><span class="sxs-lookup"><span data-stu-id="9616b-115">Examples</span></span>

- <span data-ttu-id="9616b-116">Otevře stránku dokumentace pro nový příkaz [dotnet:](dotnet-new.md)</span><span class="sxs-lookup"><span data-stu-id="9616b-116">Opens the documentation page for the [dotnet new](dotnet-new.md) command:</span></span>

  ```dotnetcli
  dotnet help new
  ```
