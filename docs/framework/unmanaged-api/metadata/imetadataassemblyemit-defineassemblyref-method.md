---
title: IMetaDataAssemblyEmit::DefineAssemblyRef – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineAssemblyRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineAssemblyRef
helpviewer_keywords:
- DefineAssemblyRef method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineAssemblyRef method [.NET Framework metadata]
ms.assetid: 0b284b18-0084-4b3a-912a-5ebe9f29c88b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c150f4bda901627fc21ed54926c3cf959bb829a3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776303"
---
# <a name="imetadataassemblyemitdefineassemblyref-method"></a><span data-ttu-id="d97c7-102">IMetaDataAssemblyEmit::DefineAssemblyRef – metoda</span><span class="sxs-lookup"><span data-stu-id="d97c7-102">IMetaDataAssemblyEmit::DefineAssemblyRef Method</span></span>
<span data-ttu-id="d97c7-103">Vytvoří `AssemblyRef` struktura obsahující metadata pro sestavení, které toto sestavení odkazuje a vrátí token metadat.</span><span class="sxs-lookup"><span data-stu-id="d97c7-103">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d97c7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d97c7-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineAssemblyRef (  
    [in]  void                *pbPublicKeyOrToken,  
    [in]  ULONG               cbPublicKeyOrToken,  
    [in]  LPCWSTR             szName,  
    [in]  ASSEMBLYMETADATA    pMetaData,  
    [in]  void                *pbHashValue,  
    [in]  ULONG               cbHashValue,  
    [in]  DWORD               dwAssemblyRefFlags,  
    [out] mdAssemblyRef       *pmdar  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d97c7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d97c7-105">Parameters</span></span>  
 `pbPublicKeyOrToken`  
 <span data-ttu-id="d97c7-106">[in] Veřejný klíč vydavatele odkazovaných sestavení.</span><span class="sxs-lookup"><span data-stu-id="d97c7-106">[in] The public key of the publisher of the referenced assembly.</span></span> <span data-ttu-id="d97c7-107">Pomocná funkce [strongnametokenfromassembly –](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md) můžete použít k získání hodnota hash veřejného klíče předejte jako tento parametr.</span><span class="sxs-lookup"><span data-stu-id="d97c7-107">The helper function [StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md) can be used to get the hash of the public key to pass as this parameter.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="d97c7-108">[in] Velikost v bajtech `pbPublicKeyOrToken`.</span><span class="sxs-lookup"><span data-stu-id="d97c7-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="d97c7-109">[in] Uživatelsky čitelná textová název sestavení.</span><span class="sxs-lookup"><span data-stu-id="d97c7-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="d97c7-110">Tato hodnota nesmí překročit 1024 znaků.</span><span class="sxs-lookup"><span data-stu-id="d97c7-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="d97c7-111">[in] Assemblymetadata – instance, který obsahuje informace o verzi, platformy a národní prostředí odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="d97c7-111">[in] An ASSEMBLYMETADATA instance that contains the version, platform and locale information of the referenced assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="d97c7-112">[in] Hodnota hash data přidružená k odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="d97c7-112">[in] The hash data associated with the referenced assembly.</span></span> <span data-ttu-id="d97c7-113">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="d97c7-113">Optional.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="d97c7-114">[in] Velikost v bajtech `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="d97c7-114">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="d97c7-115">[in] Bitová kombinace hodnot [corassemblyflags –](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) hodnoty, které ovlivňují chování prováděcího modulu.</span><span class="sxs-lookup"><span data-stu-id="d97c7-115">[in] A bitwise combination of [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values that influence the behavior of the execution engine.</span></span>  
  
 `pmdar`  
 <span data-ttu-id="d97c7-116">[out] Ukazatel na vrácenou `AssemblyRef` token metadat.</span><span class="sxs-lookup"><span data-stu-id="d97c7-116">[out] A pointer to the returned `AssemblyRef` metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d97c7-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d97c7-117">Remarks</span></span>  
 <span data-ttu-id="d97c7-118">Jeden `AssemblyRef` struktury metadat musí být definované pro jednotlivá sestavení, která toto sestavení odkazuje.</span><span class="sxs-lookup"><span data-stu-id="d97c7-118">One `AssemblyRef` metadata structure must be defined for each assembly that this assembly references.</span></span>  
  
 <span data-ttu-id="d97c7-119">Podrobnosti o odkazovaném sestavení v době běhu, jsou předány překladač sestavení s údajem, že představují informace "jako předdefinovaný".</span><span class="sxs-lookup"><span data-stu-id="d97c7-119">At run time, the details of a referenced assembly are passed to the assembly resolver with an indication that they represent the "as built" information.</span></span> <span data-ttu-id="d97c7-120">Překladač sestavení potom použije zásady.</span><span class="sxs-lookup"><span data-stu-id="d97c7-120">The assembly resolver then applies policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d97c7-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d97c7-121">Requirements</span></span>  
 <span data-ttu-id="d97c7-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d97c7-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d97c7-123">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d97c7-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d97c7-124">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d97c7-124">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d97c7-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d97c7-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d97c7-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d97c7-126">See also</span></span>

- [<span data-ttu-id="d97c7-127">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d97c7-127">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
