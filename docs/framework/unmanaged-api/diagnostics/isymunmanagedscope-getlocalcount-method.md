---
title: ISymUnmanagedScope::GetLocalCount – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetLocalCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetLocalCount
helpviewer_keywords:
- GetLocalCount method [.NET Framework debugging]
- ISymUnmanagedScope::GetLocalCount method [.NET Framework debugging]
ms.assetid: 3ede8fb5-f655-4088-8e19-9c53812588a8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2f8dde609f83a0bbf040ce0e8a4f164259e8584a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427924"
---
# <a name="isymunmanagedscopegetlocalcount-method"></a><span data-ttu-id="cc345-102">ISymUnmanagedScope::GetLocalCount – metoda</span><span class="sxs-lookup"><span data-stu-id="cc345-102">ISymUnmanagedScope::GetLocalCount Method</span></span>
<span data-ttu-id="cc345-103">Získá počet místní proměnné definované v tomto rozsahu.</span><span class="sxs-lookup"><span data-stu-id="cc345-103">Gets a count of the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc345-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc345-104">Syntax</span></span>  
  
```  
HRESULT GetLocalCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cc345-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cc345-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="cc345-106">[out] Ukazatel na `ULONG32` která přijme počet lokální proměnné.</span><span class="sxs-lookup"><span data-stu-id="cc345-106">[out] A pointer to a `ULONG32` that receives the count of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cc345-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="cc345-107">Return Value</span></span>  
 <span data-ttu-id="cc345-108">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="cc345-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc345-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cc345-109">Requirements</span></span>  
 <span data-ttu-id="cc345-110">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="cc345-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc345-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="cc345-111">See Also</span></span>  
 [<span data-ttu-id="cc345-112">ISymUnmanagedScope – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cc345-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
