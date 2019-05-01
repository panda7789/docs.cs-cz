---
title: ISymUnmanagedReader::GetGlobalVariables – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetGlobalVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetGlobalVariables
helpviewer_keywords:
- GetGlobalVariables method [.NET Framework debugging]
- ISymUnmanagedReader::GetGlobalVariables method [.NET Framework debugging]
ms.assetid: a2dd5098-3e58-4be5-b7a2-e4160b3b505a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e778a5a7baed52941a7f4b990b34d31f8ca84c24
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986385"
---
# <a name="isymunmanagedreadergetglobalvariables-method"></a><span data-ttu-id="6a792-102">ISymUnmanagedReader::GetGlobalVariables – metoda</span><span class="sxs-lookup"><span data-stu-id="6a792-102">ISymUnmanagedReader::GetGlobalVariables Method</span></span>
<span data-ttu-id="6a792-103">Vrátí všechny globální proměnné.</span><span class="sxs-lookup"><span data-stu-id="6a792-103">Returns all global variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a792-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a792-104">Syntax</span></span>  
  
```  
HRESULT GetGlobalVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars),  
        length_is(*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a792-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6a792-105">Parameters</span></span>  
 `cVars`  
 <span data-ttu-id="6a792-106">[in] Délka vyrovnávací paměti na které odkazuje `pcVars`.</span><span class="sxs-lookup"><span data-stu-id="6a792-106">[in] The length of the buffer pointed to by `pcVars`.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="6a792-107">[out] Ukazatel `ULONG32` , která obdrží velikost vyrovnávací paměti musí obsahovat proměnné.</span><span class="sxs-lookup"><span data-stu-id="6a792-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the variables.</span></span>  
  
 `pVars`  
 <span data-ttu-id="6a792-108">[out] Vyrovnávací paměť obsahující proměnné.</span><span class="sxs-lookup"><span data-stu-id="6a792-108">[out] A buffer that contains the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6a792-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6a792-109">Return Value</span></span>  
 <span data-ttu-id="6a792-110">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="6a792-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a792-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6a792-111">Requirements</span></span>  
 <span data-ttu-id="6a792-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6a792-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a792-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6a792-113">See also</span></span>

- [<span data-ttu-id="6a792-114">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6a792-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
