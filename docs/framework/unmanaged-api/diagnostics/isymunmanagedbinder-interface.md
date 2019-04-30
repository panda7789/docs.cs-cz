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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940059"
---
# <a name="isymunmanagedbinder-interface"></a><span data-ttu-id="8f93a-102">ISymUnmanagedBinder – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8f93a-102">ISymUnmanagedBinder Interface</span></span>
<span data-ttu-id="8f93a-103">Představuje vazač symbolů pro nespravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="8f93a-103">Represents a symbol binder for unmanaged code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8f93a-104">To představuje bezpečnostní riziko pro otevření souboru databáze (PDB) programu z nedůvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="8f93a-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8f93a-105">Metody</span><span class="sxs-lookup"><span data-stu-id="8f93a-105">Methods</span></span>  
  
|<span data-ttu-id="8f93a-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="8f93a-106">Method</span></span>|<span data-ttu-id="8f93a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8f93a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8f93a-108">GetReaderForFile – metoda</span><span class="sxs-lookup"><span data-stu-id="8f93a-108">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)|<span data-ttu-id="8f93a-109">Rozhraní metadat a název souboru, vrátí správné [isymunmanagedreader –](isymunmanagedreader-interface.md) struktura, která načte symboly pro ladění související s modulem.</span><span class="sxs-lookup"><span data-stu-id="8f93a-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols associated with the module.</span></span>|  
|[<span data-ttu-id="8f93a-110">GetReaderFromStream – metoda</span><span class="sxs-lookup"><span data-stu-id="8f93a-110">GetReaderFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderfromstream-method.md)|<span data-ttu-id="8f93a-111">Rozhraní metadat a datový proud, který obsahuje úložiště symbolů, vrátí správné [isymunmanagedreader –](isymunmanagedreader-interface.md) struktura, která bude číst ladění symboly z úložiště daného symbolu.</span><span class="sxs-lookup"><span data-stu-id="8f93a-111">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8f93a-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8f93a-112">Requirements</span></span>  
 <span data-ttu-id="8f93a-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8f93a-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f93a-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8f93a-114">See also</span></span>

- [<span data-ttu-id="8f93a-115">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="8f93a-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="8f93a-116">ISymUnmanagedBinder2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8f93a-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
- [<span data-ttu-id="8f93a-117">ISymUnmanagedBinder3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8f93a-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
