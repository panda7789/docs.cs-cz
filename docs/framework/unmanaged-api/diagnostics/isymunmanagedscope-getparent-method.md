---
title: "ISymUnmanagedScope::GetParent – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1defb0f95ed38d8dbe5d47d804e340b3ca35a79c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedscopegetparent-method"></a><span data-ttu-id="84b18-102">ISymUnmanagedScope::GetParent – metoda</span><span class="sxs-lookup"><span data-stu-id="84b18-102">ISymUnmanagedScope::GetParent Method</span></span>
<span data-ttu-id="84b18-103">Získá nadřazený obor tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="84b18-103">Gets the parent scope of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84b18-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84b18-104">Syntax</span></span>  
  
```  
HRESULT GetParent(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="84b18-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="84b18-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="84b18-106">[out] Ukazatel na vrácený [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="84b18-106">[out] A pointer to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="84b18-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="84b18-107">Return Value</span></span>  
 <span data-ttu-id="84b18-108">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="84b18-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84b18-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="84b18-109">Requirements</span></span>  
 <span data-ttu-id="84b18-110">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="84b18-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84b18-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="84b18-111">See Also</span></span>  
 [<span data-ttu-id="84b18-112">ISymUnmanagedScope – rozhraní</span><span class="sxs-lookup"><span data-stu-id="84b18-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 [<span data-ttu-id="84b18-113">GetChildren – metoda</span><span class="sxs-lookup"><span data-stu-id="84b18-113">GetChildren Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getchildren-method.md)
