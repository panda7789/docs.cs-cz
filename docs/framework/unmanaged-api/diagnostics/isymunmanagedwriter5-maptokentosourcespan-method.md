---
title: ISymUnmanagedWriter5::MapTokenToSourceSpan – metoda
ms.date: 03/30/2017
ms.assetid: d0fbbf61-71c6-4fb1-8c9f-d619ca5d7d68
ms.openlocfilehash: f5898cab08f332314fb33684399dcb4f2ff71cc7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609453"
---
# <a name="isymunmanagedwriter5maptokentosourcespan-method"></a><span data-ttu-id="d343f-102">ISymUnmanagedWriter5::MapTokenToSourceSpan – metoda</span><span class="sxs-lookup"><span data-stu-id="d343f-102">ISymUnmanagedWriter5::MapTokenToSourceSpan Method</span></span>
<span data-ttu-id="d343f-103">Mapuje daný token metadat na zadaný rozsah řádku zdroje v zadaném zdrojovém souboru.</span><span class="sxs-lookup"><span data-stu-id="d343f-103">Maps the given metadata token to the given source line span in the specified source file.</span></span>  
  
 <span data-ttu-id="d343f-104">Musí být volána mezi voláním [metody openmaptokenstosourcespans –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) a [metodou closemaptokenstosourcespans –](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="d343f-104">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d343f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d343f-105">Syntax</span></span>  
  
```idl  
HRESULT MapTokenToSourceSpan(    [in] mdToken token,    [in] ISymUnmanagedDocumentWriter* document,    [in] ULONG32 line,    [in] ULONG32 column,    [in] ULONG32 endLine,    [in] ULONG32 endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d343f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d343f-106">Parameters</span></span>  
  
|<span data-ttu-id="d343f-107">Parametr</span><span class="sxs-lookup"><span data-stu-id="d343f-107">Parameter</span></span>|<span data-ttu-id="d343f-108">Popis</span><span class="sxs-lookup"><span data-stu-id="d343f-108">Description</span></span>|  
|---------------|-----------------|  
|`token`||  
|`document`||  
|`line`||  
|`column`||  
|`endLine`||  
|`endColumn`||  
  
## <a name="return-value"></a><span data-ttu-id="d343f-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d343f-109">Return Value</span></span>  
 <span data-ttu-id="d343f-110">Vrací objekt `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="d343f-110">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d343f-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d343f-111">Requirements</span></span>  
 <span data-ttu-id="d343f-112">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="d343f-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d343f-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="d343f-113">See also</span></span>

- [<span data-ttu-id="d343f-114">ISymUnmanagedWriter5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d343f-114">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)
