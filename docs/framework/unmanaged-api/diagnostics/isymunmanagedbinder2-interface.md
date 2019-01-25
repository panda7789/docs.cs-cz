---
title: ISymUnmanagedBinder2 – rozhraní
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder2 Interface
helpviewer_keywords:
- ISymUnmanagedBinder2 interface [.NET Framework debugging]
ms.assetid: 7a59f405-73e8-4434-8bcc-a9dc45ea08e6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 49949989a48be13bcb70b27e47407d907b284670
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54494951"
---
# <a name="isymunmanagedbinder2-interface"></a><span data-ttu-id="a34bc-102">ISymUnmanagedBinder2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a34bc-102">ISymUnmanagedBinder2 Interface</span></span>
<span data-ttu-id="a34bc-103">Představuje vazač symbolů pro nespravovaný kód a rozšiřuje [isymunmanagedbinder –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a34bc-103">Represents a symbol binder for unmanaged code, and extends the [ISymUnmanagedBinder](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md) interface.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a34bc-104">To představuje bezpečnostní riziko pro otevření souboru databáze (PDB) programu z nedůvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="a34bc-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a34bc-105">Metody</span><span class="sxs-lookup"><span data-stu-id="a34bc-105">Methods</span></span>  
  
|<span data-ttu-id="a34bc-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="a34bc-106">Method</span></span>|<span data-ttu-id="a34bc-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a34bc-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a34bc-108">GetReaderForFile2 – metoda</span><span class="sxs-lookup"><span data-stu-id="a34bc-108">GetReaderForFile2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)|<span data-ttu-id="a34bc-109">Rozhraní metadat a název souboru, vrátí správné [isymunmanagedreader –](isymunmanagedreader-interface.md) rozhraní, které budou číst symboly ladění, které jsou spojené s modulem.</span><span class="sxs-lookup"><span data-stu-id="a34bc-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span> <span data-ttu-id="a34bc-110">Poskytuje rozsáhlejší vyhledávání, než [isymunmanagedbinder::getreaderforfile –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="a34bc-110">Provides a more extensive search than the [ISymUnmanagedBinder::GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a34bc-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a34bc-111">Requirements</span></span>  
 <span data-ttu-id="a34bc-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a34bc-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a34bc-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a34bc-113">See also</span></span>
- [<span data-ttu-id="a34bc-114">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="a34bc-114">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="a34bc-115">ISymUnmanagedBinder – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a34bc-115">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
- [<span data-ttu-id="a34bc-116">ISymUnmanagedBinder3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a34bc-116">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
