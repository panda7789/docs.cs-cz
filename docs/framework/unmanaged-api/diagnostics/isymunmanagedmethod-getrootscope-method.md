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
ms.openlocfilehash: 7c77be0dde950693d3943e41c392dcdcd9bc995e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59096072"
---
# <a name="isymunmanagedmethodgetrootscope-method"></a><span data-ttu-id="348ee-102">ISymUnmanagedMethod::GetRootScope – metoda</span><span class="sxs-lookup"><span data-stu-id="348ee-102">ISymUnmanagedMethod::GetRootScope Method</span></span>
<span data-ttu-id="348ee-103">Získá kořenového oboru lexikální v rámci této metody.</span><span class="sxs-lookup"><span data-stu-id="348ee-103">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="348ee-104">Tento rozsah obklopuje celou metodu.</span><span class="sxs-lookup"><span data-stu-id="348ee-104">This scope encloses the entire method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="348ee-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="348ee-105">Syntax</span></span>  
  
```  
HRESULT GetRootScope(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="348ee-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="348ee-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="348ee-107">[out] Ukazatel, který je nastaven na vrácenou [isymunmanagedscope –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="348ee-107">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="348ee-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="348ee-108">Return Value</span></span>  
 <span data-ttu-id="348ee-109">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="348ee-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="348ee-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="348ee-110">Requirements</span></span>  
 <span data-ttu-id="348ee-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="348ee-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="348ee-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="348ee-112">See also</span></span>

- [<span data-ttu-id="348ee-113">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="348ee-113">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
