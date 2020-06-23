---
title: CoreResponseData. m_ResponseHeaders – pole
description: Porozumět poli CoreResponseData. m_ResponseHeaders v .NET. Toto pole je typ WebHeaderCollection, který obsahuje hlavičky přidružené k odpovědi serveru.
ms.date: 01/29/2018
topic_type:
- apiref
api_name:
- System.Net.CoreResponseData.m_ResponseHeaders
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.openlocfilehash: 7c7b896193cb81e9fc9e3ec28110359003a36728
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989788"
---
# <a name="coreresponsedatam_responseheaders-field"></a><span data-ttu-id="f4095-104">CoreResponseData. m \_ ResponseHeaders hostitele – pole</span><span class="sxs-lookup"><span data-stu-id="f4095-104">CoreResponseData.m\_ResponseHeaders Field</span></span>

<span data-ttu-id="f4095-105">`CoreResponseData.m_ResponseHeaders`je hlavičkou, která je <xref:System.Net.WebHeaderCollection> přidružená k odpovědi serveru.</span><span class="sxs-lookup"><span data-stu-id="f4095-105">`CoreResponseData.m_ResponseHeaders` is a <xref:System.Net.WebHeaderCollection> of headers associated with the server response.</span></span>

## <a name="syntax"></a><span data-ttu-id="f4095-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="f4095-106">Syntax</span></span>
  
```csharp
public WebHeaderCollection m_ResponseHeaders
```

> [!WARNING]
> <span data-ttu-id="f4095-107">Toto rozhraní API není určeno k použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="f4095-107">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="f4095-108">Místo toho byste měli použít <xref:System.Diagnostics.DiagnosticSource> k zavěšení síťového kódu.</span><span class="sxs-lookup"><span data-stu-id="f4095-108">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="f4095-109">Viz [uživatelská příručka pro DiagnosticSource](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="f4095-109">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
>
> <span data-ttu-id="f4095-110">Společnost Microsoft v žádné situaci nepodporuje použití této třídy v produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f4095-110">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="f4095-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f4095-111">Requirements</span></span>

<span data-ttu-id="f4095-112">**Obor názvů:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="f4095-112">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="f4095-113">**Sestavení:** Systém (v System.dll)</span><span class="sxs-lookup"><span data-stu-id="f4095-113">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="f4095-114">**Verze .NET Framework:** K dispozici od verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="f4095-114">**.NET Framework versions:** Available since 2.0.</span></span>
