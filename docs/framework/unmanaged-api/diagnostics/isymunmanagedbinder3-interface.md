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
ms.openlocfilehash: fdfd8e8fc419809a3a490639ada1c533f286fe8b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939994"
---
# <a name="isymunmanagedbinder3-interface"></a><span data-ttu-id="1a879-102">ISymUnmanagedBinder3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1a879-102">ISymUnmanagedBinder3 Interface</span></span>
<span data-ttu-id="1a879-103">Rozšiřuje rozhraní symbol vazače.</span><span class="sxs-lookup"><span data-stu-id="1a879-103">Extends the symbol binder interface.</span></span> <span data-ttu-id="1a879-104">Získat po zavolání tohoto rozhraní `QueryInterface` na objekt, který implementuje `ISymUnmanagedBinder` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1a879-104">Obtain this interface by calling `QueryInterface` on an object that implements the `ISymUnmanagedBinder` interface.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1a879-105">To představuje bezpečnostní riziko pro otevření souboru databáze (PDB) programu z nedůvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="1a879-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1a879-106">Metody</span><span class="sxs-lookup"><span data-stu-id="1a879-106">Methods</span></span>  
  
|<span data-ttu-id="1a879-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="1a879-107">Method</span></span>|<span data-ttu-id="1a879-108">Popis</span><span class="sxs-lookup"><span data-stu-id="1a879-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1a879-109">GetReaderFromCallback – metoda</span><span class="sxs-lookup"><span data-stu-id="1a879-109">GetReaderFromCallback Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)|<span data-ttu-id="1a879-110">Umožňuje uživatelům implementovat nebo zadat buď prostřednictvím zpětného volání `IID_IDiaReadExeAtRVACallback` nebo `IID_IDiaReadExeAtOffsetCallback` získat informace o ladění adresáře z paměti</span><span class="sxs-lookup"><span data-stu-id="1a879-110">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the Debug directory information from memory</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1a879-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1a879-111">Requirements</span></span>  
 <span data-ttu-id="1a879-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1a879-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a879-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1a879-113">See also</span></span>

- [<span data-ttu-id="1a879-114">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="1a879-114">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="1a879-115">ISymUnmanagedBinder – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1a879-115">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
- [<span data-ttu-id="1a879-116">ISymUnmanagedBinder2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1a879-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
