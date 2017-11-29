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
ms.openlocfilehash: 5061ce28c4a09f445267c99420bf1942d99076bf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedbinder-interface"></a><span data-ttu-id="5e80a-102">ISymUnmanagedBinder – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5e80a-102">ISymUnmanagedBinder Interface</span></span>
<span data-ttu-id="5e80a-103">Představuje vazač symbol pro nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="5e80a-103">Represents a symbol binder for unmanaged code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5e80a-104">Je bezpečnostní riziko pro otevření souboru databáze (PDB) program z nedůvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="5e80a-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5e80a-105">Metody</span><span class="sxs-lookup"><span data-stu-id="5e80a-105">Methods</span></span>  
  
|<span data-ttu-id="5e80a-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="5e80a-106">Method</span></span>|<span data-ttu-id="5e80a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="5e80a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5e80a-108">Getreaderforfile – metoda</span><span class="sxs-lookup"><span data-stu-id="5e80a-108">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)|<span data-ttu-id="5e80a-109">Vrátí zadaný metadat rozhraní a název souboru správný <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> Struktura, která budou číst související s modulem symboly pro ladění.</span><span class="sxs-lookup"><span data-stu-id="5e80a-109">Given a metadata interface and a file name, returns the correct <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> structure that will read the debugging symbols associated with the module.</span></span>|  
|[<span data-ttu-id="5e80a-110">Getreaderfromstream – metoda</span><span class="sxs-lookup"><span data-stu-id="5e80a-110">GetReaderFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderfromstream-method.md)|<span data-ttu-id="5e80a-111">Zadaný datový proud, který obsahuje úložiště symbolů a metadat rozhraní, vrátí správné <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> Struktura, která budou číst ladění symboly z obchodu daný symbol.</span><span class="sxs-lookup"><span data-stu-id="5e80a-111">Given a metadata interface and a stream that contains the symbol store, returns the correct <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> structure that will read the debugging symbols from the given symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5e80a-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5e80a-112">Requirements</span></span>  
 <span data-ttu-id="5e80a-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5e80a-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e80a-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="5e80a-114">See Also</span></span>  
 [<span data-ttu-id="5e80a-115">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="5e80a-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="5e80a-116">Isymunmanagedbinder2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5e80a-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 [<span data-ttu-id="5e80a-117">Isymunmanagedbinder3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5e80a-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
