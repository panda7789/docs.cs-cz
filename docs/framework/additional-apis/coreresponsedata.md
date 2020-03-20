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
ms.openlocfilehash: 39a14a3df5059cc47cd4879e4d4ba351cc7b655b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79156113"
---
# <a name="coreresponsedata-class"></a><span data-ttu-id="492be-102">CoreResponseData – třída</span><span class="sxs-lookup"><span data-stu-id="492be-102">CoreResponseData Class</span></span>

<span data-ttu-id="492be-103">Třída `CoreResponseData` představuje analýzu hlavičky HTTP a tělo odpovědi.</span><span class="sxs-lookup"><span data-stu-id="492be-103">The `CoreResponseData` class represents the parsing of the HTTP headers and the response body.</span></span>

## <a name="syntax"></a><span data-ttu-id="492be-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="492be-104">Syntax</span></span>
  
```csharp
internal class CoreResponseData
```

> [!WARNING]
> <span data-ttu-id="492be-105">Toto rozhraní API je interní a není určen pro použití přímo ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="492be-105">This API is internal, and it is not meant to be used directly in your code.</span></span> <span data-ttu-id="492be-106">Místo toho byste <xref:System.Diagnostics.DiagnosticSource> měli použít připojit síťový kód.</span><span class="sxs-lookup"><span data-stu-id="492be-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="492be-107">Viz [DiagnosticSource Uživatelská příručka](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="492be-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
>
> <span data-ttu-id="492be-108">Společnost Microsoft nepodporuje použití této třídy v produkční aplikaci za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="492be-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="492be-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="492be-109">Requirements</span></span>

<span data-ttu-id="492be-110">**Obor názvů:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="492be-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="492be-111">**Sestava:** Systém (v souboru System.dll)</span><span class="sxs-lookup"><span data-stu-id="492be-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="492be-112">**Verze rozhraní .NET Framework:** K dispozici od 2.0.</span><span class="sxs-lookup"><span data-stu-id="492be-112">**.NET Framework versions:** Available since 2.0.</span></span>
