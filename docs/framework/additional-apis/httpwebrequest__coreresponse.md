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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706062"
---
# <a name="httpwebrequestcoreresponse-field"></a><span data-ttu-id="5000c-102">HttpWebRequest. \_CoreResponse pole</span><span class="sxs-lookup"><span data-stu-id="5000c-102">HttpWebRequest.\_CoreResponse Field</span></span>

<span data-ttu-id="5000c-103">`HttpWebRequest._CoreResponse` je objekt (buď [CoreResponseData](coreresponsedata.md) nebo <xref:System.Exception>) obsahující výsledky analýzy odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="5000c-103">`HttpWebRequest._CoreResponse` is an object (either a [CoreResponseData](coreresponsedata.md) or an <xref:System.Exception>) containing the result of HTTP response parsing.</span></span>

## <a name="syntax"></a><span data-ttu-id="5000c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5000c-104">Syntax</span></span>
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> <span data-ttu-id="5000c-105">Toto rozhraní API není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="5000c-105">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="5000c-106">Místo toho používejte <xref:System.Diagnostics.DiagnosticSource> k připojení sítě kódu.</span><span class="sxs-lookup"><span data-stu-id="5000c-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="5000c-107">Zobrazit [DiagnosticSource uživatelská příručka](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="5000c-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
> 
> <span data-ttu-id="5000c-108">Microsoft nepodporuje použití této třídy v produkční aplikace za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="5000c-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="5000c-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5000c-109">Requirements</span></span>

<span data-ttu-id="5000c-110">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="5000c-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="5000c-111">**Sestavení:** Systém (System.dll)</span><span class="sxs-lookup"><span data-stu-id="5000c-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="5000c-112">**Verze rozhraní .NET framework:** Dostupné od verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="5000c-112">**.NET Framework versions:** Available since 2.0.</span></span>
