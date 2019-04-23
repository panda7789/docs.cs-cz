---
title: ISymUnmanagedWriter3::Commit – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f531b96211a1dd6072d62937b9f93fc17f105d4d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59149042"
---
# <a name="isymunmanagedwriter3commit-method"></a><span data-ttu-id="617f6-102">ISymUnmanagedWriter3::Commit – metoda</span><span class="sxs-lookup"><span data-stu-id="617f6-102">ISymUnmanagedWriter3::Commit Method</span></span>
<span data-ttu-id="617f6-103">Potvrdí změny doposud zapsán do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="617f6-103">Commits the changes written so far to the stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="617f6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="617f6-104">Syntax</span></span>  
  
```  
HRESULT Commit();  
```  
  
## <a name="return-value"></a><span data-ttu-id="617f6-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="617f6-105">Return Value</span></span>  
 <span data-ttu-id="617f6-106">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="617f6-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="617f6-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="617f6-107">Requirements</span></span>  
 <span data-ttu-id="617f6-108">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="617f6-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="617f6-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="617f6-109">See also</span></span>

- [<span data-ttu-id="617f6-110">ISymUnmanagedWriter3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="617f6-110">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
