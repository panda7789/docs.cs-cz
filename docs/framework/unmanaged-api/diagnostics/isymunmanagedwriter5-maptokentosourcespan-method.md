---
title: ISymUnmanagedWriter5::MapTokenToSourceSpan – metoda
ms.date: 03/30/2017
ms.assetid: d0fbbf61-71c6-4fb1-8c9f-d619ca5d7d68
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7751ed951c213c52c68125543622ed110124f5b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427940"
---
# <a name="isymunmanagedwriter5maptokentosourcespan-method"></a><span data-ttu-id="cd5c8-102">ISymUnmanagedWriter5::MapTokenToSourceSpan – metoda</span><span class="sxs-lookup"><span data-stu-id="cd5c8-102">ISymUnmanagedWriter5::MapTokenToSourceSpan Method</span></span>
<span data-ttu-id="cd5c8-103">Mapuje token daná metadata na ose zadaná zdrojová span v zadaný zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="cd5c8-103">Maps the given metadata token to the given source line span in the specified source file.</span></span>  
  
 <span data-ttu-id="cd5c8-104">Musí být voláno mezi volání [openmaptokenstosourcespans – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) a [closemaptokenstosourcespans – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="cd5c8-104">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd5c8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd5c8-105">Syntax</span></span>  
  
```idl  
HRESULT MapTokenToSourceSpan(    [in] mdToken token,    [in] ISymUnmanagedDocumentWriter* document,    [in] ULONG32 line,    [in] ULONG32 column,    [in] ULONG32 endLine,    [in] ULONG32 endColumn);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cd5c8-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="cd5c8-106">Parameters</span></span>  
  
|<span data-ttu-id="cd5c8-107">Parametr</span><span class="sxs-lookup"><span data-stu-id="cd5c8-107">Parameter</span></span>|<span data-ttu-id="cd5c8-108">Popis</span><span class="sxs-lookup"><span data-stu-id="cd5c8-108">Description</span></span>|  
|---------------|-----------------|  
|`token`||  
|`document`||  
|`line`||  
|`column`||  
|`endLine`||  
|`endColumn`||  
  
## <a name="return-value"></a><span data-ttu-id="cd5c8-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="cd5c8-109">Return Value</span></span>  
 <span data-ttu-id="cd5c8-110">Vrátí `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="cd5c8-110">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd5c8-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cd5c8-111">Requirements</span></span>  
 <span data-ttu-id="cd5c8-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="cd5c8-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd5c8-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="cd5c8-113">See Also</span></span>  
 [<span data-ttu-id="cd5c8-114">ISymUnmanagedWriter5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cd5c8-114">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
