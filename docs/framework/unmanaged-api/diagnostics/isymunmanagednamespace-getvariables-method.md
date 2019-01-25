---
title: ISymUnmanagedNamespace::GetVariables – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetVariables
helpviewer_keywords:
- ISymUnmanagedNamespace::GetVariables method [.NET Framework debugging]
- GetVariables method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: ea7c1617-f3ce-4220-8288-f2b50eaf0f0f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 11a5eb01a3e354b4360bea59af1e63ffeb0576aa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730110"
---
# <a name="isymunmanagednamespacegetvariables-method"></a><span data-ttu-id="fb522-102">ISymUnmanagedNamespace::GetVariables – metoda</span><span class="sxs-lookup"><span data-stu-id="fb522-102">ISymUnmanagedNamespace::GetVariables Method</span></span>
<span data-ttu-id="fb522-103">Vrátí všechny proměnné definované v globálním oboru v rámci tohoto oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="fb522-103">Returns all variables defined at global scope within this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb522-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb522-104">Syntax</span></span>  
  
```  
HRESULT GetVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars), length_is(*pcVars)]  
        ISymUnmanagedVariable *pVars[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fb522-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fb522-105">Parameters</span></span>  
 `cVars`  
 <span data-ttu-id="fb522-106">[in] A `ULONG32` , který označuje velikost `pVars` pole.</span><span class="sxs-lookup"><span data-stu-id="fb522-106">[in] A `ULONG32` that indicates the size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="fb522-107">[out] Ukazatel `ULONG32` , která obdrží velikost vyrovnávací paměti musí obsahovat obory názvů.</span><span class="sxs-lookup"><span data-stu-id="fb522-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `pVars`  
 <span data-ttu-id="fb522-108">[out] Ukazatel do vyrovnávací paměti, která obsahuje obory názvů.</span><span class="sxs-lookup"><span data-stu-id="fb522-108">[out] A pointer to a buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fb522-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fb522-109">Return Value</span></span>  
 <span data-ttu-id="fb522-110">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="fb522-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb522-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fb522-111">Requirements</span></span>  
 <span data-ttu-id="fb522-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fb522-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb522-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fb522-113">See also</span></span>
- [<span data-ttu-id="fb522-114">ISymUnmanagedNamespace – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb522-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)
