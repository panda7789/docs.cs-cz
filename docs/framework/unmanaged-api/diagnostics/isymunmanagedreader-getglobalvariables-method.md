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
ms.openlocfilehash: cad85da193220c766da393a753501400e698ee8d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreadergetglobalvariables-method"></a><span data-ttu-id="04ec2-102">ISymUnmanagedReader::GetGlobalVariables – metoda</span><span class="sxs-lookup"><span data-stu-id="04ec2-102">ISymUnmanagedReader::GetGlobalVariables Method</span></span>
<span data-ttu-id="04ec2-103">Vrátí všechny globální proměnné.</span><span class="sxs-lookup"><span data-stu-id="04ec2-103">Returns all global variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04ec2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04ec2-104">Syntax</span></span>  
  
```  
HRESULT GetGlobalVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars),  
        length_is(*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="04ec2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="04ec2-105">Parameters</span></span>  
 `cVars`  
 <span data-ttu-id="04ec2-106">[v] Délka vyrovnávací paměti na kterou odkazuje `pcVars`.</span><span class="sxs-lookup"><span data-stu-id="04ec2-106">[in] The length of the buffer pointed to by `pcVars`.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="04ec2-107">[out] Ukazatel na `ULONG32` která přijme velikost vyrovnávací paměti musí obsahovat proměnné.</span><span class="sxs-lookup"><span data-stu-id="04ec2-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the variables.</span></span>  
  
 `pVars`  
 <span data-ttu-id="04ec2-108">[out] Vyrovnávací paměť, která obsahuje proměnné.</span><span class="sxs-lookup"><span data-stu-id="04ec2-108">[out] A buffer that contains the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="04ec2-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="04ec2-109">Return Value</span></span>  
 <span data-ttu-id="04ec2-110">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="04ec2-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04ec2-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="04ec2-111">Requirements</span></span>  
 <span data-ttu-id="04ec2-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="04ec2-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04ec2-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="04ec2-113">See Also</span></span>  
 [<span data-ttu-id="04ec2-114">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="04ec2-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
