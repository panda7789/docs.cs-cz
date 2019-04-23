---
title: ISymUnmanagedWriter5::MapTokenToSourceSpan – metoda
ms.date: 03/30/2017
ms.assetid: d0fbbf61-71c6-4fb1-8c9f-d619ca5d7d68
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08c219dd033b39fc07159875b184cdf70e3aa3ed
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59181516"
---
# <a name="isymunmanagedwriter5maptokentosourcespan-method"></a><span data-ttu-id="25477-102">ISymUnmanagedWriter5::MapTokenToSourceSpan – metoda</span><span class="sxs-lookup"><span data-stu-id="25477-102">ISymUnmanagedWriter5::MapTokenToSourceSpan Method</span></span>
<span data-ttu-id="25477-103">Mapy token daná metadata do daného zdroje řádku span zadaného zdrojového souboru.</span><span class="sxs-lookup"><span data-stu-id="25477-103">Maps the given metadata token to the given source line span in the specified source file.</span></span>  
  
 <span data-ttu-id="25477-104">Musí být volána mezi voláními [openmaptokenstosourcespans – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) a [closemaptokenstosourcespans – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="25477-104">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25477-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25477-105">Syntax</span></span>  
  
```idl  
HRESULT MapTokenToSourceSpan(    [in] mdToken token,    [in] ISymUnmanagedDocumentWriter* document,    [in] ULONG32 line,    [in] ULONG32 column,    [in] ULONG32 endLine,    [in] ULONG32 endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25477-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="25477-106">Parameters</span></span>  
  
|<span data-ttu-id="25477-107">Parametr</span><span class="sxs-lookup"><span data-stu-id="25477-107">Parameter</span></span>|<span data-ttu-id="25477-108">Popis</span><span class="sxs-lookup"><span data-stu-id="25477-108">Description</span></span>|  
|---------------|-----------------|  
|`token`||  
|`document`||  
|`line`||  
|`column`||  
|`endLine`||  
|`endColumn`||  
  
## <a name="return-value"></a><span data-ttu-id="25477-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="25477-109">Return Value</span></span>  
 <span data-ttu-id="25477-110">Vrátí `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="25477-110">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25477-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="25477-111">Requirements</span></span>  
 <span data-ttu-id="25477-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="25477-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25477-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="25477-113">See also</span></span>

- [<span data-ttu-id="25477-114">ISymUnmanagedWriter5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="25477-114">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
