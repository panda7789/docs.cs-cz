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
ms.openlocfilehash: 4ac1fc0b3567c49dfb36d2886926bee72d62a8dd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446075"
---
# <a name="isymunmanagedvariablegetendoffset-method"></a><span data-ttu-id="b7cfa-102">ISymUnmanagedVariable::GetEndOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="b7cfa-102">ISymUnmanagedVariable::GetEndOffset Method</span></span>
<span data-ttu-id="b7cfa-103">Získá koncový posun této proměnné v rámci své nadřazené položky.</span><span class="sxs-lookup"><span data-stu-id="b7cfa-103">Gets the end offset of this variable within its parent.</span></span> <span data-ttu-id="b7cfa-104">Pokud se jedná o lokální proměnnou v rámci oboru, koncový posun bude spadat do posunu definovaného pro daný obor.</span><span class="sxs-lookup"><span data-stu-id="b7cfa-104">If this is a local variable within a scope, the end offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7cfa-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7cfa-105">Syntax</span></span>  
  
```cpp  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7cfa-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b7cfa-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="b7cfa-107">mimo Ukazatel na `ULONG32`, který obdrží koncový posun.</span><span class="sxs-lookup"><span data-stu-id="b7cfa-107">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b7cfa-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b7cfa-108">Return Value</span></span>  
 <span data-ttu-id="b7cfa-109">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="b7cfa-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7cfa-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b7cfa-110">Requirements</span></span>  
 <span data-ttu-id="b7cfa-111">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="b7cfa-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7cfa-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b7cfa-112">See also</span></span>

- [<span data-ttu-id="b7cfa-113">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b7cfa-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="b7cfa-114">GetStartOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="b7cfa-114">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)
