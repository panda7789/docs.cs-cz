---
title: "SetAssemblyFile2 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.SetAssemblyFile2
api_location: alink.dll
api_type: COM
f1_keywords: SetAssemblyFile2
helpviewer_keywords: SetAssemblyFile2 method
ms.assetid: eedb9125-1ef1-4000-abfc-7de86e5a1f17
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7363a8f633d5f447f72e27ba03055f589564bdd2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="setassemblyfile2-method"></a><span data-ttu-id="b4a6c-102">SetAssemblyFile2 – metoda</span><span class="sxs-lookup"><span data-stu-id="b4a6c-102">SetAssemblyFile2 Method</span></span>
<span data-ttu-id="b4a6c-103">Nastaví název a možnosti pro nové sestavení.</span><span class="sxs-lookup"><span data-stu-id="b4a6c-103">Sets the name of and options for a new assembly.</span></span> <span data-ttu-id="b4a6c-104">Tato metoda není volána při vytvoření nepřipojeného moduly.</span><span class="sxs-lookup"><span data-stu-id="b4a6c-104">Do not call this method when you produce unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4a6c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4a6c-105">Syntax</span></span>  
  
```  
HRESULT SetAssemblyFile2(  
    LPCWSTR pszFilename,  
    IMetaDataEmit2* pEmitter,  
    AssemblyFlags   afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b4a6c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b4a6c-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="b4a6c-107">Název souboru manifestu.</span><span class="sxs-lookup"><span data-stu-id="b4a6c-107">Name of manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="b4a6c-108">[Imetadataemit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) rozhraní pro tento soubor.</span><span class="sxs-lookup"><span data-stu-id="b4a6c-108">[IMetaDataEmit2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interface for this file.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="b4a6c-109">Možnosti reprezentována [AssemblyFlags – výčet](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="b4a6c-109">Options represented by [AssemblyFlags Enumeration](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="b4a6c-110">Získá jedinečné ID pro sestavení vytvářen.</span><span class="sxs-lookup"><span data-stu-id="b4a6c-110">Receives unique ID for the assembly being constructed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b4a6c-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b4a6c-111">Return Value</span></span>  
 <span data-ttu-id="b4a6c-112">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="b4a6c-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4a6c-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b4a6c-113">Requirements</span></span>  
 <span data-ttu-id="b4a6c-114">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="b4a6c-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4a6c-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="b4a6c-115">See Also</span></span>  
 [<span data-ttu-id="b4a6c-116">Ialink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b4a6c-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="b4a6c-117">Ialink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b4a6c-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="b4a6c-118">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="b4a6c-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
