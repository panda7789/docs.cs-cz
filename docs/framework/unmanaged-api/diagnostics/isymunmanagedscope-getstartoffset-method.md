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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2b81ac93c67d59c294f22eb825527fa9982d9124
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54721094"
---
# <a name="isymunmanagedscopegetstartoffset-method"></a><span data-ttu-id="ad814-102">ISymUnmanagedScope::GetStartOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="ad814-102">ISymUnmanagedScope::GetStartOffset Method</span></span>
<span data-ttu-id="ad814-103">Získá počáteční odsazení pro tento obor.</span><span class="sxs-lookup"><span data-stu-id="ad814-103">Gets the start offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad814-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad814-104">Syntax</span></span>  
  
```  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ad814-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ad814-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="ad814-106">[out] Ukazatel `ULONG32` , která obsahuje počáteční posun.</span><span class="sxs-lookup"><span data-stu-id="ad814-106">[out] A pointer to a `ULONG32` that contains the starting offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ad814-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ad814-107">Return Value</span></span>  
 <span data-ttu-id="ad814-108">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="ad814-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad814-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ad814-109">Requirements</span></span>  
 <span data-ttu-id="ad814-110">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ad814-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad814-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ad814-111">See also</span></span>
- [<span data-ttu-id="ad814-112">ISymUnmanagedScope – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ad814-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
- [<span data-ttu-id="ad814-113">GetEndOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="ad814-113">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)
