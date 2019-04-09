---
title: ISymUnmanagedMethod::GetParameters – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetParameters
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetParameters
helpviewer_keywords:
- ISymUnmanagedMethod::GetParameters method [.NET Framework debugging]
- GetParameters method [.NET Framework debugging]
ms.assetid: 3a8074f1-facc-4a3f-bb9b-d6574fc2fc74
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9a757e3b28a94c96e28a5bab736a6820a83617a3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101201"
---
# <a name="isymunmanagedmethodgetparameters-method"></a><span data-ttu-id="32187-102">ISymUnmanagedMethod::GetParameters – metoda</span><span class="sxs-lookup"><span data-stu-id="32187-102">ISymUnmanagedMethod::GetParameters Method</span></span>
<span data-ttu-id="32187-103">Získá parametry pro tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="32187-103">Gets the parameters for this method.</span></span> <span data-ttu-id="32187-104">Parametry jsou vráceny v pořadí, ve kterém jsou definovány v podpisu metody.</span><span class="sxs-lookup"><span data-stu-id="32187-104">The parameters are returned in the order in which they are defined within the method's signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32187-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32187-105">Syntax</span></span>  
  
```  
HRESULT GetParameters(  
    [in]  ULONG32  cParams,  
    [out] ULONG32  *pcParams,  
    [out, size_is(cParams),  
        length_is(*pcParams)] ISymUnmanagedVariable*  params[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32187-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="32187-106">Parameters</span></span>  
 `cParams`  
 <span data-ttu-id="32187-107">[in] Velikost `params` pole.</span><span class="sxs-lookup"><span data-stu-id="32187-107">[in] The size of the `params` array.</span></span>  
  
 `pcParams`  
 <span data-ttu-id="32187-108">[in] Ukazatel `ULONG32` , která obdrží velikost vyrovnávací paměti, který musí obsahovat parametry.</span><span class="sxs-lookup"><span data-stu-id="32187-108">[in] A pointer to a `ULONG32` that receives the size of the buffer that is required to contain the parameters.</span></span>  
  
 `params`  
 <span data-ttu-id="32187-109">[out] Ukazatel do vyrovnávací paměti, která přijímá parametry.</span><span class="sxs-lookup"><span data-stu-id="32187-109">[out] A pointer to the buffer that receives the parameters.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="32187-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="32187-110">Return Value</span></span>  
 <span data-ttu-id="32187-111">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="32187-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32187-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="32187-112">Requirements</span></span>  
 <span data-ttu-id="32187-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="32187-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32187-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="32187-114">See also</span></span>

- [<span data-ttu-id="32187-115">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="32187-115">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
