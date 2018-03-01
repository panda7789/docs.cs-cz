---
title: "ISymUnmanagedVariable::GetEndOffset – metoda"
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
- ISymUnmanagedVariable.GetEndOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedVariable::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: e5d777c5-d450-4c0f-999c-b3953ee22cfb
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f91c2b0f4ecb4cc901a0389d15f4d69e926cf8f6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedvariablegetendoffset-method"></a><span data-ttu-id="4aaf3-102">ISymUnmanagedVariable::GetEndOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="4aaf3-102">ISymUnmanagedVariable::GetEndOffset Method</span></span>
<span data-ttu-id="4aaf3-103">Získá posun end této proměnné v rámci jeho nadřazený objekt.</span><span class="sxs-lookup"><span data-stu-id="4aaf3-103">Gets the end offset of this variable within its parent.</span></span> <span data-ttu-id="4aaf3-104">Pokud je to místní proměnné v oboru, posun end bude spadat do posuny definované pro obor.</span><span class="sxs-lookup"><span data-stu-id="4aaf3-104">If this is a local variable within a scope, the end offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4aaf3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4aaf3-105">Syntax</span></span>  
  
```  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4aaf3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4aaf3-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="4aaf3-107">[out] Ukazatel na `ULONG32` která přijme posun end.</span><span class="sxs-lookup"><span data-stu-id="4aaf3-107">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4aaf3-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4aaf3-108">Return Value</span></span>  
 <span data-ttu-id="4aaf3-109">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="4aaf3-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4aaf3-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4aaf3-110">Requirements</span></span>  
 <span data-ttu-id="4aaf3-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4aaf3-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4aaf3-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="4aaf3-112">See Also</span></span>  
 [<span data-ttu-id="4aaf3-113">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4aaf3-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="4aaf3-114">GetStartOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="4aaf3-114">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)
