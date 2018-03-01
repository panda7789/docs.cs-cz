---
title: "ISymUnmanagedScope2::GetConstantCount – metoda"
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
- ISymUnmanagedScope2.GetConstantCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2::GetConstantCount
helpviewer_keywords:
- ISymUnmanagedScope2::GetConstantCount method [.NET Framework debugging]
- GetConstantCount method [.NET Framework debugging]
ms.assetid: 1e1f0be6-c4e8-4d6c-98cd-d5fa9f686e87
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 23584f4b29469976f62308f9ff7fe56c0a3875be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedscope2getconstantcount-method"></a><span data-ttu-id="94830-102">ISymUnmanagedScope2::GetConstantCount – metoda</span><span class="sxs-lookup"><span data-stu-id="94830-102">ISymUnmanagedScope2::GetConstantCount Method</span></span>
<span data-ttu-id="94830-103">Získá počet konstanty definované v tomto rozsahu.</span><span class="sxs-lookup"><span data-stu-id="94830-103">Gets a count of the constants defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94830-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94830-104">Syntax</span></span>  
  
```  
HRESULT GetConstantCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="94830-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="94830-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="94830-106">[out] Ukazatel na `ULONG32` velikostí, která přijme ve znacích vyrovnávací paměti musí obsahovat konstanty.</span><span class="sxs-lookup"><span data-stu-id="94830-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="94830-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="94830-107">Return Value</span></span>  
 <span data-ttu-id="94830-108">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="94830-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94830-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="94830-109">Requirements</span></span>  
 <span data-ttu-id="94830-110">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="94830-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94830-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="94830-111">See Also</span></span>  
 [<span data-ttu-id="94830-112">ISymUnmanagedScope2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="94830-112">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
