---
title: ISymUnmanagedDispose – rozhraní
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDispose
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDispose
helpviewer_keywords:
- ISymUnmanagedDispose interface [.NET Framework debugging]
ms.assetid: b1d74e83-a200-4d00-8fbd-27918808616d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 973fc35bb99bea6b3302760763069b9df6c548e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424401"
---
# <a name="isymunmanageddispose-interface"></a><span data-ttu-id="db32c-102">ISymUnmanagedDispose – rozhraní</span><span class="sxs-lookup"><span data-stu-id="db32c-102">ISymUnmanagedDispose Interface</span></span>
<span data-ttu-id="db32c-103">Uvolní nespravované prostředky.</span><span class="sxs-lookup"><span data-stu-id="db32c-103">Disposes of unmanaged resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="db32c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="db32c-104">Methods</span></span>  
  
|<span data-ttu-id="db32c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="db32c-105">Method</span></span>|<span data-ttu-id="db32c-106">Popis</span><span class="sxs-lookup"><span data-stu-id="db32c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="db32c-107">Destroy – metoda</span><span class="sxs-lookup"><span data-stu-id="db32c-107">Destroy Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-destroy-method.md)|<span data-ttu-id="db32c-108">Způsobí, že základní objekt, který chcete uvolnit všechny odkazy interní a vrátí hodnotu Neúspěch na všechny následné metoda volání.</span><span class="sxs-lookup"><span data-stu-id="db32c-108">Causes the underlying object to release all internal references and return failure on any subsequent method calls.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="db32c-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="db32c-109">Requirements</span></span>  
 <span data-ttu-id="db32c-110">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="db32c-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db32c-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="db32c-111">See Also</span></span>  
 [<span data-ttu-id="db32c-112">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="db32c-112">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
