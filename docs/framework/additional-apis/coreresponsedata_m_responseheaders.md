---
title: CoreResponseData. m_ResponseHeaders – pole
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
ms.openlocfilehash: df0b592a5f85d4c99dee4ecb60963f4abb560a13
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741003"
---
# <a name="coreresponsedatam_responseheaders-field"></a><span data-ttu-id="06885-102">CoreResponseData. m\_pole ResponseHeaders hostitele</span><span class="sxs-lookup"><span data-stu-id="06885-102">CoreResponseData.m\_ResponseHeaders Field</span></span>

<span data-ttu-id="06885-103">`CoreResponseData.m_ResponseHeaders` je <xref:System.Net.WebHeaderCollection> hlaviček přidružených k odpovědi serveru.</span><span class="sxs-lookup"><span data-stu-id="06885-103">`CoreResponseData.m_ResponseHeaders` is a <xref:System.Net.WebHeaderCollection> of headers associated with the server response.</span></span>

## <a name="syntax"></a><span data-ttu-id="06885-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06885-104">Syntax</span></span>
  
```csharp
public WebHeaderCollection m_ResponseHeaders
```

> [!WARNING]
> <span data-ttu-id="06885-105">Toto rozhraní API není určeno k použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="06885-105">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="06885-106">Místo toho byste k připojení síťového kódu měli použít <xref:System.Diagnostics.DiagnosticSource>.</span><span class="sxs-lookup"><span data-stu-id="06885-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="06885-107">Viz [uživatelská příručka pro DiagnosticSource](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="06885-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
> 
> <span data-ttu-id="06885-108">Společnost Microsoft v žádné situaci nepodporuje použití této třídy v produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="06885-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="06885-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="06885-109">Requirements</span></span>

<span data-ttu-id="06885-110">**Obor názvů:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="06885-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="06885-111">**Sestavení:** Systém (v System. dll)</span><span class="sxs-lookup"><span data-stu-id="06885-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="06885-112">**Verze .NET Framework:** K dispozici od verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="06885-112">**.NET Framework versions:** Available since 2.0.</span></span>
