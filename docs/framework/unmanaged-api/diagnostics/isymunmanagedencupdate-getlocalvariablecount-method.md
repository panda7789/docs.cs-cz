---
title: ISymUnmanagedENCUpdate::GetLocalVariableCount – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.GetLocalVariableCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount method [.NET Framework debugging]
- GetLocalVariableCount method [.NET Framework debugging]
ms.assetid: 9777d8bb-4abc-4be8-aa7c-34f853eceb9c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d56785815105e2f4b06217d3375e2d1cfdf0494c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776906"
---
# <a name="isymunmanagedencupdategetlocalvariablecount-method"></a><span data-ttu-id="d3f6d-102">ISymUnmanagedENCUpdate::GetLocalVariableCount – metoda</span><span class="sxs-lookup"><span data-stu-id="d3f6d-102">ISymUnmanagedENCUpdate::GetLocalVariableCount Method</span></span>
<span data-ttu-id="d3f6d-103">Získá počet místních proměnných.</span><span class="sxs-lookup"><span data-stu-id="d3f6d-103">Gets the number of local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3f6d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3f6d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVariableCount(  
    [in]  mdMethodDef  mdMethodToken,  
    [out] ULONG        *pcLocals);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3f6d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d3f6d-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="d3f6d-106">[in] Token metadat z metod.</span><span class="sxs-lookup"><span data-stu-id="d3f6d-106">[in] The metadata token of methods.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="d3f6d-107">[out] Ukazatel `ULONG32` , která obdrží velikost ve znacích, vyrovnávací paměti musí obsahovat počet místních proměnných.</span><span class="sxs-lookup"><span data-stu-id="d3f6d-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the number of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d3f6d-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d3f6d-108">Return Value</span></span>  
 <span data-ttu-id="d3f6d-109">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="d3f6d-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3f6d-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d3f6d-110">Requirements</span></span>  
 <span data-ttu-id="d3f6d-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d3f6d-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3f6d-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d3f6d-112">See also</span></span>

- [<span data-ttu-id="d3f6d-113">ISymUnmanagedENCUpdate – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d3f6d-113">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
