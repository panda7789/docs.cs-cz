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
ms.openlocfilehash: bd1f101e2e9cf9baeb28290c7607ccab3d8d7440
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939682"
---
# <a name="isymunmanagedencupdateupdatemethodlines-method"></a><span data-ttu-id="0ee62-102">ISymUnmanagedENCUpdate::UpdateMethodLines – metoda</span><span class="sxs-lookup"><span data-stu-id="0ee62-102">ISymUnmanagedENCUpdate::UpdateMethodLines Method</span></span>
<span data-ttu-id="0ee62-103">Umožňuje aktualizovat informace o řádku pro metodu, která nebyla překompilovat, ale jejíž řádky přesunuty nezávisle na sobě.</span><span class="sxs-lookup"><span data-stu-id="0ee62-103">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="0ee62-104">Rozdílové hodnoty pro každý příkaz je povolen.</span><span class="sxs-lookup"><span data-stu-id="0ee62-104">A delta for each statement is allowed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ee62-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ee62-105">Syntax</span></span>  
  
```  
HRESULT UpdateMethodLines(  
    [in]  mdMethodDef  mdMethodToken,  
    [in, size_is(cDeltas)] INT32*  pDeltas,  
    [in]  ULONG        cDeltas);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ee62-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0ee62-106">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="0ee62-107">[in] Metadata token metody.</span><span class="sxs-lookup"><span data-stu-id="0ee62-107">[in] The metadata of the method token.</span></span>  
  
 `pDeltas`  
 <span data-ttu-id="0ee62-108">[in] Pole `INT32` hodnoty, které označuje rozdíly pro každý bod sekvence v metodě.</span><span class="sxs-lookup"><span data-stu-id="0ee62-108">[in] An array of `INT32` values that indicates deltas for each sequence point in the method.</span></span>  
  
 `cDeltas`  
 <span data-ttu-id="0ee62-109">[in] A `ULONG` obsahující velikost `pDeltas` parametru.</span><span class="sxs-lookup"><span data-stu-id="0ee62-109">[in] A `ULONG` containing the size of the `pDeltas` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0ee62-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0ee62-110">Return Value</span></span>  
 <span data-ttu-id="0ee62-111">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="0ee62-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ee62-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0ee62-112">Requirements</span></span>  
 <span data-ttu-id="0ee62-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0ee62-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ee62-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0ee62-114">See also</span></span>

- [<span data-ttu-id="0ee62-115">ISymUnmanagedENCUpdate – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0ee62-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
