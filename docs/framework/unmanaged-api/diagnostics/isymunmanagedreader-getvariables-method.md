---
title: ISymUnmanagedReader::GetVariables – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetVariables
helpviewer_keywords:
- ISymUnmanagedReader::GetVariables method [.NET Framework debugging]
- GetVariables method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 16dc49cb-2c60-4ac8-9c35-020e9afba3f8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 846ff76fb1073394cc27597c9a2015148581cc70
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61669998"
---
# <a name="isymunmanagedreadergetvariables-method"></a><span data-ttu-id="b96ee-102">ISymUnmanagedReader::GetVariables – metoda</span><span class="sxs-lookup"><span data-stu-id="b96ee-102">ISymUnmanagedReader::GetVariables Method</span></span>
<span data-ttu-id="b96ee-103">Vrátí jiné než místní proměnné, na základě jeho nadřazený a název.</span><span class="sxs-lookup"><span data-stu-id="b96ee-103">Returns a non-local variable, given its parent and name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b96ee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b96ee-104">Syntax</span></span>  
  
```  
HRESULT GetVariables (  
    [in]  mdToken  parent,  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is (cVars),  
        length_is (*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b96ee-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b96ee-105">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="b96ee-106">[in] Nadřazený proměnné.</span><span class="sxs-lookup"><span data-stu-id="b96ee-106">[in] The parent of the variable.</span></span>  
  
 `cVars`  
 <span data-ttu-id="b96ee-107">[in] Velikost `pVars` pole.</span><span class="sxs-lookup"><span data-stu-id="b96ee-107">[in] The size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="b96ee-108">[out] Ukazatel na proměnnou, která přijímá počet proměnné vrátí v `pVars`.</span><span class="sxs-lookup"><span data-stu-id="b96ee-108">[out] A pointer to the variable that receives the number of variables returned in `pVars`.</span></span>  
  
 `pVars`  
 <span data-ttu-id="b96ee-109">[out] Ukazatel na proměnnou, která přijímá proměnné.</span><span class="sxs-lookup"><span data-stu-id="b96ee-109">[out] A pointer to the variable that receives the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b96ee-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b96ee-110">Return Value</span></span>  
 <span data-ttu-id="b96ee-111">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="b96ee-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b96ee-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b96ee-112">Requirements</span></span>  
 <span data-ttu-id="b96ee-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b96ee-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b96ee-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b96ee-114">See also</span></span>

- [<span data-ttu-id="b96ee-115">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b96ee-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
