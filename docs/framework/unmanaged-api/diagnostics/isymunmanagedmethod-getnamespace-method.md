---
title: ISymUnmanagedMethod::GetNamespace – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetNamespace
helpviewer_keywords:
- ISymUnmanagedMethod::GetNamespace method [.NET Framework debugging]
- GetNamespace method [.NET Framework debugging]
ms.assetid: 7fbbac42-b966-406d-9ae9-67bf3aea74ce
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 676c968bb48e493f9a4514235fbc3246cf395228
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774646"
---
# <a name="isymunmanagedmethodgetnamespace-method"></a><span data-ttu-id="9b0a7-102">ISymUnmanagedMethod::GetNamespace – metoda</span><span class="sxs-lookup"><span data-stu-id="9b0a7-102">ISymUnmanagedMethod::GetNamespace Method</span></span>
<span data-ttu-id="9b0a7-103">Získá obor názvů, ve kterém je definována této metody.</span><span class="sxs-lookup"><span data-stu-id="9b0a7-103">Gets the namespace within which this method is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b0a7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b0a7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespace(  
   [out] ISymUnmanagedNamespace  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b0a7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9b0a7-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="9b0a7-106">[out] Ukazatel, který je nastaven na vrácenou [isymunmanagednamespace –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9b0a7-106">[out] A pointer that is set to the returned [ISymUnmanagedNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9b0a7-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9b0a7-107">Return Value</span></span>  
 <span data-ttu-id="9b0a7-108">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="9b0a7-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b0a7-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9b0a7-109">Requirements</span></span>  
 <span data-ttu-id="9b0a7-110">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9b0a7-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b0a7-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9b0a7-111">See also</span></span>

- [<span data-ttu-id="9b0a7-112">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9b0a7-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
