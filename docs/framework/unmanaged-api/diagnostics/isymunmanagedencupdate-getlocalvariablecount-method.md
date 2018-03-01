---
title: "ISymUnmanagedENCUpdate::GetLocalVariableCount – metoda"
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
- ISymUnmanagedENCUpdate.GetLocalVariableCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount method [.NET Framework debugging]
- GetLocalVariableCount method [.NET Framework debugging]
ms.assetid: 9777d8bb-4abc-4be8-aa7c-34f853eceb9c
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7c86b2988d414d091bc23d29bd79f518a756d688
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedencupdategetlocalvariablecount-method"></a><span data-ttu-id="7ee15-102">ISymUnmanagedENCUpdate::GetLocalVariableCount – metoda</span><span class="sxs-lookup"><span data-stu-id="7ee15-102">ISymUnmanagedENCUpdate::GetLocalVariableCount Method</span></span>
<span data-ttu-id="7ee15-103">Získá počet lokální proměnné.</span><span class="sxs-lookup"><span data-stu-id="7ee15-103">Gets the number of local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ee15-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7ee15-104">Syntax</span></span>  
  
```  
HRESULT GetLocalVariableCount(  
    [in]  mdMethodDef  mdMethodToken,  
    [out] ULONG        *pcLocals);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7ee15-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7ee15-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="7ee15-106">[v] Metadata token metod.</span><span class="sxs-lookup"><span data-stu-id="7ee15-106">[in] The metadata token of methods.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="7ee15-107">[out] Ukazatel na `ULONG32` velikostí, která přijme ve znacích vyrovnávací paměti musí obsahovat číslo lokální proměnné.</span><span class="sxs-lookup"><span data-stu-id="7ee15-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the number of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7ee15-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7ee15-108">Return Value</span></span>  
 <span data-ttu-id="7ee15-109">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="7ee15-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ee15-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7ee15-110">Requirements</span></span>  
 <span data-ttu-id="7ee15-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7ee15-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ee15-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="7ee15-112">See Also</span></span>  
 [<span data-ttu-id="7ee15-113">ISymUnmanagedENCUpdate – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7ee15-113">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
