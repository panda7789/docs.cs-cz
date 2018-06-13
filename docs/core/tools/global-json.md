---
title: odkaz na Global.JSON
description: Najdete v části schéma pro global.json souboru, který umožňuje nastavení verze nástrojů .NET Core.
author: blackdwarf
ms.author: mairaw
ms.date: 04/05/2017
ms.openlocfilehash: 7479774c7b9cdda233cf32d791c16e7fc6d733a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33209967"
---
# <a name="globaljson-reference"></a><span data-ttu-id="bbf64-103">odkaz na Global.JSON</span><span class="sxs-lookup"><span data-stu-id="bbf64-103">global.json reference</span></span>

<span data-ttu-id="bbf64-104">*Global.json* souboru umožňuje výběr verze nástrojů .NET Core používá prostřednictvím `sdk` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="bbf64-104">The *global.json* file allows selection of the .NET Core tools version being used through the `sdk` property.</span></span>

<span data-ttu-id="bbf64-105">Nástrojů příkazového řádku .NET core vyhledejte tento soubor v aktuálním pracovním adresáři (který není nutně stejná jako adresáři projektu) nebo jednoho z jeho nadřazené adresáře.</span><span class="sxs-lookup"><span data-stu-id="bbf64-105">.NET Core CLI tools look for this file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="sdk"></a><span data-ttu-id="bbf64-106">Sada SDK</span><span class="sxs-lookup"><span data-stu-id="bbf64-106">sdk</span></span>
<span data-ttu-id="bbf64-107">Typ: objekt</span><span class="sxs-lookup"><span data-stu-id="bbf64-107">Type: Object</span></span>

<span data-ttu-id="bbf64-108">Určuje informace o sadě SDK.</span><span class="sxs-lookup"><span data-stu-id="bbf64-108">Specifies information about the SDK.</span></span>

### <a name="version"></a><span data-ttu-id="bbf64-109">verze</span><span class="sxs-lookup"><span data-stu-id="bbf64-109">version</span></span>
<span data-ttu-id="bbf64-110">Typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="bbf64-110">Type: String</span></span>

<span data-ttu-id="bbf64-111">Verze sady SDK k použití.</span><span class="sxs-lookup"><span data-stu-id="bbf64-111">The version of the SDK to use.</span></span>

<span data-ttu-id="bbf64-112">Příklad:</span><span class="sxs-lookup"><span data-stu-id="bbf64-112">For example:</span></span>

```json
{
  "sdk": {
    "version": "1.0.0-preview2-003121"
  }
}
```
