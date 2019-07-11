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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e89dabeeb4956d106e8d0ca83520d87f3b330e63
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776814"
---
# <a name="isymunmanagedconstantgetvalue-method"></a><span data-ttu-id="32359-102">ISymUnmanagedConstant::GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="32359-102">ISymUnmanagedConstant::GetValue Method</span></span>
<span data-ttu-id="32359-103">Získá hodnotu konstanty.</span><span class="sxs-lookup"><span data-stu-id="32359-103">Gets the value of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32359-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32359-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue(  
    [out]  VARIANT* pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32359-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="32359-105">Parameters</span></span>  
 `pValue`  
 <span data-ttu-id="32359-106">[out] Ukazatel na proměnnou, která přijímá hodnotu.</span><span class="sxs-lookup"><span data-stu-id="32359-106">[out] A pointer to a variable that receives the value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="32359-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="32359-107">Return Value</span></span>  
 <span data-ttu-id="32359-108">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="32359-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32359-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="32359-109">Requirements</span></span>  
 <span data-ttu-id="32359-110">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="32359-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32359-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="32359-111">See also</span></span>

- [<span data-ttu-id="32359-112">ISymUnmanagedConstant – rozhraní</span><span class="sxs-lookup"><span data-stu-id="32359-112">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)
- [<span data-ttu-id="32359-113">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="32359-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="32359-114">GetSignature – metoda</span><span class="sxs-lookup"><span data-stu-id="32359-114">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getsignature-method.md)
