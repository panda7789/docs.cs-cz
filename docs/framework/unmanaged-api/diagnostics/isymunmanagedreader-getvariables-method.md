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
ms.openlocfilehash: 74df7ee71fc541c35bc393f637ad1d7b9f7aa2a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425523"
---
# <a name="isymunmanagedreadergetvariables-method"></a><span data-ttu-id="7ac67-102">ISymUnmanagedReader::GetVariables – metoda</span><span class="sxs-lookup"><span data-stu-id="7ac67-102">ISymUnmanagedReader::GetVariables Method</span></span>
<span data-ttu-id="7ac67-103">Vrátí proměnnou jiné než místní, na základě jeho nadřazený a název.</span><span class="sxs-lookup"><span data-stu-id="7ac67-103">Returns a non-local variable, given its parent and name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ac67-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7ac67-104">Syntax</span></span>  
  
```  
HRESULT GetVariables (  
    [in]  mdToken  parent,  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is (cVars),  
        length_is (*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7ac67-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7ac67-105">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="7ac67-106">[v] Nadřazené proměnnou.</span><span class="sxs-lookup"><span data-stu-id="7ac67-106">[in] The parent of the variable.</span></span>  
  
 `cVars`  
 <span data-ttu-id="7ac67-107">[v] Velikost `pVars` pole.</span><span class="sxs-lookup"><span data-stu-id="7ac67-107">[in] The size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="7ac67-108">[out] Ukazatel na proměnnou, která přijímá počet proměnných, vrátí se v `pVars`.</span><span class="sxs-lookup"><span data-stu-id="7ac67-108">[out] A pointer to the variable that receives the number of variables returned in `pVars`.</span></span>  
  
 `pVars`  
 <span data-ttu-id="7ac67-109">[out] Ukazatel na proměnnou, která přijímá proměnné.</span><span class="sxs-lookup"><span data-stu-id="7ac67-109">[out] A pointer to the variable that receives the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7ac67-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7ac67-110">Return Value</span></span>  
 <span data-ttu-id="7ac67-111">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="7ac67-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ac67-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7ac67-112">Requirements</span></span>  
 <span data-ttu-id="7ac67-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7ac67-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ac67-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="7ac67-114">See Also</span></span>  
 [<span data-ttu-id="7ac67-115">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7ac67-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
