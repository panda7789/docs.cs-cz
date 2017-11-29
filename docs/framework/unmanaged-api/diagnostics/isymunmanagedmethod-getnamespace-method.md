---
title: "ISymUnmanagedMethod::GetNamespace – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedMethod.GetNamespace
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedMethod::GetNamespace
helpviewer_keywords:
- ISymUnmanagedMethod::GetNamespace method [.NET Framework debugging]
- GetNamespace method [.NET Framework debugging]
ms.assetid: 7fbbac42-b966-406d-9ae9-67bf3aea74ce
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5aff1bcd98e67f381340ed81a187db591c0986be
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedmethodgetnamespace-method"></a><span data-ttu-id="9b828-102">ISymUnmanagedMethod::GetNamespace – metoda</span><span class="sxs-lookup"><span data-stu-id="9b828-102">ISymUnmanagedMethod::GetNamespace Method</span></span>
<span data-ttu-id="9b828-103">Získá obor názvů, ve kterém je tato metoda definována.</span><span class="sxs-lookup"><span data-stu-id="9b828-103">Gets the namespace within which this method is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b828-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b828-104">Syntax</span></span>  
  
```  
HRESULT GetNamespace(  
   [out] ISymUnmanagedNamespace  **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9b828-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9b828-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="9b828-106">[out] Ukazatele, který je nastavený s vráceným [ISymUnmanagedNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9b828-106">[out] A pointer that is set to the returned [ISymUnmanagedNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9b828-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9b828-107">Return Value</span></span>  
 <span data-ttu-id="9b828-108">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="9b828-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b828-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9b828-109">Requirements</span></span>  
 <span data-ttu-id="9b828-110">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9b828-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b828-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="9b828-111">See Also</span></span>  
 [<span data-ttu-id="9b828-112">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9b828-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
