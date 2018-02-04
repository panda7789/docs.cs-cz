---
title: HttpWebRequest._CoreResponse Field
ms.date: 01/29/2018
ms.prod: .net-framework
ms.technology: 
ms.topic: reference
topic_type:
- apiref
api_name:
- System.Net.HttpWebRequest._CoreResponse
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.author: stwhi
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: e6493747cf6c894357223f011da026770778e26c
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2018
---
# <a name="httpwebrequestcoreresponse-field"></a><span data-ttu-id="58094-102">HttpWebRequest. \_CoreResponse pole</span><span class="sxs-lookup"><span data-stu-id="58094-102">HttpWebRequest.\_CoreResponse Field</span></span>

<span data-ttu-id="58094-103">`HttpWebRequest._CoreResponse`je objektem (buď [CoreResponseData](coreresponsedata.md) nebo <xref:System.Exception>) obsahující výsledek analýzy odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="58094-103">`HttpWebRequest._CoreResponse` is an object (either a [CoreResponseData](coreresponsedata.md) or an <xref:System.Exception>) containing the result of HTTP response parsing.</span></span>

## <a name="syntax"></a><span data-ttu-id="58094-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58094-104">Syntax</span></span>
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> <span data-ttu-id="58094-105">Toto rozhraní API není určen pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="58094-105">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="58094-106">Místo toho používejte <xref:System.Diagnostics.DiagnosticSource> napojit sítě kódu.</span><span class="sxs-lookup"><span data-stu-id="58094-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="58094-107">V tématu [DiagnosticSource uživatelská příručka](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="58094-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
> 
> <span data-ttu-id="58094-108">Společnost Microsoft nepodporuje použití této třídy v produkční aplikace za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="58094-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="58094-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="58094-109">Requirements</span></span>

<span data-ttu-id="58094-110">**Namespace:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="58094-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="58094-111">**Sestavení:** systému (v System.dll)</span><span class="sxs-lookup"><span data-stu-id="58094-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="58094-112">**Verze rozhraní .NET framework:** dostupné od verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="58094-112">**.NET Framework versions:** Available since 2.0.</span></span>
