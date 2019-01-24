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
ms.openlocfilehash: be91591bfbbe4531c5518b90e560bc05457c92da
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730162"
---
# <a name="isymunmanagedbinder3-interface"></a><span data-ttu-id="f70aa-102">ISymUnmanagedBinder3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f70aa-102">ISymUnmanagedBinder3 Interface</span></span>
<span data-ttu-id="f70aa-103">Rozšiřuje rozhraní symbol vazače.</span><span class="sxs-lookup"><span data-stu-id="f70aa-103">Extends the symbol binder interface.</span></span> <span data-ttu-id="f70aa-104">Získat po zavolání tohoto rozhraní `QueryInterface` na objekt, který implementuje `ISymUnmanagedBinder` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f70aa-104">Obtain this interface by calling `QueryInterface` on an object that implements the `ISymUnmanagedBinder` interface.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f70aa-105">To představuje bezpečnostní riziko pro otevření souboru databáze (PDB) programu z nedůvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="f70aa-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f70aa-106">Metody</span><span class="sxs-lookup"><span data-stu-id="f70aa-106">Methods</span></span>  
  
|<span data-ttu-id="f70aa-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="f70aa-107">Method</span></span>|<span data-ttu-id="f70aa-108">Popis</span><span class="sxs-lookup"><span data-stu-id="f70aa-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f70aa-109">GetReaderFromCallback – metoda</span><span class="sxs-lookup"><span data-stu-id="f70aa-109">GetReaderFromCallback Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)|<span data-ttu-id="f70aa-110">Umožňuje uživatelům implementovat nebo zadat buď prostřednictvím zpětného volání `IID_IDiaReadExeAtRVACallback` nebo `IID_IDiaReadExeAtOffsetCallback` získat informace o ladění adresáře z paměti</span><span class="sxs-lookup"><span data-stu-id="f70aa-110">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the Debug directory information from memory</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f70aa-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f70aa-111">Requirements</span></span>  
 <span data-ttu-id="f70aa-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f70aa-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f70aa-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f70aa-113">See also</span></span>
- [<span data-ttu-id="f70aa-114">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="f70aa-114">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="f70aa-115">ISymUnmanagedBinder – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f70aa-115">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
- [<span data-ttu-id="f70aa-116">ISymUnmanagedBinder2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f70aa-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
