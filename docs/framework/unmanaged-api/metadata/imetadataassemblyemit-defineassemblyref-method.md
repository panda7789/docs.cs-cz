---
title: "IMetaDataAssemblyEmit::DefineAssemblyRef – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.DefineAssemblyRef
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::DefineAssemblyRef
helpviewer_keywords:
- DefineAssemblyRef method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineAssemblyRef method [.NET Framework metadata]
ms.assetid: 0b284b18-0084-4b3a-912a-5ebe9f29c88b
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 123bd37d189477eade72e3b0e74f923fecce57a7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemitdefineassemblyref-method"></a><span data-ttu-id="9a2b3-102">IMetaDataAssemblyEmit::DefineAssemblyRef – metoda</span><span class="sxs-lookup"><span data-stu-id="9a2b3-102">IMetaDataAssemblyEmit::DefineAssemblyRef Method</span></span>
<span data-ttu-id="9a2b3-103">Vytvoří `AssemblyRef` struktura obsahující metadata pro sestavení, které toto sestavení odkazuje a vrátí token přidružených metadat.</span><span class="sxs-lookup"><span data-stu-id="9a2b3-103">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a2b3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9a2b3-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="9a2b3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9a2b3-105">Parameters</span></span>  
 `pbPublicKeyOrToken`  
 <span data-ttu-id="9a2b3-106">[v] Veřejný klíč vydavatele odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="9a2b3-106">[in] The public key of the publisher of the referenced assembly.</span></span> <span data-ttu-id="9a2b3-107">Pomocné funkce [strongnametokenfromassembly –](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md) můžete použít k získání hodnota hash veřejného klíče předat jako tento parametr.</span><span class="sxs-lookup"><span data-stu-id="9a2b3-107">The helper function [StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md) can be used to get the hash of the public key to pass as this parameter.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="9a2b3-108">[v] Velikost v bajtech `pbPublicKeyOrToken`.</span><span class="sxs-lookup"><span data-stu-id="9a2b3-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="9a2b3-109">[v] Čitelný text název sestavení.</span><span class="sxs-lookup"><span data-stu-id="9a2b3-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="9a2b3-110">Tato hodnota nesmí být delší než 1024 znaků.</span><span class="sxs-lookup"><span data-stu-id="9a2b3-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="9a2b3-111">[v] Assemblymetadata – instance, který obsahuje informace o verzi, platformy a národní prostředí odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="9a2b3-111">[in] An ASSEMBLYMETADATA instance that contains the version, platform and locale information of the referenced assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="9a2b3-112">[v] Hodnota hash data související s odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="9a2b3-112">[in] The hash data associated with the referenced assembly.</span></span> <span data-ttu-id="9a2b3-113">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="9a2b3-113">Optional.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="9a2b3-114">[v] Velikost v bajtech `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="9a2b3-114">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="9a2b3-115">[v] Bitovou kombinaci [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) hodnoty, které ovlivňují chování objektu modul provádění.</span><span class="sxs-lookup"><span data-stu-id="9a2b3-115">[in] A bitwise combination of [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values that influence the behavior of the execution engine.</span></span>  
  
 `pmdar`  
 <span data-ttu-id="9a2b3-116">[out] Ukazatel na vrácený `AssemblyRef` metadata token.</span><span class="sxs-lookup"><span data-stu-id="9a2b3-116">[out] A pointer to the returned `AssemblyRef` metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a2b3-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9a2b3-117">Remarks</span></span>  
 <span data-ttu-id="9a2b3-118">Jeden `AssemblyRef` strukturu metadat musí být definovaná pro každé sestavení, které odkazuje toto sestavení.</span><span class="sxs-lookup"><span data-stu-id="9a2b3-118">One `AssemblyRef` metadata structure must be defined for each assembly that this assembly references.</span></span>  
  
 <span data-ttu-id="9a2b3-119">V době běhu podrobnosti o odkazované sestavení předaný překladač sestavení s údajem, že představují údaje "tak, jak vytvořené".</span><span class="sxs-lookup"><span data-stu-id="9a2b3-119">At run time, the details of a referenced assembly are passed to the assembly resolver with an indication that they represent the "as built" information.</span></span> <span data-ttu-id="9a2b3-120">Překladač sestavení potom platí zásady.</span><span class="sxs-lookup"><span data-stu-id="9a2b3-120">The assembly resolver then applies policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a2b3-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9a2b3-121">Requirements</span></span>  
 <span data-ttu-id="9a2b3-122">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a2b3-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a2b3-123">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9a2b3-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9a2b3-124">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9a2b3-124">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9a2b3-125">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a2b3-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a2b3-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="9a2b3-126">See Also</span></span>  
 [<span data-ttu-id="9a2b3-127">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9a2b3-127">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
