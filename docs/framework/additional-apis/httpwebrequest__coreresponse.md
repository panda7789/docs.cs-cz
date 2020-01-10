---
title: HttpWebRequest. _CoreResponse – pole
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
ms.openlocfilehash: d16936f6984e73a886f5f48e05b53501ced63c1b
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740445"
---
# <a name="httpwebrequest_coreresponse-field"></a><span data-ttu-id="ec78d-102">HttpWebRequest.\_pole CoreResponse</span><span class="sxs-lookup"><span data-stu-id="ec78d-102">HttpWebRequest.\_CoreResponse Field</span></span>

<span data-ttu-id="ec78d-103">`HttpWebRequest._CoreResponse` je objekt (buď [CoreResponseData](coreresponsedata.md) nebo <xref:System.Exception>), který obsahuje výsledek analýzy odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="ec78d-103">`HttpWebRequest._CoreResponse` is an object (either a [CoreResponseData](coreresponsedata.md) or an <xref:System.Exception>) containing the result of HTTP response parsing.</span></span>

## <a name="syntax"></a><span data-ttu-id="ec78d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec78d-104">Syntax</span></span>
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> <span data-ttu-id="ec78d-105">Toto rozhraní API není určeno k použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="ec78d-105">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="ec78d-106">Místo toho byste k připojení síťového kódu měli použít <xref:System.Diagnostics.DiagnosticSource>.</span><span class="sxs-lookup"><span data-stu-id="ec78d-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="ec78d-107">Viz [uživatelská příručka pro DiagnosticSource](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="ec78d-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
> 
> <span data-ttu-id="ec78d-108">Společnost Microsoft v žádné situaci nepodporuje použití této třídy v produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ec78d-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="ec78d-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ec78d-109">Requirements</span></span>

<span data-ttu-id="ec78d-110">**Obor názvů:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="ec78d-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="ec78d-111">**Sestavení:** Systém (v System. dll)</span><span class="sxs-lookup"><span data-stu-id="ec78d-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="ec78d-112">**Verze .NET Framework:** K dispozici od verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="ec78d-112">**.NET Framework versions:** Available since 2.0.</span></span>
