---
title: "ISymUnmanagedMethod::GetSequencePointCount – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedMethod.GetSequencePointCount
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedMethod::GetSequencePointCount
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePointCount method [.NET Framework debugging]
- GetSequencePointCount method [.NET Framework debugging]
ms.assetid: 836133e8-6108-4b9b-b0a9-bce4e08dccda
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1666eacd8756209c126171ad8ecae56afa802892
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedmethodgetsequencepointcount-method"></a><span data-ttu-id="9fa74-102">ISymUnmanagedMethod::GetSequencePointCount – metoda</span><span class="sxs-lookup"><span data-stu-id="9fa74-102">ISymUnmanagedMethod::GetSequencePointCount Method</span></span>
<span data-ttu-id="9fa74-103">Získá počet bodů pořadí v rámci této metody.</span><span class="sxs-lookup"><span data-stu-id="9fa74-103">Gets the count of sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fa74-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9fa74-104">Syntax</span></span>  
  
```  
HRESULT GetSequencePointCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9fa74-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9fa74-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="9fa74-106">[out] Ukazatel na `ULONG32` která přijme velikost vyrovnávací paměti musí obsahovat body sekvence.</span><span class="sxs-lookup"><span data-stu-id="9fa74-106">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the sequence points.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9fa74-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9fa74-107">Return Value</span></span>  
 <span data-ttu-id="9fa74-108">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="9fa74-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fa74-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9fa74-109">Requirements</span></span>  
 <span data-ttu-id="9fa74-110">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9fa74-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fa74-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="9fa74-111">See Also</span></span>  
 [<span data-ttu-id="9fa74-112">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9fa74-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
