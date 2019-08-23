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
ms.openlocfilehash: e2160ad4174d9cdfe6e27d2ba7f4748bd473a5f9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944235"
---
# <a name="isymunmanagedbinder-interface"></a><span data-ttu-id="f547e-102">ISymUnmanagedBinder – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f547e-102">ISymUnmanagedBinder Interface</span></span>
<span data-ttu-id="f547e-103">Představuje pořadač symbolů pro nespravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="f547e-103">Represents a symbol binder for unmanaged code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f547e-104">Je bezpečnostním rizikem k otevření souboru programu databáze (PDB) z nedůvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="f547e-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f547e-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f547e-105">Methods</span></span>  
  
|<span data-ttu-id="f547e-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="f547e-106">Method</span></span>|<span data-ttu-id="f547e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f547e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f547e-108">GetReaderForFile – metoda</span><span class="sxs-lookup"><span data-stu-id="f547e-108">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)|<span data-ttu-id="f547e-109">Vzhledem k rozhraní metadat a názvu souboru vrátí správnou strukturu [ISymUnmanagedReader](isymunmanagedreader-interface.md) , která načte symboly ladění přidružené k modulu.</span><span class="sxs-lookup"><span data-stu-id="f547e-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols associated with the module.</span></span>|  
|[<span data-ttu-id="f547e-110">GetReaderFromStream – metoda</span><span class="sxs-lookup"><span data-stu-id="f547e-110">GetReaderFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderfromstream-method.md)|<span data-ttu-id="f547e-111">Vzhledem k rozhraní metadat a datovému proudu, který obsahuje úložiště symbolů, vrátí správnou strukturu [ISymUnmanagedReader](isymunmanagedreader-interface.md) , která načte symboly ladění z daného úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="f547e-111">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f547e-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f547e-112">Requirements</span></span>  
 <span data-ttu-id="f547e-113">**Hlaviček** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f547e-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f547e-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f547e-114">See also</span></span>

- [<span data-ttu-id="f547e-115">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="f547e-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="f547e-116">ISymUnmanagedBinder2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f547e-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
- [<span data-ttu-id="f547e-117">ISymUnmanagedBinder3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f547e-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
