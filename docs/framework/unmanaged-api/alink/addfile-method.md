---
title: AddFile – metoda
ms.date: 03/30/2017
api_name:
- IALink.AddFile
- AddFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddFile
helpviewer_keywords:
- AddFile method
ms.assetid: 9e707abb-f905-4568-9356-12aa21d1b11c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7ff6bde5009e834bfca156fe4d3ad16da53ded85
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742382"
---
# <a name="addfile-method"></a><span data-ttu-id="d944a-102">AddFile – metoda</span><span class="sxs-lookup"><span data-stu-id="d944a-102">AddFile Method</span></span>
<span data-ttu-id="d944a-103">Přidá soubory do sestavení.</span><span class="sxs-lookup"><span data-stu-id="d944a-103">Adds files to the assembly.</span></span> <span data-ttu-id="d944a-104">Lze použít také k vytvoření nevázaného moduly.</span><span class="sxs-lookup"><span data-stu-id="d944a-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d944a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d944a-105">Syntax</span></span>  
  
```cpp  
HRESULT AddFile(  
    mdAssembly      AssemblyID,  
    LPCWSTR         pszFilename,  
    DWORD           dwFlags,  
    IMetaDataEmit*  pEmitter,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="d944a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d944a-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="d944a-107">Jedinečné ID sestavení potřeba rozšířit.</span><span class="sxs-lookup"><span data-stu-id="d944a-107">Unique ID of the assembly to be augmented.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="d944a-108">Plně kvalifikovaný název souboru má být přidána.</span><span class="sxs-lookup"><span data-stu-id="d944a-108">Fully qualified name of file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="d944a-109">COM + FileDef označí jako `ffContainsNoMetaData` a `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="d944a-109">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="d944a-110">`dwFlags` je předán [definefile – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="d944a-110">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="d944a-111">[Imetadataemit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) rozhraní použít ke generování metadat, v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="d944a-111">[IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface to be used to emit metadata, if necessary.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="d944a-112">Ukazatel na kam se má jedinečné ID přidaný soubor uložit.</span><span class="sxs-lookup"><span data-stu-id="d944a-112">Pointer to where the unique ID of the added file will be stored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d944a-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d944a-113">Return Value</span></span>  
 <span data-ttu-id="d944a-114">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="d944a-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d944a-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d944a-115">Requirements</span></span>  
 <span data-ttu-id="d944a-116">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="d944a-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d944a-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d944a-117">See also</span></span>

- [<span data-ttu-id="d944a-118">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d944a-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="d944a-119">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d944a-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="d944a-120">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="d944a-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
