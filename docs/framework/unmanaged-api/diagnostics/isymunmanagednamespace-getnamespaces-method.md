---
title: ISymUnmanagedNamespace::GetNamespaces – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetNamespaces
helpviewer_keywords:
- ISymUnmanagedNamespace::GetNamespaces method [.NET Framework debugging]
- GetNamespaces method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: 0ea9d9af-8709-4a46-872b-f54d9e840088
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3d7ac84971f7d0e97f7ccd26710151d1aeefe729
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939500"
---
# <a name="isymunmanagednamespacegetnamespaces-method"></a><span data-ttu-id="2e6be-102">ISymUnmanagedNamespace::GetNamespaces – metoda</span><span class="sxs-lookup"><span data-stu-id="2e6be-102">ISymUnmanagedNamespace::GetNamespaces Method</span></span>
<span data-ttu-id="2e6be-103">Získá podřízené objekty tohoto oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="2e6be-103">Gets the children of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e6be-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e6be-104">Syntax</span></span>  
  
```  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces), length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e6be-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2e6be-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="2e6be-106">[in] A `ULONG32` , který označuje velikost `namespaces` pole.</span><span class="sxs-lookup"><span data-stu-id="2e6be-106">[in] A `ULONG32` that indicates the size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="2e6be-107">[out] Ukazatel `ULONG32` , která obdrží velikost ve znacích, vyrovnávací paměti musí obsahovat obory názvů.</span><span class="sxs-lookup"><span data-stu-id="2e6be-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="2e6be-108">[out] Ukazatel do vyrovnávací paměti, která obsahuje obory názvů.</span><span class="sxs-lookup"><span data-stu-id="2e6be-108">[out] A pointer to the buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2e6be-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2e6be-109">Return Value</span></span>  
 <span data-ttu-id="2e6be-110">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="2e6be-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e6be-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2e6be-111">Requirements</span></span>  
 <span data-ttu-id="2e6be-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2e6be-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e6be-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2e6be-113">See also</span></span>

- [<span data-ttu-id="2e6be-114">ISymUnmanagedNamespace – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e6be-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)
