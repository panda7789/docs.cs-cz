---
title: ISymUnmanagedDispose::Destroy – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDispose.Destroy
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDispose::Destroy
helpviewer_keywords:
- ISymUnmanagedDispose::Destroy method [.NET Framework debugging]
- Destroy method [.NET Framework debugging]
ms.assetid: a854ab9f-d2ba-470e-867f-808c1e7bd07a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6d4b5f94bdbb7319cef14c8b86f8ea995df7ff21
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424479"
---
# <a name="isymunmanageddisposedestroy-method"></a><span data-ttu-id="262eb-102">ISymUnmanagedDispose::Destroy – metoda</span><span class="sxs-lookup"><span data-stu-id="262eb-102">ISymUnmanagedDispose::Destroy Method</span></span>
<span data-ttu-id="262eb-103">Způsobí, že základní objekt, který chcete uvolnit všechny odkazy interní a vrátí hodnotu Neúspěch na všechny následné metoda volání.</span><span class="sxs-lookup"><span data-stu-id="262eb-103">Causes the underlying object to release all internal references and return failure on any subsequent method calls.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="262eb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="262eb-104">Syntax</span></span>  
  
```  
HRESULT Destroy();  
```  
  
## <a name="return-value"></a><span data-ttu-id="262eb-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="262eb-105">Return Value</span></span>  
 <span data-ttu-id="262eb-106">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="262eb-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="262eb-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="262eb-107">Requirements</span></span>  
 <span data-ttu-id="262eb-108">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="262eb-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="262eb-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="262eb-109">See Also</span></span>  
 [<span data-ttu-id="262eb-110">ISymUnmanagedDispose – rozhraní</span><span class="sxs-lookup"><span data-stu-id="262eb-110">ISymUnmanagedDispose Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)
