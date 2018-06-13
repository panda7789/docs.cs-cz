---
title: HttpWebRequest._CoreResponse pole
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
ms.openlocfilehash: 3627c9bf0d72ccec3a0d6d9c7c89b62f83dcd4b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33356196"
---
# <a name="httpwebrequestcoreresponse-field"></a><span data-ttu-id="b703f-102">HttpWebRequest. \_CoreResponse pole</span><span class="sxs-lookup"><span data-stu-id="b703f-102">HttpWebRequest.\_CoreResponse Field</span></span>

<span data-ttu-id="b703f-103">`HttpWebRequest._CoreResponse` je objektem (buď [CoreResponseData](coreresponsedata.md) nebo <xref:System.Exception>) obsahující výsledek analýzy odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="b703f-103">`HttpWebRequest._CoreResponse` is an object (either a [CoreResponseData](coreresponsedata.md) or an <xref:System.Exception>) containing the result of HTTP response parsing.</span></span>

## <a name="syntax"></a><span data-ttu-id="b703f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b703f-104">Syntax</span></span>
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> <span data-ttu-id="b703f-105">Toto rozhraní API není určen pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="b703f-105">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="b703f-106">Místo toho používejte <xref:System.Diagnostics.DiagnosticSource> napojit sítě kódu.</span><span class="sxs-lookup"><span data-stu-id="b703f-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="b703f-107">V tématu [DiagnosticSource uživatelská příručka](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="b703f-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
> 
> <span data-ttu-id="b703f-108">Společnost Microsoft nepodporuje použití této třídy v produkční aplikace za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="b703f-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="b703f-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b703f-109">Requirements</span></span>

<span data-ttu-id="b703f-110">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="b703f-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="b703f-111">**Sestavení:** systému (v System.dll)</span><span class="sxs-lookup"><span data-stu-id="b703f-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="b703f-112">**Verze rozhraní .NET framework:** dostupné od verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="b703f-112">**.NET Framework versions:** Available since 2.0.</span></span>
