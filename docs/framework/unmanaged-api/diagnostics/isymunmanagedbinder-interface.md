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
ms.openlocfilehash: f23df98abc5355f0b25d7253b5f2ae808b3446a1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449368"
---
# <a name="isymunmanagedbinder-interface"></a><span data-ttu-id="5778c-102">ISymUnmanagedBinder – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5778c-102">ISymUnmanagedBinder Interface</span></span>
<span data-ttu-id="5778c-103">Představuje pořadač symbolů pro nespravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="5778c-103">Represents a symbol binder for unmanaged code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5778c-104">Je bezpečnostním rizikem k otevření souboru programu databáze (PDB) z nedůvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="5778c-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5778c-105">Metody</span><span class="sxs-lookup"><span data-stu-id="5778c-105">Methods</span></span>  
  
|<span data-ttu-id="5778c-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="5778c-106">Method</span></span>|<span data-ttu-id="5778c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="5778c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5778c-108">GetReaderForFile – metoda</span><span class="sxs-lookup"><span data-stu-id="5778c-108">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)|<span data-ttu-id="5778c-109">Vzhledem k rozhraní metadat a názvu souboru vrátí správnou strukturu [ISymUnmanagedReader](isymunmanagedreader-interface.md) , která načte symboly ladění přidružené k modulu.</span><span class="sxs-lookup"><span data-stu-id="5778c-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols associated with the module.</span></span>|  
|[<span data-ttu-id="5778c-110">GetReaderFromStream – metoda</span><span class="sxs-lookup"><span data-stu-id="5778c-110">GetReaderFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderfromstream-method.md)|<span data-ttu-id="5778c-111">Vzhledem k rozhraní metadat a datovému proudu, který obsahuje úložiště symbolů, vrátí správnou strukturu [ISymUnmanagedReader](isymunmanagedreader-interface.md) , která načte symboly ladění z daného úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="5778c-111">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5778c-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5778c-112">Requirements</span></span>  
 <span data-ttu-id="5778c-113">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="5778c-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5778c-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5778c-114">See also</span></span>

- [<span data-ttu-id="5778c-115">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="5778c-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="5778c-116">ISymUnmanagedBinder2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5778c-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
- [<span data-ttu-id="5778c-117">ISymUnmanagedBinder3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5778c-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
