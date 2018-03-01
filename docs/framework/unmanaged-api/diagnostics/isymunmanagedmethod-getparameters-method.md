---
title: "ISymUnmanagedMethod::GetParameters – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1a2e3471b63f819bfe1879b87e42ff9258036356
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedmethodgetparameters-method"></a><span data-ttu-id="92273-102">ISymUnmanagedMethod::GetParameters – metoda</span><span class="sxs-lookup"><span data-stu-id="92273-102">ISymUnmanagedMethod::GetParameters Method</span></span>
<span data-ttu-id="92273-103">Získá parametry pro tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="92273-103">Gets the parameters for this method.</span></span> <span data-ttu-id="92273-104">Parametry jsou vráceny v pořadí, ve kterém jsou definovány v rámci signatury metody.</span><span class="sxs-lookup"><span data-stu-id="92273-104">The parameters are returned in the order in which they are defined within the method's signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92273-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92273-105">Syntax</span></span>  
  
```  
HRESULT GetParameters(  
    [in]  ULONG32  cParams,  
    [out] ULONG32  *pcParams,  
    [out, size_is(cParams),  
        length_is(*pcParams)] ISymUnmanagedVariable*  params[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="92273-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="92273-106">Parameters</span></span>  
 `cParams`  
 <span data-ttu-id="92273-107">[v] Velikost `params` pole.</span><span class="sxs-lookup"><span data-stu-id="92273-107">[in] The size of the `params` array.</span></span>  
  
 `pcParams`  
 <span data-ttu-id="92273-108">[v] Ukazatel na `ULONG32` která přijme velikost vyrovnávací paměti, kterou musí obsahovat parametry.</span><span class="sxs-lookup"><span data-stu-id="92273-108">[in] A pointer to a `ULONG32` that receives the size of the buffer that is required to contain the parameters.</span></span>  
  
 `params`  
 <span data-ttu-id="92273-109">[out] Ukazatel do vyrovnávací paměti, která přijímá parametry.</span><span class="sxs-lookup"><span data-stu-id="92273-109">[out] A pointer to the buffer that receives the parameters.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="92273-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="92273-110">Return Value</span></span>  
 <span data-ttu-id="92273-111">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="92273-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92273-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="92273-112">Requirements</span></span>  
 <span data-ttu-id="92273-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="92273-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92273-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="92273-114">See Also</span></span>  
 [<span data-ttu-id="92273-115">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="92273-115">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
