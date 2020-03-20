---
title: Pole HttpWebRequest._CoreResponse
ms.date: 01/29/2018
topic_type:
- apiref
api_name:
- System.Net.HttpWebRequest._CoreResponse
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.openlocfilehash: b275f3eece96ac8a9ae3fb0ebd030c8d79e21fc1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155918"
---
# <a name="httpwebrequest_coreresponse-field"></a><span data-ttu-id="06119-102">HttpWebRequest. \_Pole CoreResponse</span><span class="sxs-lookup"><span data-stu-id="06119-102">HttpWebRequest.\_CoreResponse Field</span></span>

<span data-ttu-id="06119-103">`HttpWebRequest._CoreResponse`je objekt (buď [CoreResponseData](coreresponsedata.md) <xref:System.Exception>nebo ) obsahující výsledek analýzy odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="06119-103">`HttpWebRequest._CoreResponse` is an object (either a [CoreResponseData](coreresponsedata.md) or an <xref:System.Exception>) containing the result of HTTP response parsing.</span></span>

## <a name="syntax"></a><span data-ttu-id="06119-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06119-104">Syntax</span></span>
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> <span data-ttu-id="06119-105">Toto rozhraní API není určen pro použití přímo ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="06119-105">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="06119-106">Místo toho byste <xref:System.Diagnostics.DiagnosticSource> měli použít připojit síťový kód.</span><span class="sxs-lookup"><span data-stu-id="06119-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="06119-107">Viz [DiagnosticSource Uživatelská příručka](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="06119-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
>
> <span data-ttu-id="06119-108">Společnost Microsoft nepodporuje použití této třídy v produkční aplikaci za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="06119-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="06119-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="06119-109">Requirements</span></span>

<span data-ttu-id="06119-110">**Obor názvů:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="06119-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="06119-111">**Sestava:** Systém (v souboru System.dll)</span><span class="sxs-lookup"><span data-stu-id="06119-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="06119-112">**Verze rozhraní .NET Framework:** K dispozici od 2.0.</span><span class="sxs-lookup"><span data-stu-id="06119-112">**.NET Framework versions:** Available since 2.0.</span></span>
