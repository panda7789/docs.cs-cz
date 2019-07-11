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
ms.openlocfilehash: d2c64d7ead2f7ce3d76b40f4fdc604506ee85561
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777888"
---
# <a name="isymunmanagedscopegetnamespaces-method"></a><span data-ttu-id="d1a15-102">ISymUnmanagedScope::GetNamespaces – metoda</span><span class="sxs-lookup"><span data-stu-id="d1a15-102">ISymUnmanagedScope::GetNamespaces Method</span></span>
<span data-ttu-id="d1a15-103">Získá obory názvů, které se používají v rámci tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="d1a15-103">Gets the namespaces that are being used within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1a15-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1a15-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces),  
        length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1a15-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d1a15-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="d1a15-106">[in] Velikost `namespaces` pole.</span><span class="sxs-lookup"><span data-stu-id="d1a15-106">[in] The size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="d1a15-107">[out] Ukazatel `ULONG32` , která obdrží velikost vyrovnávací paměti musí obsahovat obory názvů.</span><span class="sxs-lookup"><span data-stu-id="d1a15-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="d1a15-108">[out] Pole, která přijímá obory názvů.</span><span class="sxs-lookup"><span data-stu-id="d1a15-108">[out] The array that receives the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d1a15-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d1a15-109">Return Value</span></span>  
 <span data-ttu-id="d1a15-110">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="d1a15-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1a15-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d1a15-111">Requirements</span></span>  
 <span data-ttu-id="d1a15-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d1a15-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1a15-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d1a15-113">See also</span></span>

- [<span data-ttu-id="d1a15-114">ISymUnmanagedScope – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d1a15-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
