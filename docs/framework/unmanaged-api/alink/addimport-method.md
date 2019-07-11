---
title: AddImport – metoda
ms.date: 03/30/2017
api_name:
- AddImport
- IALink.AddImport
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddImport
helpviewer_keywords:
- AddImport method
ms.assetid: 4fedf8a0-08c8-43d0-aa00-20f2a521c991
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 31dec878c92e2e2196ab2d586a78578b7244a41a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742238"
---
# <a name="addimport-method"></a><span data-ttu-id="46597-102">AddImport – metoda</span><span class="sxs-lookup"><span data-stu-id="46597-102">AddImport Method</span></span>
<span data-ttu-id="46597-103">Přidá importy do sestavení.</span><span class="sxs-lookup"><span data-stu-id="46597-103">Adds imports to the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46597-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46597-104">Syntax</span></span>  
  
```cpp  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="46597-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="46597-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="46597-106">Jedinečné ID sestavení potřeba rozšířit.</span><span class="sxs-lookup"><span data-stu-id="46597-106">Unique ID of assembly to be augmented.</span></span>  
  
 `ImportToken`  
 <span data-ttu-id="46597-107">Jedinečné ID získaných [importfile – metoda](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), souboru k importu.</span><span class="sxs-lookup"><span data-stu-id="46597-107">Unique ID, retrieved from [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), of file to be imported.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="46597-108">COM + FileDef označí jako `ffContainsNoMetaData` a `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="46597-108">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="46597-109">`dwFlags` je předán [definefile – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="46597-109">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="46597-110">Ukazatel na token, který přijímá ID pro výsledný soubor.</span><span class="sxs-lookup"><span data-stu-id="46597-110">Pointer to token that receives the ID for the resulting file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="46597-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="46597-111">Return Value</span></span>  
 <span data-ttu-id="46597-112">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="46597-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46597-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="46597-113">Requirements</span></span>  
 <span data-ttu-id="46597-114">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="46597-114">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46597-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="46597-115">See also</span></span>

- [<span data-ttu-id="46597-116">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="46597-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="46597-117">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="46597-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="46597-118">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="46597-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
