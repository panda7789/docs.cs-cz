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
ms.openlocfilehash: 9a490299c24f44b59da682f714f4b696fde3cba5
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614510"
---
# <a name="isymunmanagedencupdateupdatemethodlines-method"></a><span data-ttu-id="654e2-102">ISymUnmanagedENCUpdate::UpdateMethodLines – metoda</span><span class="sxs-lookup"><span data-stu-id="654e2-102">ISymUnmanagedENCUpdate::UpdateMethodLines Method</span></span>
<span data-ttu-id="654e2-103">Umožňuje aktualizovat informace o řádku pro metodu, která není znovu zkompilována, ale jejíž řádky byly přesunuty nezávisle.</span><span class="sxs-lookup"><span data-stu-id="654e2-103">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="654e2-104">Rozdíl pro každý příkaz je povolen.</span><span class="sxs-lookup"><span data-stu-id="654e2-104">A delta for each statement is allowed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="654e2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="654e2-105">Syntax</span></span>  
  
```cpp  
HRESULT UpdateMethodLines(  
    [in]  mdMethodDef  mdMethodToken,  
    [in, size_is(cDeltas)] INT32*  pDeltas,  
    [in]  ULONG        cDeltas);  
```  
  
## <a name="parameters"></a><span data-ttu-id="654e2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="654e2-106">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="654e2-107">pro Metadata tokenu metody.</span><span class="sxs-lookup"><span data-stu-id="654e2-107">[in] The metadata of the method token.</span></span>  
  
 `pDeltas`  
 <span data-ttu-id="654e2-108">pro Pole `INT32` hodnot, které označují rozdílové hodnoty pro každý bod sekvence v metodě.</span><span class="sxs-lookup"><span data-stu-id="654e2-108">[in] An array of `INT32` values that indicates deltas for each sequence point in the method.</span></span>  
  
 `cDeltas`  
 <span data-ttu-id="654e2-109">pro A `ULONG` obsahující velikost `pDeltas` parametru.</span><span class="sxs-lookup"><span data-stu-id="654e2-109">[in] A `ULONG` containing the size of the `pDeltas` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="654e2-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="654e2-110">Return Value</span></span>  
 <span data-ttu-id="654e2-111">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="654e2-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="654e2-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="654e2-112">Requirements</span></span>  
 <span data-ttu-id="654e2-113">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="654e2-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="654e2-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="654e2-114">See also</span></span>

- [<span data-ttu-id="654e2-115">ISymUnmanagedENCUpdate – rozhraní</span><span class="sxs-lookup"><span data-stu-id="654e2-115">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)
