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
ms.openlocfilehash: 6ad6bbb8a4c69f575bbeba3a297c46e049a97325
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176042"
---
# <a name="imetadataassemblyemitsetassemblyrefprops-method"></a><span data-ttu-id="47720-102">IMetaDataAssemblyEmit::SetAssemblyRefProps – metoda</span><span class="sxs-lookup"><span data-stu-id="47720-102">IMetaDataAssemblyEmit::SetAssemblyRefProps Method</span></span>
<span data-ttu-id="47720-103">Upraví zadanou `AssemblyRef` strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="47720-103">Modifies the specified `AssemblyRef` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47720-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47720-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="47720-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="47720-105">Parameters</span></span>  
 `ar`  
 <span data-ttu-id="47720-106">[v] Token metadat, který určuje `AssemblyRef` strukturu metadat, která má být změněna.</span><span class="sxs-lookup"><span data-stu-id="47720-106">[in] The metadata token that specifies the `AssemblyRef` metadata structure to be modified.</span></span>  
  
 `pbPublicKeyOrToken`  
 <span data-ttu-id="47720-107">[v] Veřejný klíč vydavatele odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="47720-107">[in] The public key of the publisher of the referenced assembly.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="47720-108">[v] Velikost v bajtů `pbPublicKeyOrToken`.</span><span class="sxs-lookup"><span data-stu-id="47720-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="47720-109">[v] Text čitelný pro člověka název sestavení.</span><span class="sxs-lookup"><span data-stu-id="47720-109">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="47720-110">[v] Ukazatel na instanci ASSEMBLYMETADATA, která obsahuje informace o verzi, platformě a národním prostředí pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="47720-110">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="47720-111">[v] Ukazatel na data hash přidružená k sestavení.</span><span class="sxs-lookup"><span data-stu-id="47720-111">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="47720-112">[v] Velikost v bajtů `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="47720-112">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="47720-113">[v] Bitová kombinace hodnot [AssemblyRefFlags,](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) které určují atributy odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="47720-113">[in] A bitwise combination of [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) values that specify attributes of the referenced assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47720-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="47720-114">Remarks</span></span>  
 <span data-ttu-id="47720-115">Chcete-li `AssemblyRef` vytvořit strukturu metadat, použijte metodu [IMetaDataAssemblyEmit::DefineAssemblyRef.](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)</span><span class="sxs-lookup"><span data-stu-id="47720-115">To create an `AssemblyRef` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47720-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="47720-116">Requirements</span></span>  
 <span data-ttu-id="47720-117">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47720-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47720-118">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="47720-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="47720-119">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="47720-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="47720-120">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47720-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47720-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="47720-121">See also</span></span>

- [<span data-ttu-id="47720-122">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="47720-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
