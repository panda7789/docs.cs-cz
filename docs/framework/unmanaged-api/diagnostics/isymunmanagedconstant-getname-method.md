---
title: ISymUnmanagedConstant::GetName – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetName
helpviewer_keywords:
- ISymUnmanagedConstant::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedConstant interface [.NET Framework debugging]
ms.assetid: cbaca4e1-4473-459b-ba34-f1f59ce7c0ba
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3ae532b20ec3486fe56e2dff340a5ad89941a8df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424372"
---
# <a name="isymunmanagedconstantgetname-method"></a><span data-ttu-id="33c2e-102">ISymUnmanagedConstant::GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="33c2e-102">ISymUnmanagedConstant::GetName Method</span></span>
<span data-ttu-id="33c2e-103">Získá název konstanty.</span><span class="sxs-lookup"><span data-stu-id="33c2e-103">Gets the name of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33c2e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="33c2e-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="33c2e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="33c2e-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="33c2e-106">[v] Délka vyrovnávací paměti, která `szName` parametr odkazuje na.</span><span class="sxs-lookup"><span data-stu-id="33c2e-106">[in] The length of the buffer that the `szName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="33c2e-107">[out] Ukazatel na `ULONG32` velikostí, která přijme ve znacích vyrovnávací paměti musí obsahovat název, včetně ukončení hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="33c2e-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="33c2e-108">[out] Vyrovnávací paměť, která ukládá název.</span><span class="sxs-lookup"><span data-stu-id="33c2e-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="33c2e-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="33c2e-109">Return Value</span></span>  
 <span data-ttu-id="33c2e-110">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="33c2e-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33c2e-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="33c2e-111">Requirements</span></span>  
 <span data-ttu-id="33c2e-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="33c2e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33c2e-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="33c2e-113">See Also</span></span>  
 [<span data-ttu-id="33c2e-114">ISymUnmanagedConstant – rozhraní</span><span class="sxs-lookup"><span data-stu-id="33c2e-114">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 [<span data-ttu-id="33c2e-115">GetSignature – metoda</span><span class="sxs-lookup"><span data-stu-id="33c2e-115">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getsignature-method.md)  
 [<span data-ttu-id="33c2e-116">GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="33c2e-116">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)
