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
ms.openlocfilehash: 3dbe5b4e57f21970b518e4974707175f4bdcf02a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778230"
---
# <a name="isymunmanagedvariablegetstartoffset-method"></a><span data-ttu-id="2ee4c-102">ISymUnmanagedVariable::GetStartOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="2ee4c-102">ISymUnmanagedVariable::GetStartOffset Method</span></span>
<span data-ttu-id="2ee4c-103">Získá počáteční odsazení této proměnné v rámci svého nadřazeného objektu.</span><span class="sxs-lookup"><span data-stu-id="2ee4c-103">Gets the start offset of this variable within its parent.</span></span> <span data-ttu-id="2ee4c-104">Pokud je to místní proměnné v rámci oboru, počáteční odsazení bude spadat do posuny definované pro tento obor.</span><span class="sxs-lookup"><span data-stu-id="2ee4c-104">If this is a local variable within a scope, the start offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ee4c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ee4c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ee4c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2ee4c-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="2ee4c-107">[out] Ukazatel `ULONG32` , která obdrží počáteční odsazení.</span><span class="sxs-lookup"><span data-stu-id="2ee4c-107">[out] A pointer to a `ULONG32` that receives the start offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2ee4c-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2ee4c-108">Return Value</span></span>  
 <span data-ttu-id="2ee4c-109">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="2ee4c-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ee4c-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2ee4c-110">Requirements</span></span>  
 <span data-ttu-id="2ee4c-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2ee4c-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ee4c-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2ee4c-112">See also</span></span>

- [<span data-ttu-id="2ee4c-113">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2ee4c-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="2ee4c-114">GetEndOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="2ee4c-114">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)
