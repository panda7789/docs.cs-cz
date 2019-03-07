---
title: AddFile2 – metoda
ms.date: 03/30/2017
api_name:
- AddFile2
- IALink2.AddFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddFile2
helpviewer_keywords:
- AddFile2 method
ms.assetid: 03bc49bf-a89b-4fb6-a88d-97482e061195
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c595f59905a369c206da2fa011038d0d95041fa4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57500678"
---
# <a name="addfile2-method"></a><span data-ttu-id="64792-102">AddFile2 – metoda</span><span class="sxs-lookup"><span data-stu-id="64792-102">AddFile2 Method</span></span>
<span data-ttu-id="64792-103">Přidá soubory do sestavení.</span><span class="sxs-lookup"><span data-stu-id="64792-103">Adds files to the assembly.</span></span> <span data-ttu-id="64792-104">Lze použít také k vytvoření nevázaného moduly.</span><span class="sxs-lookup"><span data-stu-id="64792-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64792-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="64792-105">Syntax</span></span>  
  
```  
HRESULT AddFile2(  
    mdAssembly AssemblyID,  
    LPCWSTR pszFilename,  
    DWORD dwFlags,  
    IMetaDataEmit2* pEmitter,  
    mdFile* pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="64792-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="64792-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="64792-107">ID pro sestavení, do kterého se přidá soubor.</span><span class="sxs-lookup"><span data-stu-id="64792-107">ID for the assembly to which the file is added.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="64792-108">Název souboru, který má být přidána.</span><span class="sxs-lookup"><span data-stu-id="64792-108">Name of the file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="64792-109">COM + `FileDef` označí jako `ffContainsNoMetaData` a `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="64792-109">COM+ `FileDef` flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="64792-110">`dwFlags` je předán [definefile – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="64792-110">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="64792-111">Rozhraní pro [imetadataemit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="64792-111">Interface to [IMetaDataEmit2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interface.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="64792-112">Přijímá ID souboru přidán.</span><span class="sxs-lookup"><span data-stu-id="64792-112">Receives ID for the file being added.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="64792-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="64792-113">Return Value</span></span>  
 <span data-ttu-id="64792-114">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="64792-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64792-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="64792-115">Requirements</span></span>  
 <span data-ttu-id="64792-116">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="64792-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64792-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="64792-117">See also</span></span>
- [<span data-ttu-id="64792-118">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="64792-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="64792-119">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="64792-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="64792-120">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="64792-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
