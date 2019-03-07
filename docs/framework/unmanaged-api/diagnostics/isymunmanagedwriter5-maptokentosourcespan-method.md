---
title: ISymUnmanagedWriter5::MapTokenToSourceSpan – metoda
ms.date: 03/30/2017
ms.assetid: d0fbbf61-71c6-4fb1-8c9f-d619ca5d7d68
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf061de3e75550e33ba67c1d624279b1673c5382
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57465333"
---
# <a name="isymunmanagedwriter5maptokentosourcespan-method"></a><span data-ttu-id="35993-102">ISymUnmanagedWriter5::MapTokenToSourceSpan – metoda</span><span class="sxs-lookup"><span data-stu-id="35993-102">ISymUnmanagedWriter5::MapTokenToSourceSpan Method</span></span>
<span data-ttu-id="35993-103">Mapy token daná metadata do daného zdroje řádku span zadaného zdrojového souboru.</span><span class="sxs-lookup"><span data-stu-id="35993-103">Maps the given metadata token to the given source line span in the specified source file.</span></span>  
  
 <span data-ttu-id="35993-104">Musí být volána mezi voláními [openmaptokenstosourcespans – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) a [closemaptokenstosourcespans – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="35993-104">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35993-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="35993-105">Syntax</span></span>  
  
```idl  
HRESULT MapTokenToSourceSpan(    [in] mdToken token,    [in] ISymUnmanagedDocumentWriter* document,    [in] ULONG32 line,    [in] ULONG32 column,    [in] ULONG32 endLine,    [in] ULONG32 endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="35993-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="35993-106">Parameters</span></span>  
  
|<span data-ttu-id="35993-107">Parametr</span><span class="sxs-lookup"><span data-stu-id="35993-107">Parameter</span></span>|<span data-ttu-id="35993-108">Popis</span><span class="sxs-lookup"><span data-stu-id="35993-108">Description</span></span>|  
|---------------|-----------------|  
|`token`||  
|`document`||  
|`line`||  
|`column`||  
|`endLine`||  
|`endColumn`||  
  
## <a name="return-value"></a><span data-ttu-id="35993-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="35993-109">Return Value</span></span>  
 <span data-ttu-id="35993-110">Vrátí `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="35993-110">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35993-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="35993-111">Requirements</span></span>  
 <span data-ttu-id="35993-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="35993-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35993-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="35993-113">See also</span></span>
- [<span data-ttu-id="35993-114">ISymUnmanagedWriter5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="35993-114">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
