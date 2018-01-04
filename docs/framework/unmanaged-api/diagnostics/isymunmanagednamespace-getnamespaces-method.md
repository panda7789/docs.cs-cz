---
title: "ISymUnmanagedNamespace::GetNamespaces – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedNamespace.GetNamespaces
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedNamespace::GetNamespaces
helpviewer_keywords:
- ISymUnmanagedNamespace::GetNamespaces method [.NET Framework debugging]
- GetNamespaces method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: 0ea9d9af-8709-4a46-872b-f54d9e840088
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 69ee0f6385abf78a368d488d0190796516c4f3d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagednamespacegetnamespaces-method"></a><span data-ttu-id="f9ed2-102">ISymUnmanagedNamespace::GetNamespaces – metoda</span><span class="sxs-lookup"><span data-stu-id="f9ed2-102">ISymUnmanagedNamespace::GetNamespaces Method</span></span>
<span data-ttu-id="f9ed2-103">Získá podřízené objekty daného tento obor názvů.</span><span class="sxs-lookup"><span data-stu-id="f9ed2-103">Gets the children of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9ed2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9ed2-104">Syntax</span></span>  
  
```  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces), length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f9ed2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9ed2-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="f9ed2-106">[v] A `ULONG32` určující velikost `namespaces` pole.</span><span class="sxs-lookup"><span data-stu-id="f9ed2-106">[in] A `ULONG32` that indicates the size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="f9ed2-107">[out] Ukazatel na `ULONG32` velikostí, která přijme ve znacích vyrovnávací paměti musí obsahovat obory názvů.</span><span class="sxs-lookup"><span data-stu-id="f9ed2-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="f9ed2-108">[out] Ukazatel na vyrovnávací paměť, která obsahuje obory názvů.</span><span class="sxs-lookup"><span data-stu-id="f9ed2-108">[out] A pointer to the buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f9ed2-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f9ed2-109">Return Value</span></span>  
 <span data-ttu-id="f9ed2-110">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="f9ed2-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9ed2-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f9ed2-111">Requirements</span></span>  
 <span data-ttu-id="f9ed2-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f9ed2-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9ed2-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="f9ed2-113">See Also</span></span>  
 [<span data-ttu-id="f9ed2-114">ISymUnmanagedNamespace – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f9ed2-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)
