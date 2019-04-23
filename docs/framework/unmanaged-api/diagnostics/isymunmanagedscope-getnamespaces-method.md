---
title: ISymUnmanagedScope::GetNamespaces – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetNamespaces
helpviewer_keywords:
- GetNamespaces method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetNamespaces method [.NET Framework debugging]
ms.assetid: c44b0440-04bd-460a-84fb-41afecf44503
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3dc3c842bbb4b86b82d03848751673400bed193b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59213035"
---
# <a name="isymunmanagedscopegetnamespaces-method"></a><span data-ttu-id="3a874-102">ISymUnmanagedScope::GetNamespaces – metoda</span><span class="sxs-lookup"><span data-stu-id="3a874-102">ISymUnmanagedScope::GetNamespaces Method</span></span>
<span data-ttu-id="3a874-103">Získá obory názvů, které se používají v rámci tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="3a874-103">Gets the namespaces that are being used within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a874-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3a874-104">Syntax</span></span>  
  
```  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces),  
        length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a874-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3a874-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="3a874-106">[in] Velikost `namespaces` pole.</span><span class="sxs-lookup"><span data-stu-id="3a874-106">[in] The size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="3a874-107">[out] Ukazatel `ULONG32` , která obdrží velikost vyrovnávací paměti musí obsahovat obory názvů.</span><span class="sxs-lookup"><span data-stu-id="3a874-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="3a874-108">[out] Pole, která přijímá obory názvů.</span><span class="sxs-lookup"><span data-stu-id="3a874-108">[out] The array that receives the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3a874-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3a874-109">Return Value</span></span>  
 <span data-ttu-id="3a874-110">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="3a874-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a874-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3a874-111">Requirements</span></span>  
 <span data-ttu-id="3a874-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3a874-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a874-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3a874-113">See also</span></span>

- [<span data-ttu-id="3a874-114">ISymUnmanagedScope – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3a874-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
