---
title: "ISymUnmanagedBinder2 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedBinder2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedBinder2 Interface
helpviewer_keywords: ISymUnmanagedBinder2 interface [.NET Framework debugging]
ms.assetid: 7a59f405-73e8-4434-8bcc-a9dc45ea08e6
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0fff140f6848b91e811ef4546a3e8fd50eb61e05
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedbinder2-interface"></a><span data-ttu-id="c300b-102">ISymUnmanagedBinder2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c300b-102">ISymUnmanagedBinder2 Interface</span></span>
<span data-ttu-id="c300b-103">Představuje vazač symbol pro nespravovaného kódu a rozšiřuje [isymunmanagedbinder –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c300b-103">Represents a symbol binder for unmanaged code, and extends the [ISymUnmanagedBinder](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md) interface.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c300b-104">Je bezpečnostní riziko pro otevření souboru databáze (PDB) program z nedůvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="c300b-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c300b-105">Metody</span><span class="sxs-lookup"><span data-stu-id="c300b-105">Methods</span></span>  
  
|<span data-ttu-id="c300b-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="c300b-106">Method</span></span>|<span data-ttu-id="c300b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c300b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c300b-108">GetReaderForFile2 – metoda</span><span class="sxs-lookup"><span data-stu-id="c300b-108">GetReaderForFile2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)|<span data-ttu-id="c300b-109">Vrátí zadaný metadat rozhraní a název souboru správný <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> rozhraní, které budou číst související s modulem symboly pro ladění.</span><span class="sxs-lookup"><span data-stu-id="c300b-109">Given a metadata interface and a file name, returns the correct <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interface that will read the debugging symbols associated with the module.</span></span> <span data-ttu-id="c300b-110">Poskytuje rozšířené hledání než [isymunmanagedbinder::getreaderforfile –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="c300b-110">Provides a more extensive search than the [ISymUnmanagedBinder::GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c300b-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c300b-111">Requirements</span></span>  
 <span data-ttu-id="c300b-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c300b-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c300b-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="c300b-113">See Also</span></span>  
 [<span data-ttu-id="c300b-114">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="c300b-114">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="c300b-115">ISymUnmanagedBinder – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c300b-115">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 [<span data-ttu-id="c300b-116">ISymUnmanagedBinder3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c300b-116">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
