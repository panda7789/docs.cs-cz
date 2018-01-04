---
title: "ISymUnmanagedReader::GetGlobalVariables – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetGlobalVariables
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetGlobalVariables
helpviewer_keywords:
- GetGlobalVariables method [.NET Framework debugging]
- ISymUnmanagedReader::GetGlobalVariables method [.NET Framework debugging]
ms.assetid: a2dd5098-3e58-4be5-b7a2-e4160b3b505a
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b17abe352dc37b366294e72de53bcc4e1ad8dc9d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadergetglobalvariables-method"></a><span data-ttu-id="55f4a-102">ISymUnmanagedReader::GetGlobalVariables – metoda</span><span class="sxs-lookup"><span data-stu-id="55f4a-102">ISymUnmanagedReader::GetGlobalVariables Method</span></span>
<span data-ttu-id="55f4a-103">Vrátí všechny globální proměnné.</span><span class="sxs-lookup"><span data-stu-id="55f4a-103">Returns all global variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55f4a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55f4a-104">Syntax</span></span>  
  
```  
HRESULT GetGlobalVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars),  
        length_is(*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="55f4a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="55f4a-105">Parameters</span></span>  
 `cVars`  
 <span data-ttu-id="55f4a-106">[v] Délka vyrovnávací paměti na kterou odkazuje `pcVars`.</span><span class="sxs-lookup"><span data-stu-id="55f4a-106">[in] The length of the buffer pointed to by `pcVars`.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="55f4a-107">[out] Ukazatel na `ULONG32` která přijme velikost vyrovnávací paměti musí obsahovat proměnné.</span><span class="sxs-lookup"><span data-stu-id="55f4a-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the variables.</span></span>  
  
 `pVars`  
 <span data-ttu-id="55f4a-108">[out] Vyrovnávací paměť, která obsahuje proměnné.</span><span class="sxs-lookup"><span data-stu-id="55f4a-108">[out] A buffer that contains the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="55f4a-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="55f4a-109">Return Value</span></span>  
 <span data-ttu-id="55f4a-110">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="55f4a-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55f4a-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="55f4a-111">Requirements</span></span>  
 <span data-ttu-id="55f4a-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="55f4a-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55f4a-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="55f4a-113">See Also</span></span>  
 [<span data-ttu-id="55f4a-114">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="55f4a-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
