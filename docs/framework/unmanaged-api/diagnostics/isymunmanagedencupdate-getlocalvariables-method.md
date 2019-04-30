---
title: ISymUnmanagedENCUpdate::GetLocalVariables – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.GetLocalVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables method [.NET Framework debugging]
- GetLocalVariables method [.NET Framework debugging]
ms.assetid: 5c8840be-ffea-447f-9c8d-178f1eaf8d06
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 16e91a0c748e5b148e79dc73cf213b03c68c5021
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939721"
---
# <a name="isymunmanagedencupdategetlocalvariables-method"></a><span data-ttu-id="87c65-102">ISymUnmanagedENCUpdate::GetLocalVariables – metoda</span><span class="sxs-lookup"><span data-stu-id="87c65-102">ISymUnmanagedENCUpdate::GetLocalVariables Method</span></span>
<span data-ttu-id="87c65-103">Získá místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="87c65-103">Gets the local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87c65-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="87c65-104">Syntax</span></span>  
  
```  
HRESULT GetLocalVariables(  
    [in]  mdMethodDef  mdMethodToken,  
    [in]  ULONG        cLocals,  
    [out, size_is(cLocals), length_is(*pceltFetched)]  
        ISymUnmanagedVariable *rgLocals[],  
    [out] ULONG        *pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87c65-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="87c65-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="87c65-106">[in] Metadata token metody.</span><span class="sxs-lookup"><span data-stu-id="87c65-106">[in] The metadata token of the method.</span></span>  
  
 `cLocals`  
 <span data-ttu-id="87c65-107">[in] A `ULONG` , který označuje velikost `rgLocals` parametru.</span><span class="sxs-lookup"><span data-stu-id="87c65-107">[in] A `ULONG` that indicates the size of the `rgLocals` parameter.</span></span>  
  
 `rgLocals`  
 <span data-ttu-id="87c65-108">[out] Vrácené pole [isymunmanagedvariable –](isymunmanagedvariable-interface.md) instancí.</span><span class="sxs-lookup"><span data-stu-id="87c65-108">[out] The returned array of [ISymUnmanagedVariable](isymunmanagedvariable-interface.md) instances.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="87c65-109">[out] Ukazatel `ULONG` , která obdrží velikost `rgLocals` vyrovnávací paměti musí obsahovat oknech místní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="87c65-109">[out] A pointer to a `ULONG` that receives the size of the `rgLocals` buffer required to contain the locals.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="87c65-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="87c65-110">Return Value</span></span>  
 <span data-ttu-id="87c65-111">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="87c65-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87c65-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="87c65-112">Requirements</span></span>  
 <span data-ttu-id="87c65-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="87c65-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87c65-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="87c65-114">See also</span></span>

- [<span data-ttu-id="87c65-115">ISymUnmanagedENCUpdate – rozhraní</span><span class="sxs-lookup"><span data-stu-id="87c65-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
