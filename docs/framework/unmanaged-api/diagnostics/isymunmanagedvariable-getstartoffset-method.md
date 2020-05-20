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
ms.openlocfilehash: f2996349fd2bf1765a3de5b67d3296a25b1eaa5e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610363"
---
# <a name="isymunmanagedvariablegetstartoffset-method"></a><span data-ttu-id="bc5f2-102">ISymUnmanagedVariable::GetStartOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="bc5f2-102">ISymUnmanagedVariable::GetStartOffset Method</span></span>
<span data-ttu-id="bc5f2-103">Získá počáteční posun této proměnné v rámci své nadřazené položky.</span><span class="sxs-lookup"><span data-stu-id="bc5f2-103">Gets the start offset of this variable within its parent.</span></span> <span data-ttu-id="bc5f2-104">Pokud se jedná o lokální proměnnou v rámci oboru, počáteční posun bude spadat do posunů definovaných pro daný obor.</span><span class="sxs-lookup"><span data-stu-id="bc5f2-104">If this is a local variable within a scope, the start offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc5f2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bc5f2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc5f2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="bc5f2-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="bc5f2-107">mimo Ukazatel na `ULONG32` , který obdrží počáteční posun.</span><span class="sxs-lookup"><span data-stu-id="bc5f2-107">[out] A pointer to a `ULONG32` that receives the start offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bc5f2-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bc5f2-108">Return Value</span></span>  
 <span data-ttu-id="bc5f2-109">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="bc5f2-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc5f2-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bc5f2-110">Requirements</span></span>  
 <span data-ttu-id="bc5f2-111">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="bc5f2-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc5f2-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="bc5f2-112">See also</span></span>

- [<span data-ttu-id="bc5f2-113">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bc5f2-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="bc5f2-114">GetEndOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="bc5f2-114">GetEndOffset Method</span></span>](isymunmanagedvariable-getendoffset-method.md)
