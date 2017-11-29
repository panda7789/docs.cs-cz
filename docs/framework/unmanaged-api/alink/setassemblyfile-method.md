---
title: "SetAssemblyFile – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.SetAssemblyFile
api_location: alink.dll
api_type: COM
f1_keywords: SetAssemblyFile
helpviewer_keywords: SetAssemblyFile method
ms.assetid: 3a912787-f139-43ca-a841-8bbda3107ecf
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d83062db41b5fa1485555de40be0a39a65e0459a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="setassemblyfile-method"></a><span data-ttu-id="8341d-102">SetAssemblyFile – metoda</span><span class="sxs-lookup"><span data-stu-id="8341d-102">SetAssemblyFile Method</span></span>
<span data-ttu-id="8341d-103">Přiřadí název sestavení, která má být sestaven.</span><span class="sxs-lookup"><span data-stu-id="8341d-103">Assigns the name of the assembly to be built.</span></span> <span data-ttu-id="8341d-104">Není pro použití při vytváření nevázaných moduly.</span><span class="sxs-lookup"><span data-stu-id="8341d-104">Not for use when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8341d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8341d-105">Syntax</span></span>  
  
```  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8341d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8341d-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="8341d-107">Plně kvalifikovaný název souboru manifestu.</span><span class="sxs-lookup"><span data-stu-id="8341d-107">Fully qualified name of the manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="8341d-108">Ukazatel na [imetadataemit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8341d-108">Pointer to [IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="8341d-109">Flags – jak jsou definovány v [AssemblyFlags – výčet](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="8341d-109">Flags as defined in [AssemblyFlags Enumeration](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="8341d-110">Ukazatel na ID výsledné sestavení.</span><span class="sxs-lookup"><span data-stu-id="8341d-110">Pointer to ID of resulting assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8341d-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8341d-111">Return Value</span></span>  
 <span data-ttu-id="8341d-112">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="8341d-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8341d-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8341d-113">Requirements</span></span>  
 <span data-ttu-id="8341d-114">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="8341d-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8341d-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="8341d-115">See Also</span></span>  
 [<span data-ttu-id="8341d-116">Ialink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8341d-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="8341d-117">Ialink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8341d-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="8341d-118">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="8341d-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
