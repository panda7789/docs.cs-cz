---
title: ISymUnmanagedMethod::GetRootScope – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetRootScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetRootScope
helpviewer_keywords:
- ISymUnmanagedMethod::GetRootScope method [.NET Framework debugging]
- GetRootScope method [.NET Framework debugging]
ms.assetid: 7d58caac-2e75-4dfa-9249-32d8a624b247
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b55b379f0b2e47acbec03eebf92e1e107a52f918
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57502941"
---
# <a name="isymunmanagedmethodgetrootscope-method"></a><span data-ttu-id="18daf-102">ISymUnmanagedMethod::GetRootScope – metoda</span><span class="sxs-lookup"><span data-stu-id="18daf-102">ISymUnmanagedMethod::GetRootScope Method</span></span>
<span data-ttu-id="18daf-103">Získá kořenového oboru lexikální v rámci této metody.</span><span class="sxs-lookup"><span data-stu-id="18daf-103">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="18daf-104">Tento rozsah obklopuje celou metodu.</span><span class="sxs-lookup"><span data-stu-id="18daf-104">This scope encloses the entire method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18daf-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18daf-105">Syntax</span></span>  
  
```  
HRESULT GetRootScope(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18daf-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="18daf-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="18daf-107">[out] Ukazatel, který je nastaven na vrácenou [isymunmanagedscope –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="18daf-107">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="18daf-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="18daf-108">Return Value</span></span>  
 <span data-ttu-id="18daf-109">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="18daf-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18daf-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="18daf-110">Requirements</span></span>  
 <span data-ttu-id="18daf-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="18daf-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18daf-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="18daf-112">See also</span></span>
- [<span data-ttu-id="18daf-113">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="18daf-113">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
