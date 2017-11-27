---
title: "ISymUnmanagedDispose::Destroy – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDispose.Destroy
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDispose::Destroy
helpviewer_keywords:
- ISymUnmanagedDispose::Destroy method [.NET Framework debugging]
- Destroy method [.NET Framework debugging]
ms.assetid: a854ab9f-d2ba-470e-867f-808c1e7bd07a
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d808392d883d1168d6aad8d16ab50ce072b1d9f7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanageddisposedestroy-method"></a><span data-ttu-id="4a01d-102">ISymUnmanagedDispose::Destroy – metoda</span><span class="sxs-lookup"><span data-stu-id="4a01d-102">ISymUnmanagedDispose::Destroy Method</span></span>
<span data-ttu-id="4a01d-103">Způsobí, že základní objekt, který chcete uvolnit všechny odkazy interní a vrátí hodnotu Neúspěch na všechny následné metoda volání.</span><span class="sxs-lookup"><span data-stu-id="4a01d-103">Causes the underlying object to release all internal references and return failure on any subsequent method calls.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a01d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a01d-104">Syntax</span></span>  
  
```  
HRESULT Destroy();  
```  
  
## <a name="return-value"></a><span data-ttu-id="4a01d-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4a01d-105">Return Value</span></span>  
 <span data-ttu-id="4a01d-106">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="4a01d-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a01d-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4a01d-107">Requirements</span></span>  
 <span data-ttu-id="4a01d-108">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4a01d-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a01d-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="4a01d-109">See Also</span></span>  
 [<span data-ttu-id="4a01d-110">Isymunmanageddispose – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4a01d-110">ISymUnmanagedDispose Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)
