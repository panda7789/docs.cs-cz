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
ms.openlocfilehash: 7b3c9c637bdaa0d0e18dbfd9655790ff5ebd46f6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986182"
---
# <a name="isymunmanagedscopegetlocalcount-method"></a><span data-ttu-id="f7016-102">ISymUnmanagedScope::GetLocalCount – metoda</span><span class="sxs-lookup"><span data-stu-id="f7016-102">ISymUnmanagedScope::GetLocalCount Method</span></span>
<span data-ttu-id="f7016-103">Získá počet místních proměnných definovaných v rámci tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="f7016-103">Gets a count of the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7016-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7016-104">Syntax</span></span>  
  
```  
HRESULT GetLocalCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7016-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f7016-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="f7016-106">[out] Ukazatel `ULONG32` , které přijímá počet místních proměnných.</span><span class="sxs-lookup"><span data-stu-id="f7016-106">[out] A pointer to a `ULONG32` that receives the count of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7016-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f7016-107">Return Value</span></span>  
 <span data-ttu-id="f7016-108">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="f7016-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7016-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f7016-109">Requirements</span></span>  
 <span data-ttu-id="f7016-110">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f7016-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7016-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f7016-111">See also</span></span>

- [<span data-ttu-id="f7016-112">ISymUnmanagedScope – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f7016-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
