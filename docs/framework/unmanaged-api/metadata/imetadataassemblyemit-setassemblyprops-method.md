---
title: IMetaDataAssemblyEmit::SetAssemblyProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyProps method [.NET Framework metadata]
ms.assetid: 91b633d7-9e75-43c3-a8d2-2144984e5f9e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 37d91ca7935e114504864683075f4809de7270fd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54599111"
---
# <a name="imetadataassemblyemitsetassemblyprops-method"></a><span data-ttu-id="942d9-102">IMetaDataAssemblyEmit::SetAssemblyProps – metoda</span><span class="sxs-lookup"><span data-stu-id="942d9-102">IMetaDataAssemblyEmit::SetAssemblyProps Method</span></span>
<span data-ttu-id="942d9-103">Upraví zadaný `Assembly` struktury metadat.</span><span class="sxs-lookup"><span data-stu-id="942d9-103">Modifies the specified `Assembly` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="942d9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="942d9-104">Syntax</span></span>  
  
```  
HRESULT SetAssemblyProps (  
    [in] mdAssembly               pma,  
    [in] const void               *pbPublicKey,  
    [in] ULONG                    cbPublicKey,  
    [in] ULONG                    ulHashAlgId,  
    [in] LPCWSTR                  szName,  
    [in] const ASSEMBLYMETADATA   *pMetaData,  
    [in] DWORD                    dwAssemblyFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="942d9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="942d9-105">Parameters</span></span>  
 `pma`  
 <span data-ttu-id="942d9-106">[in] Token metadat, který určuje `Assembly` struktury metadat má být upraven.</span><span class="sxs-lookup"><span data-stu-id="942d9-106">[in] The metadata token that specifies the `Assembly` metadata structure to be modified.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="942d9-107">[in] Ukazatel na veřejný klíč sestavení vydavatele.</span><span class="sxs-lookup"><span data-stu-id="942d9-107">[in] A pointer to the public key of the publisher of the assembly.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="942d9-108">[in] Velikost v bajtech `pbPublicKey`.</span><span class="sxs-lookup"><span data-stu-id="942d9-108">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `ulHashAlgId`  
 <span data-ttu-id="942d9-109">[in] Identifikátor algoritmu hash používá k vytvoření hodnoty hash souborů sestavení.</span><span class="sxs-lookup"><span data-stu-id="942d9-109">[in] The identifier for the hash algorithm used to hash the assembly files.</span></span>  
  
 `szName`  
 <span data-ttu-id="942d9-110">[in] Uživatelsky čitelná textová název sestavení.</span><span class="sxs-lookup"><span data-stu-id="942d9-110">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="942d9-111">[in] Ukazatel na assemblymetadata –, který obsahuje informace o verzi, platformy a národní prostředí pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="942d9-111">[in] A pointer to the ASSEMBLYMETADATA that contains version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="942d9-112">[in] Bitová kombinace hodnot [assemblyflags –](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md) hodnoty, které určují různé atributy sestavení.</span><span class="sxs-lookup"><span data-stu-id="942d9-112">[in] A bitwise combination of [AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md) values that specify various attributes of the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="942d9-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="942d9-113">Remarks</span></span>  
 <span data-ttu-id="942d9-114">K vytvoření `Assembly` struktury metadat, použijte [imetadataassemblyemit::defineassembly –](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="942d9-114">To create an `Assembly` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssembly](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="942d9-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="942d9-115">Requirements</span></span>  
 <span data-ttu-id="942d9-116">**Platforma:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="942d9-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="942d9-117">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="942d9-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="942d9-118">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="942d9-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="942d9-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="942d9-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="942d9-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="942d9-120">See also</span></span>
- [<span data-ttu-id="942d9-121">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="942d9-121">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
