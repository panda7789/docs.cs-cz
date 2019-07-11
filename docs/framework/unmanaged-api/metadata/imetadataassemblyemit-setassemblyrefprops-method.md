---
title: IMetaDataAssemblyEmit::SetAssemblyRefProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyRefProps
helpviewer_keywords:
- SetAssemblyRefProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 70a32bf3-9051-4f96-ae87-11356d06a073
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 984ec5dea757971081ce05c858788473a0f616e7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775270"
---
# <a name="imetadataassemblyemitsetassemblyrefprops-method"></a><span data-ttu-id="0f8b8-102">IMetaDataAssemblyEmit::SetAssemblyRefProps – metoda</span><span class="sxs-lookup"><span data-stu-id="0f8b8-102">IMetaDataAssemblyEmit::SetAssemblyRefProps Method</span></span>
<span data-ttu-id="0f8b8-103">Upraví zadaný `AssemblyRef` struktury metadat.</span><span class="sxs-lookup"><span data-stu-id="0f8b8-103">Modifies the specified `AssemblyRef` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f8b8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f8b8-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="0f8b8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0f8b8-105">Parameters</span></span>  
 `ar`  
 <span data-ttu-id="0f8b8-106">[in] Token metadat, který určuje `AssemblyRef` struktury metadat má být upraven.</span><span class="sxs-lookup"><span data-stu-id="0f8b8-106">[in] The metadata token that specifies the `AssemblyRef` metadata structure to be modified.</span></span>  
  
 `pbPublicKeyOrToken`  
 <span data-ttu-id="0f8b8-107">[in] Veřejný klíč vydavatele odkazovaných sestavení.</span><span class="sxs-lookup"><span data-stu-id="0f8b8-107">[in] The public key of the publisher of the referenced assembly.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="0f8b8-108">[in] Velikost v bajtech `pbPublicKeyOrToken`.</span><span class="sxs-lookup"><span data-stu-id="0f8b8-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="0f8b8-109">[in] Uživatelsky čitelná textová název sestavení.</span><span class="sxs-lookup"><span data-stu-id="0f8b8-109">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="0f8b8-110">[in] Ukazatel na instanci assemblymetadata –, který obsahuje informace o verzi, platformy a národní prostředí pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="0f8b8-110">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="0f8b8-111">[in] Ukazatel na hodnotu hash dat přidružené k sestavení.</span><span class="sxs-lookup"><span data-stu-id="0f8b8-111">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="0f8b8-112">[in] Velikost v bajtech `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="0f8b8-112">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="0f8b8-113">[in] Bitová kombinace hodnot [assemblyrefflags –](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) hodnoty, které určují atributy odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="0f8b8-113">[in] A bitwise combination of [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) values that specify attributes of the referenced assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f8b8-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0f8b8-114">Remarks</span></span>  
 <span data-ttu-id="0f8b8-115">K vytvoření `AssemblyRef` struktury metadat, použijte [imetadataassemblyemit::defineassemblyref –](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="0f8b8-115">To create an `AssemblyRef` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f8b8-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0f8b8-116">Requirements</span></span>  
 <span data-ttu-id="0f8b8-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f8b8-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f8b8-118">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0f8b8-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0f8b8-119">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0f8b8-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0f8b8-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f8b8-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f8b8-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0f8b8-121">See also</span></span>

- [<span data-ttu-id="0f8b8-122">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0f8b8-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
