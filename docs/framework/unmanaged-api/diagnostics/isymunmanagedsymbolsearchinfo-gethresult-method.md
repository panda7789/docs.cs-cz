---
title: "ISymUnmanagedSymbolSearchInfo::GetHRESULT – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedSymbolSearchInfo.GetHRESULT
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedSymbolSearchInfo::GetHRESULT
helpviewer_keywords:
- ISymUnmanagedSymbolSearchInfo::GetHRESULT method [.NET Framework debugging]
- GetHRESULT method [.NET Framework debugging]
ms.assetid: 6999dc3d-65d7-4bf6-bb0a-6efc0fc72588
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 42f2e0053a83d4ef7414791626ec204671429a3f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedsymbolsearchinfogethresult-method"></a><span data-ttu-id="08dc9-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT – metoda</span><span class="sxs-lookup"><span data-stu-id="08dc9-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT Method</span></span>
<span data-ttu-id="08dc9-103">Získá hodnota HRESULT.</span><span class="sxs-lookup"><span data-stu-id="08dc9-103">Gets the HRESULT.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08dc9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08dc9-104">Syntax</span></span>  
  
```  
HRESULT GetHRESULT(  
    [out] HRESULT *phr);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="08dc9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="08dc9-105">Parameters</span></span>  
 `phr`  
 <span data-ttu-id="08dc9-106">[out] Ukazatel HRESULT.</span><span class="sxs-lookup"><span data-stu-id="08dc9-106">[out] A pointer to the HRESULT.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="08dc9-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="08dc9-107">Return Value</span></span>  
 <span data-ttu-id="08dc9-108">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="08dc9-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08dc9-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="08dc9-109">Requirements</span></span>  
 <span data-ttu-id="08dc9-110">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="08dc9-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08dc9-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="08dc9-111">See Also</span></span>  
 [<span data-ttu-id="08dc9-112">Isymunmanagedsymbolsearchinfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="08dc9-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)
