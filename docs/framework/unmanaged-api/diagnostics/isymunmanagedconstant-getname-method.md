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
ms.openlocfilehash: 924feaeb91b42404461ad5d276c0cb77279d4dc4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449276"
---
# <a name="isymunmanagedconstantgetname-method"></a><span data-ttu-id="da06f-102">ISymUnmanagedConstant::GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="da06f-102">ISymUnmanagedConstant::GetName Method</span></span>
<span data-ttu-id="da06f-103">Gets the name of the constant.</span><span class="sxs-lookup"><span data-stu-id="da06f-103">Gets the name of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da06f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da06f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da06f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="da06f-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="da06f-106">[in] The length of the buffer that the `szName` parameter points to.</span><span class="sxs-lookup"><span data-stu-id="da06f-106">[in] The length of the buffer that the `szName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="da06f-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span><span class="sxs-lookup"><span data-stu-id="da06f-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="da06f-108">[out] The buffer that stores the name.</span><span class="sxs-lookup"><span data-stu-id="da06f-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="da06f-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="da06f-109">Return Value</span></span>  
 <span data-ttu-id="da06f-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="da06f-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da06f-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="da06f-111">Requirements</span></span>  
 <span data-ttu-id="da06f-112">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="da06f-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da06f-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="da06f-113">See also</span></span>

- [<span data-ttu-id="da06f-114">ISymUnmanagedConstant – rozhraní</span><span class="sxs-lookup"><span data-stu-id="da06f-114">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)
- [<span data-ttu-id="da06f-115">GetSignature – metoda</span><span class="sxs-lookup"><span data-stu-id="da06f-115">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getsignature-method.md)
- [<span data-ttu-id="da06f-116">GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="da06f-116">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)
