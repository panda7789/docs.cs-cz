---
title: ISymUnmanagedScope::GetStartOffset – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetStartOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetStartOffset
helpviewer_keywords:
- GetStartOffset method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetStartOffset method [.NET Framework debugging]
ms.assetid: da6bbc75-94d1-4354-9722-0d455b4428fb
topic_type:
- apiref
ms.openlocfilehash: 071ad6c24804eecb0f2260d54c854f22ff997bc1
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83611013"
---
# <a name="isymunmanagedscopegetstartoffset-method"></a><span data-ttu-id="0efda-102">ISymUnmanagedScope::GetStartOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="0efda-102">ISymUnmanagedScope::GetStartOffset Method</span></span>
<span data-ttu-id="0efda-103">Získá posun začátku tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="0efda-103">Gets the start offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0efda-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0efda-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0efda-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0efda-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="0efda-106">mimo Ukazatel na `ULONG32` , který obsahuje počáteční posun.</span><span class="sxs-lookup"><span data-stu-id="0efda-106">[out] A pointer to a `ULONG32` that contains the starting offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0efda-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0efda-107">Return Value</span></span>  
 <span data-ttu-id="0efda-108">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="0efda-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0efda-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0efda-109">Requirements</span></span>  
 <span data-ttu-id="0efda-110">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="0efda-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0efda-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="0efda-111">See also</span></span>

- [<span data-ttu-id="0efda-112">ISymUnmanagedScope – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0efda-112">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
- [<span data-ttu-id="0efda-113">GetEndOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="0efda-113">GetEndOffset Method</span></span>](isymunmanagedscope-getendoffset-method.md)
