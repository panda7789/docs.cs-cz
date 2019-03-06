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
ms.openlocfilehash: 38d9c3eeb5cdb8b15ef5306a641910f2f4bcc9cf
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372344"
---
# <a name="isymunmanagedwriter3commit-method"></a><span data-ttu-id="51cca-102">ISymUnmanagedWriter3::Commit – metoda</span><span class="sxs-lookup"><span data-stu-id="51cca-102">ISymUnmanagedWriter3::Commit Method</span></span>
<span data-ttu-id="51cca-103">Potvrdí změny doposud zapsán do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="51cca-103">Commits the changes written so far to the stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51cca-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51cca-104">Syntax</span></span>  
  
```  
HRESULT Commit();  
```  
  
## <a name="return-value"></a><span data-ttu-id="51cca-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="51cca-105">Return Value</span></span>  
 <span data-ttu-id="51cca-106">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="51cca-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51cca-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="51cca-107">Requirements</span></span>  
 <span data-ttu-id="51cca-108">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="51cca-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51cca-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="51cca-109">See also</span></span>
- [<span data-ttu-id="51cca-110">ISymUnmanagedWriter3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="51cca-110">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
