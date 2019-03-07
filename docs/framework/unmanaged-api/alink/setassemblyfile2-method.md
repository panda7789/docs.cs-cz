---
title: SetAssemblyFile2 – metoda
ms.date: 03/30/2017
api_name:
- IALink2.SetAssemblyFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile2
helpviewer_keywords:
- SetAssemblyFile2 method
ms.assetid: eedb9125-1ef1-4000-abfc-7de86e5a1f17
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 41e10855a7254da4124ac0bf9aa247b90311632b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479075"
---
# <a name="setassemblyfile2-method"></a><span data-ttu-id="c8758-102">SetAssemblyFile2 – metoda</span><span class="sxs-lookup"><span data-stu-id="c8758-102">SetAssemblyFile2 Method</span></span>
<span data-ttu-id="c8758-103">Nastaví název a možnosti pro nové sestavení.</span><span class="sxs-lookup"><span data-stu-id="c8758-103">Sets the name of and options for a new assembly.</span></span> <span data-ttu-id="c8758-104">Nevolejte tuto metodu při vytvoření nevázaného moduly.</span><span class="sxs-lookup"><span data-stu-id="c8758-104">Do not call this method when you produce unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8758-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c8758-105">Syntax</span></span>  
  
```  
HRESULT SetAssemblyFile2(  
    LPCWSTR pszFilename,  
    IMetaDataEmit2* pEmitter,  
    AssemblyFlags   afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8758-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c8758-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="c8758-107">Název souboru manifestu.</span><span class="sxs-lookup"><span data-stu-id="c8758-107">Name of manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="c8758-108">[Imetadataemit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) rozhraní pro tento soubor.</span><span class="sxs-lookup"><span data-stu-id="c8758-108">[IMetaDataEmit2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interface for this file.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="c8758-109">Možnosti reprezentována [assemblyflags – výčet](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="c8758-109">Options represented by [AssemblyFlags Enumeration](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="c8758-110">Získá jedinečné ID pro sestavení vytváří.</span><span class="sxs-lookup"><span data-stu-id="c8758-110">Receives unique ID for the assembly being constructed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c8758-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c8758-111">Return Value</span></span>  
 <span data-ttu-id="c8758-112">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="c8758-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8758-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c8758-113">Requirements</span></span>  
 <span data-ttu-id="c8758-114">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="c8758-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8758-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c8758-115">See also</span></span>
- [<span data-ttu-id="c8758-116">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c8758-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="c8758-117">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c8758-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="c8758-118">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="c8758-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
