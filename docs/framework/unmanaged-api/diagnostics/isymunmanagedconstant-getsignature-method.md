---
title: ISymUnmanagedConstant::GetSignature – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetSignature
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetSignature
helpviewer_keywords:
- GetSignature method, ISymUnmanagedConstant interface [.NET Framework debugging]
- ISymUnmanagedConstant::GetSignature method [.NET Framework debugging]
ms.assetid: 3eb41151-a228-43e3-ba8f-e6dd3ceb8542
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ab1282109d7241c2599f8ca029fc79e4a3135209
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59170986"
---
# <a name="isymunmanagedconstantgetsignature-method"></a><span data-ttu-id="8a021-102">ISymUnmanagedConstant::GetSignature – metoda</span><span class="sxs-lookup"><span data-stu-id="8a021-102">ISymUnmanagedConstant::GetSignature Method</span></span>
<span data-ttu-id="8a021-103">Získá podpis konstanty.</span><span class="sxs-lookup"><span data-stu-id="8a021-103">Gets the signature of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a021-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8a021-104">Syntax</span></span>  
  
```  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a021-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8a021-105">Parameters</span></span>  
 `cSig`  
 <span data-ttu-id="8a021-106">[in] Délka vyrovnávací paměti, která `pcSig` parametr odkazuje na.</span><span class="sxs-lookup"><span data-stu-id="8a021-106">[in] The length of the buffer that the `pcSig` parameter points to.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="8a021-107">[out] Ukazatel `ULONG32` , která obdrží velikost ve znacích, vyrovnávací paměti musí obsahovat podpis.</span><span class="sxs-lookup"><span data-stu-id="8a021-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="8a021-108">[out] Vyrovnávací paměť, která ukládá podpis.</span><span class="sxs-lookup"><span data-stu-id="8a021-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8a021-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8a021-109">Return Value</span></span>  
 <span data-ttu-id="8a021-110">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="8a021-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a021-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8a021-111">Requirements</span></span>  
 <span data-ttu-id="8a021-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8a021-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a021-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8a021-113">See also</span></span>

- [<span data-ttu-id="8a021-114">ISymUnmanagedConstant – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8a021-114">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)
- [<span data-ttu-id="8a021-115">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="8a021-115">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="8a021-116">GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="8a021-116">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)
