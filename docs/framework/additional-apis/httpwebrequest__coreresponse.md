---
title: HttpWebRequest. _CoreResponse – pole
description: Přečtěte si o poli HttpWebRequest. _CoreResponse v .NET. Toto pole je objekt CoreResponseData nebo Exception, který obsahuje výsledek analýzy odpovědi HTTP.
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
ms.openlocfilehash: 5093ec7ed2c3b94931dcd622ae9ccdb42feffa18
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989747"
---
# <a name="httpwebrequest_coreresponse-field"></a><span data-ttu-id="2ec86-104">HttpWebRequest. \_ Pole CoreResponse</span><span class="sxs-lookup"><span data-stu-id="2ec86-104">HttpWebRequest.\_CoreResponse Field</span></span>

<span data-ttu-id="2ec86-105">`HttpWebRequest._CoreResponse`je objekt (buď [CoreResponseData](coreresponsedata.md) nebo a <xref:System.Exception> ), který obsahuje výsledek analýzy odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="2ec86-105">`HttpWebRequest._CoreResponse` is an object (either a [CoreResponseData](coreresponsedata.md) or an <xref:System.Exception>) containing the result of HTTP response parsing.</span></span>

## <a name="syntax"></a><span data-ttu-id="2ec86-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="2ec86-106">Syntax</span></span>
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> <span data-ttu-id="2ec86-107">Toto rozhraní API není určeno k použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="2ec86-107">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="2ec86-108">Místo toho byste měli použít <xref:System.Diagnostics.DiagnosticSource> k zavěšení síťového kódu.</span><span class="sxs-lookup"><span data-stu-id="2ec86-108">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="2ec86-109">Viz [uživatelská příručka pro DiagnosticSource](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="2ec86-109">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
>
> <span data-ttu-id="2ec86-110">Společnost Microsoft v žádné situaci nepodporuje použití této třídy v produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2ec86-110">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="2ec86-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2ec86-111">Requirements</span></span>

<span data-ttu-id="2ec86-112">**Obor názvů:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="2ec86-112">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="2ec86-113">**Sestavení:** Systém (v System.dll)</span><span class="sxs-lookup"><span data-stu-id="2ec86-113">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="2ec86-114">**Verze .NET Framework:** K dispozici od verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="2ec86-114">**.NET Framework versions:** Available since 2.0.</span></span>
