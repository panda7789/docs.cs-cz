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
ms.openlocfilehash: 8e81cea13fb8d25701ccbe163f112904baf47a9f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143159"
---
# <a name="isymunmanageddispose-interface"></a><span data-ttu-id="4d9be-102">ISymUnmanagedDispose – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4d9be-102">ISymUnmanagedDispose Interface</span></span>
<span data-ttu-id="4d9be-103">Uvolní nespravované prostředky.</span><span class="sxs-lookup"><span data-stu-id="4d9be-103">Disposes of unmanaged resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4d9be-104">Metody</span><span class="sxs-lookup"><span data-stu-id="4d9be-104">Methods</span></span>  
  
|<span data-ttu-id="4d9be-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="4d9be-105">Method</span></span>|<span data-ttu-id="4d9be-106">Popis</span><span class="sxs-lookup"><span data-stu-id="4d9be-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4d9be-107">Destroy – metoda</span><span class="sxs-lookup"><span data-stu-id="4d9be-107">Destroy Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-destroy-method.md)|<span data-ttu-id="4d9be-108">Způsobí, že základní objekt a uvolnit všechny vnitřní odkazy na všechna volání další metody, vrátí hodnotu neúspěch.</span><span class="sxs-lookup"><span data-stu-id="4d9be-108">Causes the underlying object to release all internal references and return failure on any subsequent method calls.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4d9be-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4d9be-109">Requirements</span></span>  
 <span data-ttu-id="4d9be-110">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4d9be-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d9be-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4d9be-111">See also</span></span>

- [<span data-ttu-id="4d9be-112">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="4d9be-112">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
