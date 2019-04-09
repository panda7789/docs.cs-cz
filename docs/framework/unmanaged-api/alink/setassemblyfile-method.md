---
title: SetAssemblyFile – metoda
ms.date: 03/30/2017
api_name:
- IALink.SetAssemblyFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile
helpviewer_keywords:
- SetAssemblyFile method
ms.assetid: 3a912787-f139-43ca-a841-8bbda3107ecf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a19762cbec91871d7af617957896e4ee34944fba
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132705"
---
# <a name="setassemblyfile-method"></a><span data-ttu-id="aaf3f-102">SetAssemblyFile – metoda</span><span class="sxs-lookup"><span data-stu-id="aaf3f-102">SetAssemblyFile Method</span></span>
<span data-ttu-id="aaf3f-103">Přiřadí název sestavení, které má být sestaven.</span><span class="sxs-lookup"><span data-stu-id="aaf3f-103">Assigns the name of the assembly to be built.</span></span> <span data-ttu-id="aaf3f-104">Není pro použití při vytváření nevázaných moduly.</span><span class="sxs-lookup"><span data-stu-id="aaf3f-104">Not for use when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aaf3f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aaf3f-105">Syntax</span></span>  
  
```  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="aaf3f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="aaf3f-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="aaf3f-107">Plně kvalifikovaný název souboru manifestu.</span><span class="sxs-lookup"><span data-stu-id="aaf3f-107">Fully qualified name of the manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="aaf3f-108">Ukazatel na [imetadataemit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="aaf3f-108">Pointer to [IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="aaf3f-109">Označí příznakem, jak jsou definovány v [assemblyflags – výčet](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="aaf3f-109">Flags as defined in [AssemblyFlags Enumeration](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="aaf3f-110">Ukazatel na ID výsledné sestavení.</span><span class="sxs-lookup"><span data-stu-id="aaf3f-110">Pointer to ID of resulting assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aaf3f-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="aaf3f-111">Return Value</span></span>  
 <span data-ttu-id="aaf3f-112">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="aaf3f-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aaf3f-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aaf3f-113">Requirements</span></span>  
 <span data-ttu-id="aaf3f-114">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="aaf3f-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaf3f-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aaf3f-115">See also</span></span>

- [<span data-ttu-id="aaf3f-116">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aaf3f-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="aaf3f-117">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aaf3f-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="aaf3f-118">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="aaf3f-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
