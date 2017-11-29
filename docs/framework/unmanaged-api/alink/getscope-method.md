---
title: "Getscope – Method1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.GetScope
api_location: alink.dll
api_type: COM
f1_keywords: GetScope
helpviewer_keywords: GetScope method
ms.assetid: e1555328-2c71-4ece-b357-9eb6d3a8efc4
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b3ebcb90142cc70a2d246d2e9ea6c42babe83b18
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="getscope-method1"></a><span data-ttu-id="f15fe-102">Getscope – Method1</span><span class="sxs-lookup"><span data-stu-id="f15fe-102">GetScope Method1</span></span>
<span data-ttu-id="f15fe-103">Získá obor importu.</span><span class="sxs-lookup"><span data-stu-id="f15fe-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f15fe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f15fe-104">Syntax</span></span>  
  
```  
HRESULT GetScope(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport** ppImportScope  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f15fe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f15fe-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="f15fe-106">Jedinečné ID sestavení import do.</span><span class="sxs-lookup"><span data-stu-id="f15fe-106">Unique ID of assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="f15fe-107">Jedinečné ID souboru pro import z.</span><span class="sxs-lookup"><span data-stu-id="f15fe-107">Unique ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="f15fe-108">Počítaný od nuly oboru pro import.</span><span class="sxs-lookup"><span data-stu-id="f15fe-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="f15fe-109">Obdrží [imetadataimport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) rozhraní pro obor.</span><span class="sxs-lookup"><span data-stu-id="f15fe-109">Receives [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface for the scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f15fe-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f15fe-110">Return Value</span></span>  
 <span data-ttu-id="f15fe-111">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="f15fe-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f15fe-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f15fe-112">Requirements</span></span>  
 <span data-ttu-id="f15fe-113">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="f15fe-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f15fe-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="f15fe-114">See Also</span></span>  
 [<span data-ttu-id="f15fe-115">Ialink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f15fe-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="f15fe-116">Ialink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f15fe-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="f15fe-117">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="f15fe-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
