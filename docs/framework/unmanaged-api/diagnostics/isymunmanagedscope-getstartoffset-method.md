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
ms.openlocfilehash: faab55199a3b921ea8b995e2a0f9823fb4da9cc7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761611"
---
# <a name="isymunmanagedscopegetstartoffset-method"></a><span data-ttu-id="ac5bf-102">ISymUnmanagedScope::GetStartOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="ac5bf-102">ISymUnmanagedScope::GetStartOffset Method</span></span>
<span data-ttu-id="ac5bf-103">Získá počáteční odsazení pro tento obor.</span><span class="sxs-lookup"><span data-stu-id="ac5bf-103">Gets the start offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac5bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac5bf-104">Syntax</span></span>  
  
```  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac5bf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ac5bf-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="ac5bf-106">[out] Ukazatel `ULONG32` , která obsahuje počáteční posun.</span><span class="sxs-lookup"><span data-stu-id="ac5bf-106">[out] A pointer to a `ULONG32` that contains the starting offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ac5bf-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ac5bf-107">Return Value</span></span>  
 <span data-ttu-id="ac5bf-108">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="ac5bf-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac5bf-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ac5bf-109">Requirements</span></span>  
 <span data-ttu-id="ac5bf-110">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ac5bf-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac5bf-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ac5bf-111">See also</span></span>

- [<span data-ttu-id="ac5bf-112">ISymUnmanagedScope – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ac5bf-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
- [<span data-ttu-id="ac5bf-113">GetEndOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="ac5bf-113">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)
