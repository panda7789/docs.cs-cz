---
title: CoreResponseData – třída
description: Pochopení třídy CoreResponseData, která představuje analýzu hlaviček protokolu HTTP a textu odpovědi. Je v oboru názvů System.Net v .NET.
ms.date: 01/29/2018
topic_type:
- apiref
api_name:
- System.Net.CoreResponseData
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.openlocfilehash: 8248cc20f6528a1c3bc64c9b9339a3a3000d03a0
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989800"
---
# <a name="coreresponsedata-class"></a><span data-ttu-id="8c598-104">CoreResponseData – třída</span><span class="sxs-lookup"><span data-stu-id="8c598-104">CoreResponseData Class</span></span>

<span data-ttu-id="8c598-105">`CoreResponseData`Třída představuje analýzu hlaviček protokolu HTTP a textu odpovědi.</span><span class="sxs-lookup"><span data-stu-id="8c598-105">The `CoreResponseData` class represents the parsing of the HTTP headers and the response body.</span></span>

## <a name="syntax"></a><span data-ttu-id="8c598-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="8c598-106">Syntax</span></span>
  
```csharp
internal class CoreResponseData
```

> [!WARNING]
> <span data-ttu-id="8c598-107">Toto rozhraní API je interní a není určeno pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="8c598-107">This API is internal, and it is not meant to be used directly in your code.</span></span> <span data-ttu-id="8c598-108">Místo toho byste měli použít <xref:System.Diagnostics.DiagnosticSource> k zavěšení síťového kódu.</span><span class="sxs-lookup"><span data-stu-id="8c598-108">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="8c598-109">Viz [uživatelská příručka pro DiagnosticSource](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="8c598-109">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
>
> <span data-ttu-id="8c598-110">Společnost Microsoft v žádné situaci nepodporuje použití této třídy v produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8c598-110">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="8c598-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8c598-111">Requirements</span></span>

<span data-ttu-id="8c598-112">**Obor názvů:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="8c598-112">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="8c598-113">**Sestavení:** Systém (v System.dll)</span><span class="sxs-lookup"><span data-stu-id="8c598-113">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="8c598-114">**Verze .NET Framework:** K dispozici od verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="8c598-114">**.NET Framework versions:** Available since 2.0.</span></span>
