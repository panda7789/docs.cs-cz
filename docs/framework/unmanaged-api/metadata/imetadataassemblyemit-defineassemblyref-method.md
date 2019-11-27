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
ms.openlocfilehash: c88b7a401a19b1bd0e02edab7ef7bbee1372199e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432077"
---
# <a name="imetadataassemblyemitdefineassemblyref-method"></a><span data-ttu-id="3de18-102">IMetaDataAssemblyEmit::DefineAssemblyRef – metoda</span><span class="sxs-lookup"><span data-stu-id="3de18-102">IMetaDataAssemblyEmit::DefineAssemblyRef Method</span></span>
<span data-ttu-id="3de18-103">Vytvoří strukturu `AssemblyRef` obsahující metadata pro sestavení, na které odkazuje toto sestavení, a vrátí přidružený token metadat.</span><span class="sxs-lookup"><span data-stu-id="3de18-103">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3de18-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3de18-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="3de18-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3de18-105">Parameters</span></span>  
 `pbPublicKeyOrToken`  
 <span data-ttu-id="3de18-106">pro Veřejný klíč vydavatele odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="3de18-106">[in] The public key of the publisher of the referenced assembly.</span></span> <span data-ttu-id="3de18-107">Pomocná funkce [StrongNameTokenFromAssembly –](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md) se dá použít k získání hodnoty hash veřejného klíče, která se má předat jako tento parametr.</span><span class="sxs-lookup"><span data-stu-id="3de18-107">The helper function [StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md) can be used to get the hash of the public key to pass as this parameter.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="3de18-108">pro Velikost v bajtech `pbPublicKeyOrToken`.</span><span class="sxs-lookup"><span data-stu-id="3de18-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="3de18-109">pro Textový název sestavení čitelný lidmi</span><span class="sxs-lookup"><span data-stu-id="3de18-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="3de18-110">Tato hodnota nesmí překročit 1024 znaků.</span><span class="sxs-lookup"><span data-stu-id="3de18-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="3de18-111">pro Instance AssemblyMetadata –, která obsahuje informace o verzi, platformě a národním prostředí odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="3de18-111">[in] An ASSEMBLYMETADATA instance that contains the version, platform and locale information of the referenced assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="3de18-112">pro Data algoritmu hash přidružená k odkazovanému sestavení</span><span class="sxs-lookup"><span data-stu-id="3de18-112">[in] The hash data associated with the referenced assembly.</span></span> <span data-ttu-id="3de18-113">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="3de18-113">Optional.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="3de18-114">pro Velikost v bajtech `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="3de18-114">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="3de18-115">pro Bitová kombinace hodnot [CorAssemblyFlags –](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) , která má vliv na chování prováděcího modulu.</span><span class="sxs-lookup"><span data-stu-id="3de18-115">[in] A bitwise combination of [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values that influence the behavior of the execution engine.</span></span>  
  
 `pmdar`  
 <span data-ttu-id="3de18-116">mimo Ukazatel na vrácený `AssemblyRef` token metadat.</span><span class="sxs-lookup"><span data-stu-id="3de18-116">[out] A pointer to the returned `AssemblyRef` metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3de18-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3de18-117">Remarks</span></span>  
 <span data-ttu-id="3de18-118">Pro každé sestavení, na které odkazuje toto sestavení, musí být definována jedna `AssemblyRef` struktura metadat.</span><span class="sxs-lookup"><span data-stu-id="3de18-118">One `AssemblyRef` metadata structure must be defined for each assembly that this assembly references.</span></span>  
  
 <span data-ttu-id="3de18-119">V době běhu jsou podrobnosti odkazovaného sestavení předány do překladače sestavení s označením, že představují informace "sestavené".</span><span class="sxs-lookup"><span data-stu-id="3de18-119">At run time, the details of a referenced assembly are passed to the assembly resolver with an indication that they represent the "as built" information.</span></span> <span data-ttu-id="3de18-120">Překladač sestavení následně aplikuje zásady.</span><span class="sxs-lookup"><span data-stu-id="3de18-120">The assembly resolver then applies policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3de18-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3de18-121">Requirements</span></span>  
 <span data-ttu-id="3de18-122">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3de18-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3de18-123">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3de18-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3de18-124">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="3de18-124">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3de18-125">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3de18-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3de18-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3de18-126">See also</span></span>

- [<span data-ttu-id="3de18-127">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3de18-127">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
