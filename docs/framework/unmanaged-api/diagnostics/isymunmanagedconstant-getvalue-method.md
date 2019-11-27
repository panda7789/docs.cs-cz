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
# <a name="isymunmanagedconstantgetvalue-method"></a><span data-ttu-id="e770c-102">ISymUnmanagedConstant::GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="e770c-102">ISymUnmanagedConstant::GetValue Method</span></span>
<span data-ttu-id="e770c-103">Získá hodnotu konstanty.</span><span class="sxs-lookup"><span data-stu-id="e770c-103">Gets the value of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e770c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e770c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue(  
    [out]  VARIANT* pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e770c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e770c-105">Parameters</span></span>  
 `pValue`  
 <span data-ttu-id="e770c-106">mimo Ukazatel na proměnnou, která přijímá hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e770c-106">[out] A pointer to a variable that receives the value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e770c-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e770c-107">Return Value</span></span>  
 <span data-ttu-id="e770c-108">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="e770c-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e770c-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e770c-109">Requirements</span></span>  
 <span data-ttu-id="e770c-110">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="e770c-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e770c-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e770c-111">See also</span></span>

- [<span data-ttu-id="e770c-112">ISymUnmanagedConstant – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e770c-112">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)
- [<span data-ttu-id="e770c-113">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="e770c-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="e770c-114">GetSignature – metoda</span><span class="sxs-lookup"><span data-stu-id="e770c-114">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getsignature-method.md)
