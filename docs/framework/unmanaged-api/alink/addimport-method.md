---
title: "Addimport – Method1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- AddImport
- IALink.AddImport
api_location: alink.dll
api_type: COM
f1_keywords: AddImport
helpviewer_keywords: AddImport method
ms.assetid: 4fedf8a0-08c8-43d0-aa00-20f2a521c991
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4d8827821deaeda311a42855737ecf53ab635a02
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="addimport-method1"></a><span data-ttu-id="c3d04-102">Addimport – Method1</span><span class="sxs-lookup"><span data-stu-id="c3d04-102">AddImport Method1</span></span>
<span data-ttu-id="c3d04-103">Přidá importy sestavení.</span><span class="sxs-lookup"><span data-stu-id="c3d04-103">Adds imports to the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3d04-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3d04-104">Syntax</span></span>  
  
```  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c3d04-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c3d04-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="c3d04-106">Jedinečné ID sestavení, které má být rozšířen.</span><span class="sxs-lookup"><span data-stu-id="c3d04-106">Unique ID of assembly to be augmented.</span></span>  
  
 `ImportToken`  
 <span data-ttu-id="c3d04-107">Jedinečné ID načítají [importfile – metoda](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), souboru určených k importu.</span><span class="sxs-lookup"><span data-stu-id="c3d04-107">Unique ID, retrieved from [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), of file to be imported.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="c3d04-108">Modelu COM + FileDef flags – například `ffContainsNoMetaData` a `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="c3d04-108">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="c3d04-109">`dwFlags`Předaný [definefile – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="c3d04-109">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="c3d04-110">Ukazatel na token, který přijímá ID pro výsledný soubor.</span><span class="sxs-lookup"><span data-stu-id="c3d04-110">Pointer to token that receives the ID for the resulting file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c3d04-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c3d04-111">Return Value</span></span>  
 <span data-ttu-id="c3d04-112">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="c3d04-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3d04-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c3d04-113">Requirements</span></span>  
 <span data-ttu-id="c3d04-114">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="c3d04-114">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3d04-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="c3d04-115">See Also</span></span>  
 [<span data-ttu-id="c3d04-116">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c3d04-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="c3d04-117">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c3d04-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="c3d04-118">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="c3d04-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
