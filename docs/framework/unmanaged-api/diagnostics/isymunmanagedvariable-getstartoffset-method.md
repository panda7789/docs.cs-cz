---
title: ISymUnmanagedVariable::GetStartOffset – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetStartOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetStartOffset
helpviewer_keywords:
- GetStartOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetStartOffset method [.NET Framework debugging]
ms.assetid: 63021fc1-9c2d-4788-811f-fe8ca077206a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 996f9af1bccb446ad4fcc6faec60b88e511262de
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474277"
---
# <a name="isymunmanagedvariablegetstartoffset-method"></a><span data-ttu-id="f4fc4-102">ISymUnmanagedVariable::GetStartOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="f4fc4-102">ISymUnmanagedVariable::GetStartOffset Method</span></span>
<span data-ttu-id="f4fc4-103">Získá počáteční odsazení této proměnné v rámci svého nadřazeného objektu.</span><span class="sxs-lookup"><span data-stu-id="f4fc4-103">Gets the start offset of this variable within its parent.</span></span> <span data-ttu-id="f4fc4-104">Pokud je to místní proměnné v rámci oboru, počáteční odsazení bude spadat do posuny definované pro tento obor.</span><span class="sxs-lookup"><span data-stu-id="f4fc4-104">If this is a local variable within a scope, the start offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4fc4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f4fc4-105">Syntax</span></span>  
  
```  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4fc4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f4fc4-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="f4fc4-107">[out] Ukazatel `ULONG32` , která obdrží počáteční odsazení.</span><span class="sxs-lookup"><span data-stu-id="f4fc4-107">[out] A pointer to a `ULONG32` that receives the start offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f4fc4-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f4fc4-108">Return Value</span></span>  
 <span data-ttu-id="f4fc4-109">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="f4fc4-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4fc4-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f4fc4-110">Requirements</span></span>  
 <span data-ttu-id="f4fc4-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f4fc4-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4fc4-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f4fc4-112">See also</span></span>
- [<span data-ttu-id="f4fc4-113">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f4fc4-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="f4fc4-114">GetEndOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="f4fc4-114">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)
