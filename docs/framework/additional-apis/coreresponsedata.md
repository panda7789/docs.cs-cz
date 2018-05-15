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
ms.openlocfilehash: 640a925c3aec86b4743b1b2b62eb3793af1cc0bb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="coreresponsedata-class"></a><span data-ttu-id="908f1-102">CoreResponseData – třída</span><span class="sxs-lookup"><span data-stu-id="908f1-102">CoreResponseData Class</span></span>

<span data-ttu-id="908f1-103">`CoreResponseData` Třída reprezentuje analýza hlaviček protokolu HTTP a text odpovědi.</span><span class="sxs-lookup"><span data-stu-id="908f1-103">The `CoreResponseData` class represents the parsing of the HTTP headers and the response body.</span></span>

## <a name="syntax"></a><span data-ttu-id="908f1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="908f1-104">Syntax</span></span>
  
```csharp
internal class CoreResponseData
```

> [!WARNING]
> <span data-ttu-id="908f1-105">Toto rozhraní API je interní a není určen pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="908f1-105">This API is internal, and it is not meant to be used directly in your code.</span></span> <span data-ttu-id="908f1-106">Místo toho používejte <xref:System.Diagnostics.DiagnosticSource> napojit sítě kódu.</span><span class="sxs-lookup"><span data-stu-id="908f1-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="908f1-107">V tématu [DiagnosticSource uživatelská příručka](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="908f1-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
> 
> <span data-ttu-id="908f1-108">Společnost Microsoft nepodporuje použití této třídy v produkční aplikace za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="908f1-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="908f1-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="908f1-109">Requirements</span></span>

<span data-ttu-id="908f1-110">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="908f1-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="908f1-111">**Sestavení:** systému (v System.dll)</span><span class="sxs-lookup"><span data-stu-id="908f1-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="908f1-112">**Verze rozhraní .NET framework:** dostupné od verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="908f1-112">**.NET Framework versions:** Available since 2.0.</span></span>
