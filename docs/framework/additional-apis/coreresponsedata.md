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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675413"
---
# <a name="coreresponsedata-class"></a><span data-ttu-id="dbd2d-102">CoreResponseData – třída</span><span class="sxs-lookup"><span data-stu-id="dbd2d-102">CoreResponseData Class</span></span>

<span data-ttu-id="dbd2d-103">`CoreResponseData` Třída představuje, analýze hlavičky protokolu HTTP a text odpovědi.</span><span class="sxs-lookup"><span data-stu-id="dbd2d-103">The `CoreResponseData` class represents the parsing of the HTTP headers and the response body.</span></span>

## <a name="syntax"></a><span data-ttu-id="dbd2d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dbd2d-104">Syntax</span></span>
  
```csharp
internal class CoreResponseData
```

> [!WARNING]
> <span data-ttu-id="dbd2d-105">Toto rozhraní API je interní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="dbd2d-105">This API is internal, and it is not meant to be used directly in your code.</span></span> <span data-ttu-id="dbd2d-106">Místo toho používejte <xref:System.Diagnostics.DiagnosticSource> k připojení sítě kódu.</span><span class="sxs-lookup"><span data-stu-id="dbd2d-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="dbd2d-107">Zobrazit [DiagnosticSource uživatelská příručka](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="dbd2d-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
> 
> <span data-ttu-id="dbd2d-108">Microsoft nepodporuje použití této třídy v produkční aplikace za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="dbd2d-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="dbd2d-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dbd2d-109">Requirements</span></span>

<span data-ttu-id="dbd2d-110">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="dbd2d-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="dbd2d-111">**Sestavení:** Systém (System.dll)</span><span class="sxs-lookup"><span data-stu-id="dbd2d-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="dbd2d-112">**Verze rozhraní .NET framework:** Dostupné od verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="dbd2d-112">**.NET Framework versions:** Available since 2.0.</span></span>
