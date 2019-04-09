---
title: ISymUnmanagedScope::GetParent – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetParent
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetParent
helpviewer_keywords:
- GetParent method [.NET Framework debugging]
- ISymUnmanagedScope::GetParent method [.NET Framework debugging]
ms.assetid: c7963c87-6ec5-49b3-a5cd-e0fe0c43f9b4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d90aeb22a945f4fa1576009c700c420704dd891b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59144778"
---
# <a name="isymunmanagedscopegetparent-method"></a><span data-ttu-id="800e3-102">ISymUnmanagedScope::GetParent – metoda</span><span class="sxs-lookup"><span data-stu-id="800e3-102">ISymUnmanagedScope::GetParent Method</span></span>
<span data-ttu-id="800e3-103">Získá nadřazený obor tohoto rozsahu.</span><span class="sxs-lookup"><span data-stu-id="800e3-103">Gets the parent scope of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="800e3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="800e3-104">Syntax</span></span>  
  
```  
HRESULT GetParent(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="800e3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="800e3-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="800e3-106">[out] Ukazatel na vrácenou [isymunmanagedscope –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="800e3-106">[out] A pointer to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="800e3-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="800e3-107">Return Value</span></span>  
 <span data-ttu-id="800e3-108">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="800e3-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="800e3-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="800e3-109">Requirements</span></span>  
 <span data-ttu-id="800e3-110">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="800e3-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="800e3-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="800e3-111">See also</span></span>

- [<span data-ttu-id="800e3-112">ISymUnmanagedScope – rozhraní</span><span class="sxs-lookup"><span data-stu-id="800e3-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
- [<span data-ttu-id="800e3-113">GetChildren – metoda</span><span class="sxs-lookup"><span data-stu-id="800e3-113">GetChildren Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getchildren-method.md)
