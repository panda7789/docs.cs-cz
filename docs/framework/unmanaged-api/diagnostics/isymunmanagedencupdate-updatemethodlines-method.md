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
ms.openlocfilehash: 9aace77c4b3549c033433d4c305b07daa1f7a8c1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448992"
---
# <a name="isymunmanagedencupdateupdatemethodlines-method"></a><span data-ttu-id="1a3b0-102">ISymUnmanagedENCUpdate::UpdateMethodLines – metoda</span><span class="sxs-lookup"><span data-stu-id="1a3b0-102">ISymUnmanagedENCUpdate::UpdateMethodLines Method</span></span>
<span data-ttu-id="1a3b0-103">Umožňuje aktualizovat informace o řádku pro metodu, která není znovu zkompilována, ale jejíž řádky byly přesunuty nezávisle.</span><span class="sxs-lookup"><span data-stu-id="1a3b0-103">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="1a3b0-104">Rozdíl pro každý příkaz je povolen.</span><span class="sxs-lookup"><span data-stu-id="1a3b0-104">A delta for each statement is allowed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a3b0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a3b0-105">Syntax</span></span>  
  
```cpp  
HRESULT UpdateMethodLines(  
    [in]  mdMethodDef  mdMethodToken,  
    [in, size_is(cDeltas)] INT32*  pDeltas,  
    [in]  ULONG        cDeltas);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a3b0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1a3b0-106">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="1a3b0-107">pro Metadata tokenu metody.</span><span class="sxs-lookup"><span data-stu-id="1a3b0-107">[in] The metadata of the method token.</span></span>  
  
 `pDeltas`  
 <span data-ttu-id="1a3b0-108">pro Pole hodnot `INT32`, které označují rozdílové hodnoty pro každý bod sekvence v metodě.</span><span class="sxs-lookup"><span data-stu-id="1a3b0-108">[in] An array of `INT32` values that indicates deltas for each sequence point in the method.</span></span>  
  
 `cDeltas`  
 <span data-ttu-id="1a3b0-109">pro `ULONG`, který obsahuje velikost `pDeltas` parametru.</span><span class="sxs-lookup"><span data-stu-id="1a3b0-109">[in] A `ULONG` containing the size of the `pDeltas` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1a3b0-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1a3b0-110">Return Value</span></span>  
 <span data-ttu-id="1a3b0-111">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="1a3b0-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a3b0-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1a3b0-112">Requirements</span></span>  
 <span data-ttu-id="1a3b0-113">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="1a3b0-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a3b0-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1a3b0-114">See also</span></span>

- [<span data-ttu-id="1a3b0-115">ISymUnmanagedENCUpdate – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1a3b0-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
