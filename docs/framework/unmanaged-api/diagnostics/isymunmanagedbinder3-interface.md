---
title: "ISymUnmanagedBinder3 – rozhraní"
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
- ISymUnmanagedBinder3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder3 Interface
helpviewer_keywords:
- ISymUnmanagedBinder3 interface [.NET Framework debugging]
ms.assetid: 37527a84-4b03-4f08-8135-94d898599089
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0c93275fc32e68f49618d93bdd0b54f1970121ee
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedbinder3-interface"></a><span data-ttu-id="15c1e-102">ISymUnmanagedBinder3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="15c1e-102">ISymUnmanagedBinder3 Interface</span></span>
<span data-ttu-id="15c1e-103">Rozšiřuje rozhraní symbol vazač.</span><span class="sxs-lookup"><span data-stu-id="15c1e-103">Extends the symbol binder interface.</span></span> <span data-ttu-id="15c1e-104">Získat toto rozhraní vyvoláním `QueryInterface` na objekt, který implementuje `ISymUnmanagedBinder` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="15c1e-104">Obtain this interface by calling `QueryInterface` on an object that implements the `ISymUnmanagedBinder` interface.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="15c1e-105">Je bezpečnostní riziko pro otevření souboru databáze (PDB) program z nedůvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="15c1e-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="15c1e-106">Metody</span><span class="sxs-lookup"><span data-stu-id="15c1e-106">Methods</span></span>  
  
|<span data-ttu-id="15c1e-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="15c1e-107">Method</span></span>|<span data-ttu-id="15c1e-108">Popis</span><span class="sxs-lookup"><span data-stu-id="15c1e-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="15c1e-109">GetReaderFromCallback – metoda</span><span class="sxs-lookup"><span data-stu-id="15c1e-109">GetReaderFromCallback Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)|<span data-ttu-id="15c1e-110">Umožňuje uživateli implementovat nebo zadat buď přes zpětného volání `IID_IDiaReadExeAtRVACallback` nebo `IID_IDiaReadExeAtOffsetCallback` získat informace o directory ladění z paměti</span><span class="sxs-lookup"><span data-stu-id="15c1e-110">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the Debug directory information from memory</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="15c1e-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="15c1e-111">Requirements</span></span>  
 <span data-ttu-id="15c1e-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="15c1e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15c1e-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="15c1e-113">See Also</span></span>  
 [<span data-ttu-id="15c1e-114">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="15c1e-114">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="15c1e-115">ISymUnmanagedBinder – rozhraní</span><span class="sxs-lookup"><span data-stu-id="15c1e-115">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 [<span data-ttu-id="15c1e-116">ISymUnmanagedBinder2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="15c1e-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
