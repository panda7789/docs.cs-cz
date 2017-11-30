---
title: "AddFile2 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- AddFile2
- IALink2.AddFile2
api_location: alink.dll
api_type: COM
f1_keywords: AddFile2
helpviewer_keywords: AddFile2 method
ms.assetid: 03bc49bf-a89b-4fb6-a88d-97482e061195
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: fe10a3ca8930087a52d02905534696dbb2d8fb25
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="addfile2-method"></a><span data-ttu-id="edf1f-102">AddFile2 – metoda</span><span class="sxs-lookup"><span data-stu-id="edf1f-102">AddFile2 Method</span></span>
<span data-ttu-id="edf1f-103">Přidá soubory do sestavení.</span><span class="sxs-lookup"><span data-stu-id="edf1f-103">Adds files to the assembly.</span></span> <span data-ttu-id="edf1f-104">Můžete také použít k vytvoření nepřipojeného moduly.</span><span class="sxs-lookup"><span data-stu-id="edf1f-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edf1f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="edf1f-105">Syntax</span></span>  
  
```  
HRESULT AddFile2(  
    mdAssembly AssemblyID,  
    LPCWSTR pszFilename,  
    DWORD dwFlags,  
    IMetaDataEmit2* pEmitter,  
    mdFile* pFileToken  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="edf1f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="edf1f-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="edf1f-107">ID pro sestavení, ke kterému se přidá soubor.</span><span class="sxs-lookup"><span data-stu-id="edf1f-107">ID for the assembly to which the file is added.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="edf1f-108">Název souboru, který se má přidat.</span><span class="sxs-lookup"><span data-stu-id="edf1f-108">Name of the file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="edf1f-109">Modelu COM + `FileDef` flags – například `ffContainsNoMetaData` a `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="edf1f-109">COM+ `FileDef` flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="edf1f-110">`dwFlags`Předaný [definefile – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="edf1f-110">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="edf1f-111">Rozhraní pro [imetadataemit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="edf1f-111">Interface to [IMetaDataEmit2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interface.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="edf1f-112">Získá ID pro soubor, který chcete přidat.</span><span class="sxs-lookup"><span data-stu-id="edf1f-112">Receives ID for the file being added.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="edf1f-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="edf1f-113">Return Value</span></span>  
 <span data-ttu-id="edf1f-114">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="edf1f-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edf1f-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="edf1f-115">Requirements</span></span>  
 <span data-ttu-id="edf1f-116">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="edf1f-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edf1f-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="edf1f-117">See Also</span></span>  
 [<span data-ttu-id="edf1f-118">Ialink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="edf1f-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="edf1f-119">Ialink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="edf1f-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="edf1f-120">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="edf1f-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
