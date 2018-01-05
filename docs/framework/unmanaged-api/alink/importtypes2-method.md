---
title: "ImportTypes2 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.ImportTypes2
api_location: alink.dll
api_type: COM
f1_keywords: ImportTypes2
helpviewer_keywords: ImportTypes2 method
ms.assetid: 32f3ba58-9695-41e9-ba58-fd19e45ed396
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 47c49253a1e2839939ef4e671f155e4a44d07529
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="importtypes2-method"></a><span data-ttu-id="a4a7c-102">ImportTypes2 – metoda</span><span class="sxs-lookup"><span data-stu-id="a4a7c-102">ImportTypes2 Method</span></span>
<span data-ttu-id="a4a7c-103">Zahájí import typy.</span><span class="sxs-lookup"><span data-stu-id="a4a7c-103">Initiates the import of types.</span></span> <span data-ttu-id="a4a7c-104">Voláním této metody lze importovat z každého oboru importovat prostřednictvím typy [importfile – metoda](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="a4a7c-104">Call this method to begin importing types from each scope imported via [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4a7c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4a7c-105">Syntax</span></span>  
  
```  
HRESULT ImportTypes2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport2** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a4a7c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a4a7c-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="a4a7c-107">ID sestavení, do kterých se má importovat.</span><span class="sxs-lookup"><span data-stu-id="a4a7c-107">ID of assembly into which to import.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="a4a7c-108">ID souboru ze kterých chcete importovat.</span><span class="sxs-lookup"><span data-stu-id="a4a7c-108">ID of file to from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="a4a7c-109">Počítaný od nuly oboru, ze kterého chcete importovat.</span><span class="sxs-lookup"><span data-stu-id="a4a7c-109">Zero-based scope from which to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="a4a7c-110">Získá popisovač výčtu pro typy v daném oboru.</span><span class="sxs-lookup"><span data-stu-id="a4a7c-110">Receives enumerator handle for the types in the given scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="a4a7c-111">Volitelně obdrží [imetadataimport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a4a7c-111">Optionally receives [IMetaDataImport2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="a4a7c-112">Volitelně přijme počet typů v zadaném oboru.</span><span class="sxs-lookup"><span data-stu-id="a4a7c-112">Optionally receives count of types in the specified scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a4a7c-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a4a7c-113">Return Value</span></span>  
 <span data-ttu-id="a4a7c-114">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="a4a7c-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4a7c-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a4a7c-115">Requirements</span></span>  
 <span data-ttu-id="a4a7c-116">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="a4a7c-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4a7c-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="a4a7c-117">See Also</span></span>  
 [<span data-ttu-id="a4a7c-118">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a4a7c-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="a4a7c-119">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a4a7c-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="a4a7c-120">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="a4a7c-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
