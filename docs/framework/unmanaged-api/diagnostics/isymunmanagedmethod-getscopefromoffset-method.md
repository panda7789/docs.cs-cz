---
title: ISymUnmanagedMethod::GetScopeFromOffset – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetScopeFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetScopeFromOffset
helpviewer_keywords:
- GetScopeFromOffset method [.NET Framework debugging]
- ISymUnmanagedMethod::GetScopeFromOffset method [.NET Framework debugging]
ms.assetid: d14cf210-81f8-46e1-8b19-6ddec0ba8b11
topic_type:
- apiref
ms.openlocfilehash: 4eefd019280f501a6ce194e5ce84388e32cc66e1
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615134"
---
# <a name="isymunmanagedmethodgetscopefromoffset-method"></a><span data-ttu-id="a95d6-102">ISymUnmanagedMethod::GetScopeFromOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="a95d6-102">ISymUnmanagedMethod::GetScopeFromOffset Method</span></span>
<span data-ttu-id="a95d6-103">Získá nejvíce ohraničující lexikální obor v rámci této metody, která uzavře daný posun.</span><span class="sxs-lookup"><span data-stu-id="a95d6-103">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span> <span data-ttu-id="a95d6-104">Tato možnost slouží ke spuštění hledání místních proměnných.</span><span class="sxs-lookup"><span data-stu-id="a95d6-104">This can be used to start local variable searches.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a95d6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a95d6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetScopeFromOffset(  
    [in]  ULONG32 offset,  
    [out, retval] ISymUnmanagedScope**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a95d6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a95d6-106">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="a95d6-107">pro `ULONG`, Který obsahuje posun.</span><span class="sxs-lookup"><span data-stu-id="a95d6-107">[in] A `ULONG` that contains the offset.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="a95d6-108">mimo Ukazatel, který je nastaven na vrácené rozhraní [ISymUnmanagedScope](isymunmanagedscope-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="a95d6-108">[out] A pointer that is set to the returned [ISymUnmanagedScope](isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a95d6-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a95d6-109">Return Value</span></span>  
 <span data-ttu-id="a95d6-110">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="a95d6-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a95d6-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a95d6-111">Requirements</span></span>  
 <span data-ttu-id="a95d6-112">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="a95d6-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a95d6-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="a95d6-113">See also</span></span>

- [<span data-ttu-id="a95d6-114">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a95d6-114">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
