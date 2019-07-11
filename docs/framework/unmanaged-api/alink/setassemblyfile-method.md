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
ms.openlocfilehash: b7be346f1c92c877932957787b0747515c144752
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741546"
---
# <a name="setassemblyfile-method"></a><span data-ttu-id="bb781-102">SetAssemblyFile – metoda</span><span class="sxs-lookup"><span data-stu-id="bb781-102">SetAssemblyFile Method</span></span>
<span data-ttu-id="bb781-103">Přiřadí název sestavení, které má být sestaven.</span><span class="sxs-lookup"><span data-stu-id="bb781-103">Assigns the name of the assembly to be built.</span></span> <span data-ttu-id="bb781-104">Není pro použití při vytváření nevázaných moduly.</span><span class="sxs-lookup"><span data-stu-id="bb781-104">Not for use when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb781-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb781-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb781-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="bb781-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="bb781-107">Plně kvalifikovaný název souboru manifestu.</span><span class="sxs-lookup"><span data-stu-id="bb781-107">Fully qualified name of the manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="bb781-108">Ukazatel na [imetadataemit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bb781-108">Pointer to [IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="bb781-109">Označí příznakem, jak jsou definovány v [assemblyflags – výčet](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="bb781-109">Flags as defined in [AssemblyFlags Enumeration](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="bb781-110">Ukazatel na ID výsledné sestavení.</span><span class="sxs-lookup"><span data-stu-id="bb781-110">Pointer to ID of resulting assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bb781-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bb781-111">Return Value</span></span>  
 <span data-ttu-id="bb781-112">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="bb781-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb781-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bb781-113">Requirements</span></span>  
 <span data-ttu-id="bb781-114">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="bb781-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb781-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bb781-115">See also</span></span>

- [<span data-ttu-id="bb781-116">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bb781-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="bb781-117">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bb781-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="bb781-118">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="bb781-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
