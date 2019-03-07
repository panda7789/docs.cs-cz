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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bf6e0c1de9bfb920932e5c22adb4eb8573125506
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489954"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a><span data-ttu-id="80a27-102">IMetaDataAssemblyEmit::DefineAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="80a27-102">IMetaDataAssemblyEmit::DefineAssembly Method</span></span>
<span data-ttu-id="80a27-103">Vytvoří `Assembly` struktury obsahující metadata pro zadané sestavení a vrátí token metadat.</span><span class="sxs-lookup"><span data-stu-id="80a27-103">Creates an `Assembly` structure containing metadata for the specified assembly and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80a27-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80a27-104">Syntax</span></span>  
  
```  
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
  
## <a name="parameters"></a><span data-ttu-id="80a27-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="80a27-105">Parameters</span></span>  
 `pbPublicKey`  
 <span data-ttu-id="80a27-106">[in] Veřejný klíč, který identifikuje vydavatele sestavení nebo hodnota NULL, pokud sestavení není silně pojmenováno.</span><span class="sxs-lookup"><span data-stu-id="80a27-106">[in] The public key that identifies the publisher of the assembly, or NULL if the assembly is not strongly named.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="80a27-107">[in] Velikost v bajtech `pbPublicKey`.</span><span class="sxs-lookup"><span data-stu-id="80a27-107">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="80a27-108">[in] Identifikátor algoritmu hash určený k šifrování souborů v sestavení nebo hodnota NULL k určení algoritmus SHA-1.</span><span class="sxs-lookup"><span data-stu-id="80a27-108">[in] The identifier of the hashing algorithm to use to encrypt the files in the assembly, or NULL to specify the SHA-1 algorithm.</span></span>  
  
 `szName`  
 <span data-ttu-id="80a27-109">[in] Uživatelsky čitelná textová název sestavení.</span><span class="sxs-lookup"><span data-stu-id="80a27-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="80a27-110">Tato hodnota nesmí překročit 1024 znaků.</span><span class="sxs-lookup"><span data-stu-id="80a27-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="80a27-111">[in] Ukazatel na instanci assemblymetadata –, který obsahuje informace o verzi, platformy a národní prostředí pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="80a27-111">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="80a27-112">[in] Kombinace [corassemblyflags –](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) hodnoty, které popisují funkce sestavení.</span><span class="sxs-lookup"><span data-stu-id="80a27-112">[in] A combination of [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values that describe features of the assembly.</span></span>  
  
 `pmda`  
 <span data-ttu-id="80a27-113">[out] Ukazatel na token metadat.</span><span class="sxs-lookup"><span data-stu-id="80a27-113">[out] A pointer to the metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80a27-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="80a27-114">Remarks</span></span>  
 <span data-ttu-id="80a27-115">Pouze jeden `Assembly` metadat struktury lze definovat v rámci manifestu.</span><span class="sxs-lookup"><span data-stu-id="80a27-115">Only one `Assembly` metadata structure can be defined within a manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80a27-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="80a27-116">Requirements</span></span>  
 <span data-ttu-id="80a27-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80a27-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80a27-118">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="80a27-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="80a27-119">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="80a27-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="80a27-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80a27-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80a27-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="80a27-121">See also</span></span>
- [<span data-ttu-id="80a27-122">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="80a27-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
