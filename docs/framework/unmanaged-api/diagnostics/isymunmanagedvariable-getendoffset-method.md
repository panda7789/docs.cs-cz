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
ms.openlocfilehash: 325db05cc322d85e836ca9ba62b6a169e8965241
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59220952"
---
# <a name="isymunmanagedvariablegetendoffset-method"></a><span data-ttu-id="acad8-102">ISymUnmanagedVariable::GetEndOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="acad8-102">ISymUnmanagedVariable::GetEndOffset Method</span></span>
<span data-ttu-id="acad8-103">Získá posun ukončení této proměnné v rámci svého nadřazeného objektu.</span><span class="sxs-lookup"><span data-stu-id="acad8-103">Gets the end offset of this variable within its parent.</span></span> <span data-ttu-id="acad8-104">Pokud je to místní proměnné v rámci oboru, koncové odsazení bude spadat do posuny definované pro tento obor.</span><span class="sxs-lookup"><span data-stu-id="acad8-104">If this is a local variable within a scope, the end offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acad8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="acad8-105">Syntax</span></span>  
  
```  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="acad8-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="acad8-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="acad8-107">[out] Ukazatel `ULONG32` , která obdrží koncové odsazení.</span><span class="sxs-lookup"><span data-stu-id="acad8-107">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="acad8-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="acad8-108">Return Value</span></span>  
 <span data-ttu-id="acad8-109">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="acad8-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="acad8-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="acad8-110">Requirements</span></span>  
 <span data-ttu-id="acad8-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="acad8-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acad8-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="acad8-112">See also</span></span>

- [<span data-ttu-id="acad8-113">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="acad8-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="acad8-114">GetStartOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="acad8-114">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)
