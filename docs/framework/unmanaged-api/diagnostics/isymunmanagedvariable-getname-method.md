---
title: "ISymUnmanagedVariable::GetName – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable.GetName
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable::GetName
helpviewer_keywords:
- GetName method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetName method [.NET Framework debugging]
ms.assetid: eedf1ef0-9d4a-4847-a201-4e99572dfe5e
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0a50fe9d0fddc6239eb03c9007ec2ca64d7d27ce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedvariablegetname-method"></a><span data-ttu-id="388c7-102">ISymUnmanagedVariable::GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="388c7-102">ISymUnmanagedVariable::GetName Method</span></span>
<span data-ttu-id="388c7-103">Získá název této proměnné.</span><span class="sxs-lookup"><span data-stu-id="388c7-103">Gets the name of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="388c7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="388c7-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="388c7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="388c7-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="388c7-106">[v] Délka vyrovnávací paměti, která `pcchName` parametr odkazuje na.</span><span class="sxs-lookup"><span data-stu-id="388c7-106">[in] The length of the buffer that the `pcchName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="388c7-107">[out] Ukazatel na `ULONG32` velikostí, která přijme ve znacích vyrovnávací paměti musí obsahovat název, včetně ukončení hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="388c7-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="388c7-108">[out] Vyrovnávací paměť, která ukládá název.</span><span class="sxs-lookup"><span data-stu-id="388c7-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="388c7-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="388c7-109">Return Value</span></span>  
 <span data-ttu-id="388c7-110">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="388c7-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="388c7-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="388c7-111">Requirements</span></span>  
 <span data-ttu-id="388c7-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="388c7-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="388c7-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="388c7-113">See Also</span></span>  
 [<span data-ttu-id="388c7-114">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="388c7-114">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
