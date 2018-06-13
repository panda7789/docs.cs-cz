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
ms.openlocfilehash: 1e557cc0da7bc684843ae3969242ffb84d811c44
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405343"
---
# <a name="setassemblyfile-method"></a><span data-ttu-id="e2438-102">SetAssemblyFile – metoda</span><span class="sxs-lookup"><span data-stu-id="e2438-102">SetAssemblyFile Method</span></span>
<span data-ttu-id="e2438-103">Přiřadí název sestavení, která má být sestaven.</span><span class="sxs-lookup"><span data-stu-id="e2438-103">Assigns the name of the assembly to be built.</span></span> <span data-ttu-id="e2438-104">Není pro použití při vytváření nevázaných moduly.</span><span class="sxs-lookup"><span data-stu-id="e2438-104">Not for use when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2438-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2438-105">Syntax</span></span>  
  
```  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e2438-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e2438-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="e2438-107">Plně kvalifikovaný název souboru manifestu.</span><span class="sxs-lookup"><span data-stu-id="e2438-107">Fully qualified name of the manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="e2438-108">Ukazatel na [imetadataemit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e2438-108">Pointer to [IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="e2438-109">Flags – jak jsou definovány v [AssemblyFlags – výčet](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="e2438-109">Flags as defined in [AssemblyFlags Enumeration](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="e2438-110">Ukazatel na ID výsledné sestavení.</span><span class="sxs-lookup"><span data-stu-id="e2438-110">Pointer to ID of resulting assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e2438-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e2438-111">Return Value</span></span>  
 <span data-ttu-id="e2438-112">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="e2438-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2438-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e2438-113">Requirements</span></span>  
 <span data-ttu-id="e2438-114">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="e2438-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2438-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="e2438-115">See Also</span></span>  
 [<span data-ttu-id="e2438-116">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e2438-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="e2438-117">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e2438-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="e2438-118">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="e2438-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
