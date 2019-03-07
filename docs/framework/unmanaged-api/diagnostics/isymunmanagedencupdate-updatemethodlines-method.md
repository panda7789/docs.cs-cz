---
title: ISymUnmanagedENCUpdate::UpdateMethodLines – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.UpdateMethodLines
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::UpdateMethodLines
helpviewer_keywords:
- UpdateMethodLines method [.NET Framework debugging]
- ISymUnmanagedENCUpdate::UpdateMethodLines method [.NET Framework debugging]
ms.assetid: 275ef87b-0b53-49f9-af6b-58506335dc06
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 226d9aa75d0a9e4d6cef92e2d2edacb6e98cf34e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57473053"
---
# <a name="isymunmanagedencupdateupdatemethodlines-method"></a><span data-ttu-id="ebc9b-102">ISymUnmanagedENCUpdate::UpdateMethodLines – metoda</span><span class="sxs-lookup"><span data-stu-id="ebc9b-102">ISymUnmanagedENCUpdate::UpdateMethodLines Method</span></span>
<span data-ttu-id="ebc9b-103">Umožňuje aktualizovat informace o řádku pro metodu, která nebyla překompilovat, ale jejíž řádky přesunuty nezávisle na sobě.</span><span class="sxs-lookup"><span data-stu-id="ebc9b-103">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="ebc9b-104">Rozdílové hodnoty pro každý příkaz je povolen.</span><span class="sxs-lookup"><span data-stu-id="ebc9b-104">A delta for each statement is allowed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebc9b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ebc9b-105">Syntax</span></span>  
  
```  
HRESULT UpdateMethodLines(  
    [in]  mdMethodDef  mdMethodToken,  
    [in, size_is(cDeltas)] INT32*  pDeltas,  
    [in]  ULONG        cDeltas);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ebc9b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ebc9b-106">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="ebc9b-107">[in] Metadata token metody.</span><span class="sxs-lookup"><span data-stu-id="ebc9b-107">[in] The metadata of the method token.</span></span>  
  
 `pDeltas`  
 <span data-ttu-id="ebc9b-108">[in] Pole `INT32` hodnoty, které označuje rozdíly pro každý bod sekvence v metodě.</span><span class="sxs-lookup"><span data-stu-id="ebc9b-108">[in] An array of `INT32` values that indicates deltas for each sequence point in the method.</span></span>  
  
 `cDeltas`  
 <span data-ttu-id="ebc9b-109">[in] A `ULONG` obsahující velikost `pDeltas` parametru.</span><span class="sxs-lookup"><span data-stu-id="ebc9b-109">[in] A `ULONG` containing the size of the `pDeltas` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ebc9b-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ebc9b-110">Return Value</span></span>  
 <span data-ttu-id="ebc9b-111">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="ebc9b-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebc9b-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ebc9b-112">Requirements</span></span>  
 <span data-ttu-id="ebc9b-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ebc9b-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebc9b-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ebc9b-114">See also</span></span>
- [<span data-ttu-id="ebc9b-115">ISymUnmanagedENCUpdate – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ebc9b-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
