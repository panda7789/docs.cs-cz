---
title: "ISymUnmanagedWriter3::Commit – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedWriter3.Commit
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3::Commit
helpviewer_keywords:
- Commit method, ISymUnmanagedWriter3 interface [.NET Framework debugging]
- ISymUnmanagedWriter3::Commit method [.NET Framework debugging]
ms.assetid: f6961922-46ec-4d2c-8369-85f880731f37
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 10c36f1972e3c55b22a472c81ec8499fcfde3405
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter3commit-method"></a><span data-ttu-id="38a41-102">ISymUnmanagedWriter3::Commit – metoda</span><span class="sxs-lookup"><span data-stu-id="38a41-102">ISymUnmanagedWriter3::Commit Method</span></span>
<span data-ttu-id="38a41-103">Potvrdí změny dosavadní zapisovat do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="38a41-103">Commits the changes written so far to the stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38a41-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38a41-104">Syntax</span></span>  
  
```  
HRESULT Commit();  
```  
  
## <a name="return-value"></a><span data-ttu-id="38a41-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="38a41-105">Return Value</span></span>  
 <span data-ttu-id="38a41-106">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="38a41-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38a41-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="38a41-107">Requirements</span></span>  
 <span data-ttu-id="38a41-108">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="38a41-108">**Header:** CorSym.idl , CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38a41-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="38a41-109">See Also</span></span>  
 [<span data-ttu-id="38a41-110">ISymUnmanagedWriter3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="38a41-110">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
