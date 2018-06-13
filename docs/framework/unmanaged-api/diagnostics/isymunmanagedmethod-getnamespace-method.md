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
ms.openlocfilehash: 53a47cf67edb36b06c92be83cb23c2e1dd1e75cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424427"
---
# <a name="isymunmanagedmethodgetnamespace-method"></a><span data-ttu-id="de26f-102">ISymUnmanagedMethod::GetNamespace – metoda</span><span class="sxs-lookup"><span data-stu-id="de26f-102">ISymUnmanagedMethod::GetNamespace Method</span></span>
<span data-ttu-id="de26f-103">Získá obor názvů, ve kterém je tato metoda definována.</span><span class="sxs-lookup"><span data-stu-id="de26f-103">Gets the namespace within which this method is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de26f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de26f-104">Syntax</span></span>  
  
```  
HRESULT GetNamespace(  
   [out] ISymUnmanagedNamespace  **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="de26f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="de26f-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="de26f-106">[out] Ukazatele, který je nastavený s vráceným [ISymUnmanagedNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="de26f-106">[out] A pointer that is set to the returned [ISymUnmanagedNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="de26f-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="de26f-107">Return Value</span></span>  
 <span data-ttu-id="de26f-108">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="de26f-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de26f-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="de26f-109">Requirements</span></span>  
 <span data-ttu-id="de26f-110">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="de26f-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de26f-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="de26f-111">See Also</span></span>  
 [<span data-ttu-id="de26f-112">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="de26f-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
