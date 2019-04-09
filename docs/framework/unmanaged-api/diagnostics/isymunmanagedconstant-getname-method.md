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
ms.openlocfilehash: 1da8d89cf9ae2eed7b846774434d6ea472afbb94
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59194393"
---
# <a name="isymunmanagedconstantgetname-method"></a><span data-ttu-id="09b4e-102">ISymUnmanagedConstant::GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="09b4e-102">ISymUnmanagedConstant::GetName Method</span></span>
<span data-ttu-id="09b4e-103">Získá název konstanty.</span><span class="sxs-lookup"><span data-stu-id="09b4e-103">Gets the name of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09b4e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09b4e-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09b4e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="09b4e-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="09b4e-106">[in] Délka vyrovnávací paměti, která `szName` parametr odkazuje na.</span><span class="sxs-lookup"><span data-stu-id="09b4e-106">[in] The length of the buffer that the `szName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="09b4e-107">[out] Ukazatel `ULONG32` , která obdrží velikost ve znacích, vyrovnávací paměti musí obsahovat název, včetně ukončení hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="09b4e-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="09b4e-108">[out] Vyrovnávací paměť, která ukládá název.</span><span class="sxs-lookup"><span data-stu-id="09b4e-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="09b4e-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="09b4e-109">Return Value</span></span>  
 <span data-ttu-id="09b4e-110">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="09b4e-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09b4e-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="09b4e-111">Requirements</span></span>  
 <span data-ttu-id="09b4e-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="09b4e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09b4e-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="09b4e-113">See also</span></span>

- [<span data-ttu-id="09b4e-114">ISymUnmanagedConstant – rozhraní</span><span class="sxs-lookup"><span data-stu-id="09b4e-114">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)
- [<span data-ttu-id="09b4e-115">GetSignature – metoda</span><span class="sxs-lookup"><span data-stu-id="09b4e-115">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getsignature-method.md)
- [<span data-ttu-id="09b4e-116">GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="09b4e-116">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)
