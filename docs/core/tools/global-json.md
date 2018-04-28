---
title: odkaz na Global.JSON
description: Najdete v části schéma pro global.json souboru, který umožňuje nastavení verze nástrojů .NET Core.
author: blackdwarf
ms.author: mairaw
ms.date: 04/05/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: ac53a899e76c99527f2670d0a6bed3f8cc6ce31f
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="globaljson-reference"></a><span data-ttu-id="bcc3d-103">odkaz na Global.JSON</span><span class="sxs-lookup"><span data-stu-id="bcc3d-103">global.json reference</span></span>

<span data-ttu-id="bcc3d-104">*Global.json* souboru umožňuje výběr verze nástrojů .NET Core používá prostřednictvím `sdk` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="bcc3d-104">The *global.json* file allows selection of the .NET Core tools version being used through the `sdk` property.</span></span>

<span data-ttu-id="bcc3d-105">Nástrojů příkazového řádku .NET core vyhledejte tento soubor v aktuálním pracovním adresáři (který není nutně stejná jako adresáři projektu) nebo jednoho z jeho nadřazené adresáře.</span><span class="sxs-lookup"><span data-stu-id="bcc3d-105">.NET Core CLI tools look for this file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="sdk"></a><span data-ttu-id="bcc3d-106">Sada SDK</span><span class="sxs-lookup"><span data-stu-id="bcc3d-106">sdk</span></span>
<span data-ttu-id="bcc3d-107">Typ: objekt</span><span class="sxs-lookup"><span data-stu-id="bcc3d-107">Type: Object</span></span>

<span data-ttu-id="bcc3d-108">Určuje informace o sadě SDK.</span><span class="sxs-lookup"><span data-stu-id="bcc3d-108">Specifies information about the SDK.</span></span>

### <a name="version"></a><span data-ttu-id="bcc3d-109">verze</span><span class="sxs-lookup"><span data-stu-id="bcc3d-109">version</span></span>
<span data-ttu-id="bcc3d-110">Typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="bcc3d-110">Type: String</span></span>

<span data-ttu-id="bcc3d-111">Verze sady SDK k použití.</span><span class="sxs-lookup"><span data-stu-id="bcc3d-111">The version of the SDK to use.</span></span>

<span data-ttu-id="bcc3d-112">Příklad:</span><span class="sxs-lookup"><span data-stu-id="bcc3d-112">For example:</span></span>

```json
{
  "sdk": {
    "version": "1.0.0-preview2-003121"
  }
}
```
