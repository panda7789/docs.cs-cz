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
ms.openlocfilehash: 8956d72d25f240eff653d3eefb92b68431f4e2ae
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771779"
---
# <a name="isymunmanagedmethodgetrootscope-method"></a><span data-ttu-id="fbf98-102">ISymUnmanagedMethod::GetRootScope – metoda</span><span class="sxs-lookup"><span data-stu-id="fbf98-102">ISymUnmanagedMethod::GetRootScope Method</span></span>
<span data-ttu-id="fbf98-103">Získá kořenového oboru lexikální v rámci této metody.</span><span class="sxs-lookup"><span data-stu-id="fbf98-103">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="fbf98-104">Tento rozsah obklopuje celou metodu.</span><span class="sxs-lookup"><span data-stu-id="fbf98-104">This scope encloses the entire method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbf98-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fbf98-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRootScope(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fbf98-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="fbf98-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="fbf98-107">[out] Ukazatel, který je nastaven na vrácenou [isymunmanagedscope –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fbf98-107">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fbf98-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fbf98-108">Return Value</span></span>  
 <span data-ttu-id="fbf98-109">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="fbf98-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbf98-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fbf98-110">Requirements</span></span>  
 <span data-ttu-id="fbf98-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fbf98-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbf98-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fbf98-112">See also</span></span>

- [<span data-ttu-id="fbf98-113">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fbf98-113">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
