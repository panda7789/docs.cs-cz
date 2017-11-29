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
ms.openlocfilehash: 61d707cdd827b5e435c961a14e67170ab0e2bc90
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="importtypes2-method"></a><span data-ttu-id="e9e4e-102">ImportTypes2 – metoda</span><span class="sxs-lookup"><span data-stu-id="e9e4e-102">ImportTypes2 Method</span></span>
<span data-ttu-id="e9e4e-103">Zahájí import typy.</span><span class="sxs-lookup"><span data-stu-id="e9e4e-103">Initiates the import of types.</span></span> <span data-ttu-id="e9e4e-104">Voláním této metody lze importovat z každého oboru importovat prostřednictvím typy [importfile – metoda](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="e9e4e-104">Call this method to begin importing types from each scope imported via [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9e4e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9e4e-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="e9e4e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9e4e-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="e9e4e-107">ID sestavení, do kterých se má importovat.</span><span class="sxs-lookup"><span data-stu-id="e9e4e-107">ID of assembly into which to import.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="e9e4e-108">ID souboru ze kterých chcete importovat.</span><span class="sxs-lookup"><span data-stu-id="e9e4e-108">ID of file to from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="e9e4e-109">Počítaný od nuly oboru, ze kterého chcete importovat.</span><span class="sxs-lookup"><span data-stu-id="e9e4e-109">Zero-based scope from which to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="e9e4e-110">Získá popisovač výčtu pro typy v daném oboru.</span><span class="sxs-lookup"><span data-stu-id="e9e4e-110">Receives enumerator handle for the types in the given scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="e9e4e-111">Volitelně obdrží [imetadataimport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e9e4e-111">Optionally receives [IMetaDataImport2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="e9e4e-112">Volitelně přijme počet typů v zadaném oboru.</span><span class="sxs-lookup"><span data-stu-id="e9e4e-112">Optionally receives count of types in the specified scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e9e4e-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e9e4e-113">Return Value</span></span>  
 <span data-ttu-id="e9e4e-114">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="e9e4e-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9e4e-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e9e4e-115">Requirements</span></span>  
 <span data-ttu-id="e9e4e-116">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="e9e4e-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9e4e-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="e9e4e-117">See Also</span></span>  
 [<span data-ttu-id="e9e4e-118">Ialink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e9e4e-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="e9e4e-119">Ialink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e9e4e-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="e9e4e-120">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="e9e4e-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
