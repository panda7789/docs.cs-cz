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
ms.openlocfilehash: a2bba44af50607772f2a52203a47e21d8699f78b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716149"
---
# <a name="isymunmanagedmethodgetnamespace-method"></a><span data-ttu-id="08740-102">ISymUnmanagedMethod::GetNamespace – metoda</span><span class="sxs-lookup"><span data-stu-id="08740-102">ISymUnmanagedMethod::GetNamespace Method</span></span>
<span data-ttu-id="08740-103">Získá obor názvů, ve kterém je definována této metody.</span><span class="sxs-lookup"><span data-stu-id="08740-103">Gets the namespace within which this method is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08740-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08740-104">Syntax</span></span>  
  
```  
HRESULT GetNamespace(  
   [out] ISymUnmanagedNamespace  **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="08740-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="08740-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="08740-106">[out] Ukazatel, který je nastaven na vrácenou [isymunmanagednamespace –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="08740-106">[out] A pointer that is set to the returned [ISymUnmanagedNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="08740-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="08740-107">Return Value</span></span>  
 <span data-ttu-id="08740-108">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="08740-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08740-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="08740-109">Requirements</span></span>  
 <span data-ttu-id="08740-110">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="08740-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08740-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="08740-111">See also</span></span>
- [<span data-ttu-id="08740-112">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="08740-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
