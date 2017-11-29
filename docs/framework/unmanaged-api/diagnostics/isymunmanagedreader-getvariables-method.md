---
title: "ISymUnmanagedReader::GetVariables – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetVariables
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetVariables
helpviewer_keywords:
- ISymUnmanagedReader::GetVariables method [.NET Framework debugging]
- GetVariables method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 16dc49cb-2c60-4ac8-9c35-020e9afba3f8
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b9ef176b3863b2c1c9422bfd0aeb8814401a22d2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreadergetvariables-method"></a><span data-ttu-id="e5610-102">ISymUnmanagedReader::GetVariables – metoda</span><span class="sxs-lookup"><span data-stu-id="e5610-102">ISymUnmanagedReader::GetVariables Method</span></span>
<span data-ttu-id="e5610-103">Vrátí proměnnou jiné než místní, na základě jeho nadřazený a název.</span><span class="sxs-lookup"><span data-stu-id="e5610-103">Returns a non-local variable, given its parent and name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5610-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5610-104">Syntax</span></span>  
  
```  
HRESULT GetVariables (  
    [in]  mdToken  parent,  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is (cVars),  
        length_is (*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e5610-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e5610-105">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="e5610-106">[v] Nadřazené proměnnou.</span><span class="sxs-lookup"><span data-stu-id="e5610-106">[in] The parent of the variable.</span></span>  
  
 `cVars`  
 <span data-ttu-id="e5610-107">[v] Velikost `pVars` pole.</span><span class="sxs-lookup"><span data-stu-id="e5610-107">[in] The size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="e5610-108">[out] Ukazatel na proměnnou, která přijímá počet proměnných, vrátí se v `pVars`.</span><span class="sxs-lookup"><span data-stu-id="e5610-108">[out] A pointer to the variable that receives the number of variables returned in `pVars`.</span></span>  
  
 `pVars`  
 <span data-ttu-id="e5610-109">[out] Ukazatel na proměnnou, která přijímá proměnné.</span><span class="sxs-lookup"><span data-stu-id="e5610-109">[out] A pointer to the variable that receives the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e5610-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e5610-110">Return Value</span></span>  
 <span data-ttu-id="e5610-111">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="e5610-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5610-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e5610-112">Requirements</span></span>  
 <span data-ttu-id="e5610-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e5610-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5610-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="e5610-114">See Also</span></span>  
 [<span data-ttu-id="e5610-115">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e5610-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
