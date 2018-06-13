---
title: ISymUnmanagedScope::GetMethod – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetMethod
helpviewer_keywords:
- GetMethod method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetMethod method [.NET Framework debugging]
ms.assetid: a61866ee-221a-45b9-a1b7-395825b77872
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ebef54baf4e560b364845a521e4b4444ed359395
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426117"
---
# <a name="isymunmanagedscopegetmethod-method"></a><span data-ttu-id="f8c83-102">ISymUnmanagedScope::GetMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="f8c83-102">ISymUnmanagedScope::GetMethod Method</span></span>
<span data-ttu-id="f8c83-103">Získá metody, která obsahuje tento obor.</span><span class="sxs-lookup"><span data-stu-id="f8c83-103">Gets the method that contains this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8c83-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8c83-104">Syntax</span></span>  
  
```  
HRESULT GetMethod(  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f8c83-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f8c83-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="f8c83-106">[out] Ukazatel na vrácený [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f8c83-106">[out] A pointer to the returned [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f8c83-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f8c83-107">Return Value</span></span>  
 <span data-ttu-id="f8c83-108">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="f8c83-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8c83-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f8c83-109">Requirements</span></span>  
 <span data-ttu-id="f8c83-110">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f8c83-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8c83-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="f8c83-111">See Also</span></span>  
 [<span data-ttu-id="f8c83-112">ISymUnmanagedScope – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f8c83-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
