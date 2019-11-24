---
title: ISymUnmanagedConstant::GetValue – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetValue
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetValue
helpviewer_keywords:
- GetValue method, ISymUnmanagedConstant interface [.NET Framework debugging]
- ISymUnmanagedConstant::GetValue method [.NET Framework debugging]
ms.assetid: 0036fc10-e768-47a8-b9cf-bf47faf8d194
topic_type:
- apiref
ms.openlocfilehash: 00be35e9a15349b8bca5f76b948b8477dd240888
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449237"
---
# <a name="isymunmanagedconstantgetvalue-method"></a><span data-ttu-id="af02e-102">ISymUnmanagedConstant::GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="af02e-102">ISymUnmanagedConstant::GetValue Method</span></span>
<span data-ttu-id="af02e-103">Gets the value of the constant.</span><span class="sxs-lookup"><span data-stu-id="af02e-103">Gets the value of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af02e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af02e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue(  
    [out]  VARIANT* pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af02e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="af02e-105">Parameters</span></span>  
 `pValue`  
 <span data-ttu-id="af02e-106">[out] A pointer to a variable that receives the value.</span><span class="sxs-lookup"><span data-stu-id="af02e-106">[out] A pointer to a variable that receives the value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="af02e-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="af02e-107">Return Value</span></span>  
 <span data-ttu-id="af02e-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="af02e-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af02e-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="af02e-109">Requirements</span></span>  
 <span data-ttu-id="af02e-110">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="af02e-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af02e-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="af02e-111">See also</span></span>

- [<span data-ttu-id="af02e-112">ISymUnmanagedConstant – rozhraní</span><span class="sxs-lookup"><span data-stu-id="af02e-112">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)
- [<span data-ttu-id="af02e-113">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="af02e-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="af02e-114">GetSignature – metoda</span><span class="sxs-lookup"><span data-stu-id="af02e-114">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getsignature-method.md)
