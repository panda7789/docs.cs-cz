---
title: Přerušující se změny, .NET Framework .NET Core 3,0 – .NET Core
description: Obsahuje seznam nejnovějších změn z .NET Framework .NET Core 3,0 pro model Windows Forms a Windows Presentation Foundation.
ms.date: 09/10/2019
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 292a6dbd26fe76486c62f860b7f546e20459d76c
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71119315"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core-30"></a><span data-ttu-id="fc0d0-103">Zásadní změny migrace z .NET Framework do .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="fc0d0-103">Breaking changes for migration from .NET Framework to .NET Core 3.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fc0d0-104">Tento článek je v rámci konstrukce.</span><span class="sxs-lookup"><span data-stu-id="fc0d0-104">This article is under construction.</span></span> <span data-ttu-id="fc0d0-105">Nejedná se o úplný seznam nejnovějších změn .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fc0d0-105">This is not a complete list of .NET Core breaking changes.</span></span> <span data-ttu-id="fc0d0-106">Další informace o nejnovějších změnách .NET Core můžete prostudovat jednotlivé problémy se [změnami](https://github.com/dotnet/docs/issues?q=is%3Aissue+is%3Aopen+label%3Abreaking-change) v úložišti dotnet/Docs na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="fc0d0-106">For more information on .NET Core breaking changes, you can examine individual [breaking changes issues](https://github.com/dotnet/docs/issues?q=is%3Aissue+is%3Aopen+label%3Abreaking-change) in the dotnet/docs repo on GitHub.</span></span> 

<span data-ttu-id="fc0d0-107">Pokud migrujete model Windows Forms nebo Windows Presentation Foundation aplikaci z .NET Framework na .NET Core 3,0, přečtěte si následující témata, kde najdete zásadní změny, které můžou mít vliv na vaši aplikaci:</span><span class="sxs-lookup"><span data-stu-id="fc0d0-107">If you are migrating a Windows Forms or Windows Presentation Foundation application from .NET Framework to .NET Core 3.0, review the following topics for breaking changes that may affect your app:</span></span>

## <a name="windows-forms"></a><span data-ttu-id="fc0d0-108">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fc0d0-108">Windows Forms</span></span>

[!INCLUDE[Control.DefaultFont changed to Segoe UI 9pt](~/includes/core-changes/windowsforms/control-defaultfont-changed.md)]

[!INCLUDE[Modernization of the FolderBrowserDialog](~/includes/core-changes/windowsforms/modernized-folderbrowserdialog.md)]
