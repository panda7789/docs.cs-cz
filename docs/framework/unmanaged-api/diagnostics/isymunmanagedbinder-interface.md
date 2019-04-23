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
ms.openlocfilehash: b6d91f68ac737ce28cdbef926119bb3711bc1096
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59105807"
---
# <a name="isymunmanagedbinder-interface"></a><span data-ttu-id="d53a6-102">ISymUnmanagedBinder – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d53a6-102">ISymUnmanagedBinder Interface</span></span>
<span data-ttu-id="d53a6-103">Představuje vazač symbolů pro nespravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="d53a6-103">Represents a symbol binder for unmanaged code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d53a6-104">To představuje bezpečnostní riziko pro otevření souboru databáze (PDB) programu z nedůvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="d53a6-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d53a6-105">Metody</span><span class="sxs-lookup"><span data-stu-id="d53a6-105">Methods</span></span>  
  
|<span data-ttu-id="d53a6-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="d53a6-106">Method</span></span>|<span data-ttu-id="d53a6-107">Popis</span><span class="sxs-lookup"><span data-stu-id="d53a6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d53a6-108">GetReaderForFile – metoda</span><span class="sxs-lookup"><span data-stu-id="d53a6-108">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)|<span data-ttu-id="d53a6-109">Rozhraní metadat a název souboru, vrátí správné [isymunmanagedreader –](isymunmanagedreader-interface.md) struktura, která načte symboly pro ladění související s modulem.</span><span class="sxs-lookup"><span data-stu-id="d53a6-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols associated with the module.</span></span>|  
|[<span data-ttu-id="d53a6-110">GetReaderFromStream – metoda</span><span class="sxs-lookup"><span data-stu-id="d53a6-110">GetReaderFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderfromstream-method.md)|<span data-ttu-id="d53a6-111">Rozhraní metadat a datový proud, který obsahuje úložiště symbolů, vrátí správné [isymunmanagedreader –](isymunmanagedreader-interface.md) struktura, která bude číst ladění symboly z úložiště daného symbolu.</span><span class="sxs-lookup"><span data-stu-id="d53a6-111">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d53a6-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d53a6-112">Requirements</span></span>  
 <span data-ttu-id="d53a6-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d53a6-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d53a6-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d53a6-114">See also</span></span>

- [<span data-ttu-id="d53a6-115">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="d53a6-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="d53a6-116">ISymUnmanagedBinder2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d53a6-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
- [<span data-ttu-id="d53a6-117">ISymUnmanagedBinder3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d53a6-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
