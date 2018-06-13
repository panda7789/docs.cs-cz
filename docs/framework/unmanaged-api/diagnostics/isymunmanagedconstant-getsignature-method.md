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
ms.openlocfilehash: ce9ce768e32434e0a1acd2fad67a0cdc99f49e18
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430143"
---
# <a name="isymunmanagedconstantgetsignature-method"></a><span data-ttu-id="d9e66-102">ISymUnmanagedConstant::GetSignature – metoda</span><span class="sxs-lookup"><span data-stu-id="d9e66-102">ISymUnmanagedConstant::GetSignature Method</span></span>
<span data-ttu-id="d9e66-103">Získá podpis konstanty.</span><span class="sxs-lookup"><span data-stu-id="d9e66-103">Gets the signature of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9e66-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d9e66-104">Syntax</span></span>  
  
```  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d9e66-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d9e66-105">Parameters</span></span>  
 `cSig`  
 <span data-ttu-id="d9e66-106">[v] Délka vyrovnávací paměti, která `pcSig` parametr odkazuje na.</span><span class="sxs-lookup"><span data-stu-id="d9e66-106">[in] The length of the buffer that the `pcSig` parameter points to.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="d9e66-107">[out] Ukazatel na `ULONG32` velikostí, která přijme ve znacích vyrovnávací paměti musí obsahovat podpis.</span><span class="sxs-lookup"><span data-stu-id="d9e66-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="d9e66-108">[out] Vyrovnávací paměť, která ukládá podpis.</span><span class="sxs-lookup"><span data-stu-id="d9e66-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9e66-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d9e66-109">Return Value</span></span>  
 <span data-ttu-id="d9e66-110">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="d9e66-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9e66-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d9e66-111">Requirements</span></span>  
 <span data-ttu-id="d9e66-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d9e66-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9e66-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="d9e66-113">See Also</span></span>  
 [<span data-ttu-id="d9e66-114">ISymUnmanagedConstant – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d9e66-114">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 [<span data-ttu-id="d9e66-115">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="d9e66-115">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getname-method.md)  
 [<span data-ttu-id="d9e66-116">GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="d9e66-116">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)
