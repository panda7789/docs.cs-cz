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
ms.openlocfilehash: 813f57377c1885b09190ada3c73f4391a3f2d931
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895059"
---
# <a name="isymunmanagednamespacegetvariables-method"></a><span data-ttu-id="e6fc8-102">ISymUnmanagedNamespace::GetVariables – metoda</span><span class="sxs-lookup"><span data-stu-id="e6fc8-102">ISymUnmanagedNamespace::GetVariables Method</span></span>
<span data-ttu-id="e6fc8-103">Vrátí všechny proměnné definované v globálním oboru v rámci tohoto oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e6fc8-103">Returns all variables defined at global scope within this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6fc8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6fc8-104">Syntax</span></span>  
  
```cpp
HRESULT GetVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars), length_is(*pcVars)]  
        ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6fc8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e6fc8-105">Parameters</span></span>  
 `cVars`  
 <span data-ttu-id="e6fc8-106">pro Který označuje velikost `pVars`pole. `ULONG32`</span><span class="sxs-lookup"><span data-stu-id="e6fc8-106">[in] A `ULONG32` that indicates the size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="e6fc8-107">mimo Ukazatel na `ULONG32` , který přijímá velikost vyrovnávací paměti vyžadované k omezení oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e6fc8-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `pVars`  
 <span data-ttu-id="e6fc8-108">mimo Ukazatel na vyrovnávací paměť, která obsahuje obory názvů.</span><span class="sxs-lookup"><span data-stu-id="e6fc8-108">[out] A pointer to a buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e6fc8-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e6fc8-109">Return Value</span></span>  
 <span data-ttu-id="e6fc8-110">S_OK, pokud je metoda úspěšná; jinak E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="e6fc8-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6fc8-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e6fc8-111">Requirements</span></span>  
 <span data-ttu-id="e6fc8-112">**Hlaviček** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e6fc8-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6fc8-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e6fc8-113">See also</span></span>

- [<span data-ttu-id="e6fc8-114">ISymUnmanagedNamespace – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e6fc8-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)
