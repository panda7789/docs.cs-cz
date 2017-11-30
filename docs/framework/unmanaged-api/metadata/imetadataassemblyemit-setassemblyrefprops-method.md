---
title: "IMetaDataAssemblyEmit::SetAssemblyRefProps – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.SetAssemblyRefProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::SetAssemblyRefProps
helpviewer_keywords:
- SetAssemblyRefProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 70a32bf3-9051-4f96-ae87-11356d06a073
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 84b6c0d748578b717a128ff3b808977ba902c6dc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyemitsetassemblyrefprops-method"></a><span data-ttu-id="f2180-102">IMetaDataAssemblyEmit::SetAssemblyRefProps – metoda</span><span class="sxs-lookup"><span data-stu-id="f2180-102">IMetaDataAssemblyEmit::SetAssemblyRefProps Method</span></span>
<span data-ttu-id="f2180-103">Upraví zadaný `AssemblyRef` strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="f2180-103">Modifies the specified `AssemblyRef` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2180-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2180-104">Syntax</span></span>  
  
```  
HRESULT SetAssemblyRefProps (  
    [in] mdAssemblyRef              ar,  
    [in] const void                 *pbPublicKeyOrToken,  
    [in] ULONG                      cbPublicKeyOrToken,  
    [in] LPCWSTR                    szName,   
    [in] const ASSEMBLYMETADATA     *pMetaData,   
    [in] const void                 *pbHashValue,  
    [in] ULONG                      cbHashValue,  
    [in] DWORD                      dwAssemblyRefFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f2180-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f2180-105">Parameters</span></span>  
 `ar`  
 <span data-ttu-id="f2180-106">[v] Metadata token, který určuje `AssemblyRef` strukturu metadat má být změněn.</span><span class="sxs-lookup"><span data-stu-id="f2180-106">[in] The metadata token that specifies the `AssemblyRef` metadata structure to be modified.</span></span>  
  
 `pbPublicKeyOrToken`  
 <span data-ttu-id="f2180-107">[v] Veřejný klíč vydavatele odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="f2180-107">[in] The public key of the publisher of the referenced assembly.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="f2180-108">[v] Velikost v bajtech `pbPublicKeyOrToken`.</span><span class="sxs-lookup"><span data-stu-id="f2180-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="f2180-109">[v] Čitelný text název sestavení.</span><span class="sxs-lookup"><span data-stu-id="f2180-109">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="f2180-110">[v] Ukazatel na instanci assemblymetadata –, který obsahuje informace o verzi, platformy a národní prostředí pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="f2180-110">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="f2180-111">[v] Ukazatel na hodnotu hash data přidružená k sestavení.</span><span class="sxs-lookup"><span data-stu-id="f2180-111">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="f2180-112">[v] Velikost v bajtech `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="f2180-112">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="f2180-113">[v] Bitovou kombinaci [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) hodnoty, které určují atributy odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="f2180-113">[in] A bitwise combination of [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) values that specify attributes of the referenced assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2180-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f2180-114">Remarks</span></span>  
 <span data-ttu-id="f2180-115">Chcete-li vytvořit `AssemblyRef` strukturu metadat, použijte [imetadataassemblyemit::defineassemblyref –](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="f2180-115">To create an `AssemblyRef` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2180-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f2180-116">Requirements</span></span>  
 <span data-ttu-id="f2180-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2180-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2180-118">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f2180-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f2180-119">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f2180-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f2180-120">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2180-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2180-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="f2180-121">See Also</span></span>  
 [<span data-ttu-id="f2180-122">Imetadataassemblyemit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f2180-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
