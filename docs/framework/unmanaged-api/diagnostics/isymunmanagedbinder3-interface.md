---
title: ISymUnmanagedBinder3 – rozhraní
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 06a4d5b1b108c15fa7ee4a7f5270b73f7adc1e6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426339"
---
# <a name="isymunmanagedbinder3-interface"></a><span data-ttu-id="b541a-102">ISymUnmanagedBinder3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b541a-102">ISymUnmanagedBinder3 Interface</span></span>
<span data-ttu-id="b541a-103">Rozšiřuje rozhraní symbol vazač.</span><span class="sxs-lookup"><span data-stu-id="b541a-103">Extends the symbol binder interface.</span></span> <span data-ttu-id="b541a-104">Získat toto rozhraní vyvoláním `QueryInterface` na objekt, který implementuje `ISymUnmanagedBinder` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b541a-104">Obtain this interface by calling `QueryInterface` on an object that implements the `ISymUnmanagedBinder` interface.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b541a-105">Je bezpečnostní riziko pro otevření souboru databáze (PDB) program z nedůvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="b541a-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b541a-106">Metody</span><span class="sxs-lookup"><span data-stu-id="b541a-106">Methods</span></span>  
  
|<span data-ttu-id="b541a-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="b541a-107">Method</span></span>|<span data-ttu-id="b541a-108">Popis</span><span class="sxs-lookup"><span data-stu-id="b541a-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b541a-109">GetReaderFromCallback – metoda</span><span class="sxs-lookup"><span data-stu-id="b541a-109">GetReaderFromCallback Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)|<span data-ttu-id="b541a-110">Umožňuje uživateli implementovat nebo zadat buď přes zpětného volání `IID_IDiaReadExeAtRVACallback` nebo `IID_IDiaReadExeAtOffsetCallback` získat informace o directory ladění z paměti</span><span class="sxs-lookup"><span data-stu-id="b541a-110">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the Debug directory information from memory</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b541a-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b541a-111">Requirements</span></span>  
 <span data-ttu-id="b541a-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b541a-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b541a-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="b541a-113">See Also</span></span>  
 [<span data-ttu-id="b541a-114">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="b541a-114">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="b541a-115">ISymUnmanagedBinder – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b541a-115">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 [<span data-ttu-id="b541a-116">ISymUnmanagedBinder2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b541a-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
