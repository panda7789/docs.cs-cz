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
ms.openlocfilehash: 2b63dbcaa54e03e5603e06545f8b4fec393d8268
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424606"
---
# <a name="isymunmanagednamespacegetvariables-method"></a><span data-ttu-id="28c07-102">ISymUnmanagedNamespace::GetVariables – metoda</span><span class="sxs-lookup"><span data-stu-id="28c07-102">ISymUnmanagedNamespace::GetVariables Method</span></span>
<span data-ttu-id="28c07-103">Vrátí všechny proměnné definované v globálním oboru v rámci tento obor názvů.</span><span class="sxs-lookup"><span data-stu-id="28c07-103">Returns all variables defined at global scope within this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28c07-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="28c07-104">Syntax</span></span>  
  
```  
HRESULT GetVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars), length_is(*pcVars)]  
        ISymUnmanagedVariable *pVars[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="28c07-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="28c07-105">Parameters</span></span>  
 `cVars`  
 <span data-ttu-id="28c07-106">[v] A `ULONG32` určující velikost `pVars` pole.</span><span class="sxs-lookup"><span data-stu-id="28c07-106">[in] A `ULONG32` that indicates the size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="28c07-107">[out] Ukazatel na `ULONG32` která přijme velikost vyrovnávací paměti musí obsahovat obory názvů.</span><span class="sxs-lookup"><span data-stu-id="28c07-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `pVars`  
 <span data-ttu-id="28c07-108">[out] Ukazatel na vyrovnávací paměť, která obsahuje obory názvů.</span><span class="sxs-lookup"><span data-stu-id="28c07-108">[out] A pointer to a buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="28c07-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="28c07-109">Return Value</span></span>  
 <span data-ttu-id="28c07-110">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="28c07-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28c07-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="28c07-111">Requirements</span></span>  
 <span data-ttu-id="28c07-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="28c07-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28c07-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="28c07-113">See Also</span></span>  
 [<span data-ttu-id="28c07-114">ISymUnmanagedNamespace – rozhraní</span><span class="sxs-lookup"><span data-stu-id="28c07-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)
