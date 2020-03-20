---
title: IMetaDataAssemblyEmit::DefineAssembly – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineAssembly
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineAssembly method [.NET Framework metadata]
- DefineAssembly method [.NET Framework metadata]
ms.assetid: a0637d66-74bf-4f2d-8137-9ff838bccece
topic_type:
- apiref
ms.openlocfilehash: 14bd352099890e4ca36321d550b8e982d4373231
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177891"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a><span data-ttu-id="86c35-102">IMetaDataAssemblyEmit::DefineAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="86c35-102">IMetaDataAssemblyEmit::DefineAssembly Method</span></span>
<span data-ttu-id="86c35-103">Vytvoří `Assembly` strukturu obsahující metadata pro zadané sestavení a vrátí přidružený token metadat.</span><span class="sxs-lookup"><span data-stu-id="86c35-103">Creates an `Assembly` structure containing metadata for the specified assembly and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86c35-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86c35-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineAssembly (  
    [in]  void                 *pbPublicKey,  
    [in]  ULONG                cbPublicKey,  
    [in]  ULONG                uHashAlgId,  
    [in]  LPCWSTR              szName,
    [in]  ASSEMBLYMETADATA     *pMetaData,  
    [in]  DWORD                dwAssemblyFlags,  
    [out] mdAssembly           *pmda  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86c35-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="86c35-105">Parameters</span></span>  
 `pbPublicKey`  
 <span data-ttu-id="86c35-106">[v] Veřejný klíč, který identifikuje vydavatele sestavení nebo NULL, pokud sestavení není silně pojmenované.</span><span class="sxs-lookup"><span data-stu-id="86c35-106">[in] The public key that identifies the publisher of the assembly, or NULL if the assembly is not strongly named.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="86c35-107">[v] Velikost v bajtů `pbPublicKey`.</span><span class="sxs-lookup"><span data-stu-id="86c35-107">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="86c35-108">[v] Identifikátor algoritmu hash, který se má použít k šifrování souborů v sestavení, nebo null pro určení algoritmu SHA-1.</span><span class="sxs-lookup"><span data-stu-id="86c35-108">[in] The identifier of the hashing algorithm to use to encrypt the files in the assembly, or NULL to specify the SHA-1 algorithm.</span></span>  
  
 `szName`  
 <span data-ttu-id="86c35-109">[v] Text čitelný pro člověka název sestavení.</span><span class="sxs-lookup"><span data-stu-id="86c35-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="86c35-110">Tato hodnota nesmí překročit 1024 znaků.</span><span class="sxs-lookup"><span data-stu-id="86c35-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="86c35-111">[v] Ukazatel na instanci ASSEMBLYMETADATA, která obsahuje informace o verzi, platformě a národním prostředí pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="86c35-111">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="86c35-112">[v] Kombinace hodnot [CorAssemblyFlags,](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) které popisují prvky sestavy.</span><span class="sxs-lookup"><span data-stu-id="86c35-112">[in] A combination of [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values that describe features of the assembly.</span></span>  
  
 `pmda`  
 <span data-ttu-id="86c35-113">[out] Ukazatel na token metadat.</span><span class="sxs-lookup"><span data-stu-id="86c35-113">[out] A pointer to the metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86c35-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="86c35-114">Remarks</span></span>  
 <span data-ttu-id="86c35-115">V `Assembly` rámci manifestu lze definovat pouze jednu strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="86c35-115">Only one `Assembly` metadata structure can be defined within a manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86c35-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="86c35-116">Requirements</span></span>  
 <span data-ttu-id="86c35-117">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86c35-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86c35-118">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="86c35-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="86c35-119">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="86c35-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="86c35-120">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86c35-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86c35-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="86c35-121">See also</span></span>

- [<span data-ttu-id="86c35-122">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="86c35-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
