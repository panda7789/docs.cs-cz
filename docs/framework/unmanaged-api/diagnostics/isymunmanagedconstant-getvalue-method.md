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
ms.openlocfilehash: 75cc16f44ddf29b161c758718b697cc2aaba8e08
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59204663"
---
# <a name="isymunmanagedconstantgetvalue-method"></a><span data-ttu-id="f5451-102">ISymUnmanagedConstant::GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="f5451-102">ISymUnmanagedConstant::GetValue Method</span></span>
<span data-ttu-id="f5451-103">Získá hodnotu konstanty.</span><span class="sxs-lookup"><span data-stu-id="f5451-103">Gets the value of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5451-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5451-104">Syntax</span></span>  
  
```  
HRESULT GetValue(  
    [out]  VARIANT* pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5451-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f5451-105">Parameters</span></span>  
 `pValue`  
 <span data-ttu-id="f5451-106">[out] Ukazatel na proměnnou, která přijímá hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f5451-106">[out] A pointer to a variable that receives the value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f5451-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f5451-107">Return Value</span></span>  
 <span data-ttu-id="f5451-108">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="f5451-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5451-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f5451-109">Requirements</span></span>  
 <span data-ttu-id="f5451-110">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f5451-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5451-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f5451-111">See also</span></span>

- [<span data-ttu-id="f5451-112">ISymUnmanagedConstant – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f5451-112">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)
- [<span data-ttu-id="f5451-113">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="f5451-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="f5451-114">GetSignature – metoda</span><span class="sxs-lookup"><span data-stu-id="f5451-114">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getsignature-method.md)
