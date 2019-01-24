---
title: ISymUnmanagedBinder – rozhraní
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder
helpviewer_keywords:
- ISymUnmanagedBinder interface [.NET Framework debugging]
ms.assetid: b22fbe19-b30f-4696-8175-e6b91da9edab
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e149f121de8c965c2215f58dba1a485feebd32ef
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643621"
---
# <a name="isymunmanagedbinder-interface"></a><span data-ttu-id="cabb2-102">ISymUnmanagedBinder – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cabb2-102">ISymUnmanagedBinder Interface</span></span>
<span data-ttu-id="cabb2-103">Představuje vazač symbolů pro nespravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="cabb2-103">Represents a symbol binder for unmanaged code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cabb2-104">To představuje bezpečnostní riziko pro otevření souboru databáze (PDB) programu z nedůvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="cabb2-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cabb2-105">Metody</span><span class="sxs-lookup"><span data-stu-id="cabb2-105">Methods</span></span>  
  
|<span data-ttu-id="cabb2-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="cabb2-106">Method</span></span>|<span data-ttu-id="cabb2-107">Popis</span><span class="sxs-lookup"><span data-stu-id="cabb2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cabb2-108">GetReaderForFile – metoda</span><span class="sxs-lookup"><span data-stu-id="cabb2-108">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)|<span data-ttu-id="cabb2-109">Rozhraní metadat a název souboru, vrátí správné [isymunmanagedreader –](isymunmanagedreader-interface.md) struktura, která načte symboly pro ladění související s modulem.</span><span class="sxs-lookup"><span data-stu-id="cabb2-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols associated with the module.</span></span>|  
|[<span data-ttu-id="cabb2-110">GetReaderFromStream – metoda</span><span class="sxs-lookup"><span data-stu-id="cabb2-110">GetReaderFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderfromstream-method.md)|<span data-ttu-id="cabb2-111">Rozhraní metadat a datový proud, který obsahuje úložiště symbolů, vrátí správné [isymunmanagedreader –](isymunmanagedreader-interface.md) struktura, která bude číst ladění symboly z úložiště daného symbolu.</span><span class="sxs-lookup"><span data-stu-id="cabb2-111">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cabb2-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cabb2-112">Requirements</span></span>  
 <span data-ttu-id="cabb2-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="cabb2-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cabb2-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cabb2-114">See also</span></span>
- [<span data-ttu-id="cabb2-115">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="cabb2-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="cabb2-116">ISymUnmanagedBinder2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cabb2-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
- [<span data-ttu-id="cabb2-117">ISymUnmanagedBinder3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cabb2-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
