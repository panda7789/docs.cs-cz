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
ms.openlocfilehash: 50d9ac08b01a67df68ff077721ff5421fbc27707
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424271"
---
# <a name="isymunmanagedencupdateupdatemethodlines-method"></a><span data-ttu-id="e3c2a-102">ISymUnmanagedENCUpdate::UpdateMethodLines – metoda</span><span class="sxs-lookup"><span data-stu-id="e3c2a-102">ISymUnmanagedENCUpdate::UpdateMethodLines Method</span></span>
<span data-ttu-id="e3c2a-103">Umožňuje aktualizaci řádku informace pro metodu, která nebyla překompilovat, ale jejichž řádky byl přesunut nezávisle.</span><span class="sxs-lookup"><span data-stu-id="e3c2a-103">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="e3c2a-104">Rozdílové každý příkaz je povolen.</span><span class="sxs-lookup"><span data-stu-id="e3c2a-104">A delta for each statement is allowed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3c2a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3c2a-105">Syntax</span></span>  
  
```  
HRESULT UpdateMethodLines(  
    [in]  mdMethodDef  mdMethodToken,  
    [in, size_is(cDeltas)] INT32*  pDeltas,  
    [in]  ULONG        cDeltas);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e3c2a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e3c2a-106">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="e3c2a-107">[v] Metadata metoda tokenu.</span><span class="sxs-lookup"><span data-stu-id="e3c2a-107">[in] The metadata of the method token.</span></span>  
  
 `pDeltas`  
 <span data-ttu-id="e3c2a-108">[v] Pole `INT32` hodnoty, které označuje rozdíly pro každý bod pořadí v metodě.</span><span class="sxs-lookup"><span data-stu-id="e3c2a-108">[in] An array of `INT32` values that indicates deltas for each sequence point in the method.</span></span>  
  
 `cDeltas`  
 <span data-ttu-id="e3c2a-109">[v] A `ULONG` obsahující velikost `pDeltas` parametr.</span><span class="sxs-lookup"><span data-stu-id="e3c2a-109">[in] A `ULONG` containing the size of the `pDeltas` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e3c2a-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e3c2a-110">Return Value</span></span>  
 <span data-ttu-id="e3c2a-111">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="e3c2a-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3c2a-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e3c2a-112">Requirements</span></span>  
 <span data-ttu-id="e3c2a-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e3c2a-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3c2a-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="e3c2a-114">See Also</span></span>  
 [<span data-ttu-id="e3c2a-115">ISymUnmanagedENCUpdate – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e3c2a-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
