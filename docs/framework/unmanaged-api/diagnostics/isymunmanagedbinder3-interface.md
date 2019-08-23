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
ms.openlocfilehash: a6f514cc070a0a38eb09a5387efc8611100765b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944100"
---
# <a name="isymunmanagedbinder3-interface"></a><span data-ttu-id="68139-102">ISymUnmanagedBinder3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="68139-102">ISymUnmanagedBinder3 Interface</span></span>
<span data-ttu-id="68139-103">Rozšiřuje rozhraní pořadače symbolů.</span><span class="sxs-lookup"><span data-stu-id="68139-103">Extends the symbol binder interface.</span></span> <span data-ttu-id="68139-104">Získejte toto rozhraní voláním `QueryInterface` objektu, který `ISymUnmanagedBinder` implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="68139-104">Obtain this interface by calling `QueryInterface` on an object that implements the `ISymUnmanagedBinder` interface.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="68139-105">Je bezpečnostním rizikem k otevření souboru programu databáze (PDB) z nedůvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="68139-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="68139-106">Metody</span><span class="sxs-lookup"><span data-stu-id="68139-106">Methods</span></span>  
  
|<span data-ttu-id="68139-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="68139-107">Method</span></span>|<span data-ttu-id="68139-108">Popis</span><span class="sxs-lookup"><span data-stu-id="68139-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="68139-109">GetReaderFromCallback – metoda</span><span class="sxs-lookup"><span data-stu-id="68139-109">GetReaderFromCallback Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)|<span data-ttu-id="68139-110">Umožňuje uživateli implementovat nebo dodávkovat prostřednictvím zpětného volání `IID_IDiaReadExeAtRVACallback` buď `IID_IDiaReadExeAtOffsetCallback` nebo, aby získal informace adresáře ladění z paměti.</span><span class="sxs-lookup"><span data-stu-id="68139-110">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the Debug directory information from memory</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="68139-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="68139-111">Requirements</span></span>  
 <span data-ttu-id="68139-112">**Hlaviček** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="68139-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68139-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="68139-113">See also</span></span>

- [<span data-ttu-id="68139-114">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="68139-114">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="68139-115">ISymUnmanagedBinder – rozhraní</span><span class="sxs-lookup"><span data-stu-id="68139-115">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
- [<span data-ttu-id="68139-116">ISymUnmanagedBinder2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="68139-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
