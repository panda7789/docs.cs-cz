---
title: ISymUnmanagedVariable::GetEndOffset – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a4c474b2ea9bc80be156c8e1424eabe3d2384666
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585263"
---
# <a name="isymunmanagedvariablegetendoffset-method"></a><span data-ttu-id="674cf-102">ISymUnmanagedVariable::GetEndOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="674cf-102">ISymUnmanagedVariable::GetEndOffset Method</span></span>
<span data-ttu-id="674cf-103">Získá posun ukončení této proměnné v rámci svého nadřazeného objektu.</span><span class="sxs-lookup"><span data-stu-id="674cf-103">Gets the end offset of this variable within its parent.</span></span> <span data-ttu-id="674cf-104">Pokud je to místní proměnné v rámci oboru, koncové odsazení bude spadat do posuny definované pro tento obor.</span><span class="sxs-lookup"><span data-stu-id="674cf-104">If this is a local variable within a scope, the end offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="674cf-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="674cf-105">Syntax</span></span>  
  
```  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="674cf-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="674cf-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="674cf-107">[out] Ukazatel `ULONG32` , která obdrží koncové odsazení.</span><span class="sxs-lookup"><span data-stu-id="674cf-107">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="674cf-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="674cf-108">Return Value</span></span>  
 <span data-ttu-id="674cf-109">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="674cf-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="674cf-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="674cf-110">Requirements</span></span>  
 <span data-ttu-id="674cf-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="674cf-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="674cf-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="674cf-112">See also</span></span>
- [<span data-ttu-id="674cf-113">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="674cf-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="674cf-114">GetStartOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="674cf-114">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)
