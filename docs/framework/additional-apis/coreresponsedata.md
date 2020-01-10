---
title: CoreResponseData – třída
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
ms.openlocfilehash: fd0ffb982c22b0a8b6cb5dd677faafb9921bf5d9
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741018"
---
# <a name="coreresponsedata-class"></a><span data-ttu-id="df058-102">CoreResponseData – třída</span><span class="sxs-lookup"><span data-stu-id="df058-102">CoreResponseData Class</span></span>

<span data-ttu-id="df058-103">Třída `CoreResponseData` představuje analýzu hlaviček protokolu HTTP a textu odpovědi.</span><span class="sxs-lookup"><span data-stu-id="df058-103">The `CoreResponseData` class represents the parsing of the HTTP headers and the response body.</span></span>

## <a name="syntax"></a><span data-ttu-id="df058-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df058-104">Syntax</span></span>
  
```csharp
internal class CoreResponseData
```

> [!WARNING]
> <span data-ttu-id="df058-105">Toto rozhraní API je interní a není určeno pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="df058-105">This API is internal, and it is not meant to be used directly in your code.</span></span> <span data-ttu-id="df058-106">Místo toho byste k připojení síťového kódu měli použít <xref:System.Diagnostics.DiagnosticSource>.</span><span class="sxs-lookup"><span data-stu-id="df058-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="df058-107">Viz [uživatelská příručka pro DiagnosticSource](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="df058-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
> 
> <span data-ttu-id="df058-108">Společnost Microsoft v žádné situaci nepodporuje použití této třídy v produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="df058-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="df058-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="df058-109">Requirements</span></span>

<span data-ttu-id="df058-110">**Obor názvů:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="df058-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="df058-111">**Sestavení:** Systém (v System. dll)</span><span class="sxs-lookup"><span data-stu-id="df058-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="df058-112">**Verze .NET Framework:** K dispozici od verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="df058-112">**.NET Framework versions:** Available since 2.0.</span></span>
