---
title: "ISymUnmanagedBinder – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedBinder
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedBinder
helpviewer_keywords: ISymUnmanagedBinder interface [.NET Framework debugging]
ms.assetid: b22fbe19-b30f-4696-8175-e6b91da9edab
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 00b0b5ee330a606ae7417185a804f3d37ab6664a
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2017
---
# <a name="isymunmanagedbinder-interface"></a><span data-ttu-id="e2c6e-102">ISymUnmanagedBinder – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e2c6e-102">ISymUnmanagedBinder Interface</span></span>
<span data-ttu-id="e2c6e-103">Představuje vazač symbol pro nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="e2c6e-103">Represents a symbol binder for unmanaged code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e2c6e-104">Je bezpečnostní riziko pro otevření souboru databáze (PDB) program z nedůvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="e2c6e-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e2c6e-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e2c6e-105">Methods</span></span>  
  
|<span data-ttu-id="e2c6e-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="e2c6e-106">Method</span></span>|<span data-ttu-id="e2c6e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e2c6e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e2c6e-108">Getreaderforfile – metoda</span><span class="sxs-lookup"><span data-stu-id="e2c6e-108">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)|<span data-ttu-id="e2c6e-109">Vrátí zadaný metadat rozhraní a název souboru správný [ISymUnmanagedReader](isymunmanagedreader-interface.md) struktura, která budou číst související s modulem symboly pro ladění.</span><span class="sxs-lookup"><span data-stu-id="e2c6e-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols associated with the module.</span></span>|  
|[<span data-ttu-id="e2c6e-110">Getreaderfromstream – metoda</span><span class="sxs-lookup"><span data-stu-id="e2c6e-110">GetReaderFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderfromstream-method.md)|<span data-ttu-id="e2c6e-111">Zadaný datový proud, který obsahuje úložiště symbolů a metadat rozhraní, vrátí správné [ISymUnmanagedReader](isymunmanagedreader-interface.md) struktura, která budou číst ladění symboly z obchodu daný symbol.</span><span class="sxs-lookup"><span data-stu-id="e2c6e-111">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e2c6e-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e2c6e-112">Requirements</span></span>  
 <span data-ttu-id="e2c6e-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e2c6e-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2c6e-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="e2c6e-114">See Also</span></span>  
 [<span data-ttu-id="e2c6e-115">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="e2c6e-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="e2c6e-116">Isymunmanagedbinder2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e2c6e-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 [<span data-ttu-id="e2c6e-117">Isymunmanagedbinder3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e2c6e-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
