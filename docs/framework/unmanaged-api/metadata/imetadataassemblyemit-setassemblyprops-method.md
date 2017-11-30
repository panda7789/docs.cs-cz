---
title: "IMetaDataAssemblyEmit::SetAssemblyProps – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.SetAssemblyProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyProps method [.NET Framework metadata]
ms.assetid: 91b633d7-9e75-43c3-a8d2-2144984e5f9e
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d2c9336855d706a9861d4e832e5f0234cdf04db7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyemitsetassemblyprops-method"></a><span data-ttu-id="53126-102">IMetaDataAssemblyEmit::SetAssemblyProps – metoda</span><span class="sxs-lookup"><span data-stu-id="53126-102">IMetaDataAssemblyEmit::SetAssemblyProps Method</span></span>
<span data-ttu-id="53126-103">Upraví zadaný `Assembly` strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="53126-103">Modifies the specified `Assembly` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53126-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53126-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="53126-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="53126-105">Parameters</span></span>  
 `pma`  
 <span data-ttu-id="53126-106">[v] Metadata token, který určuje `Assembly` strukturu metadat má být změněn.</span><span class="sxs-lookup"><span data-stu-id="53126-106">[in] The metadata token that specifies the `Assembly` metadata structure to be modified.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="53126-107">[v] Ukazatel na veřejný klíč vydavatele sestavení.</span><span class="sxs-lookup"><span data-stu-id="53126-107">[in] A pointer to the public key of the publisher of the assembly.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="53126-108">[v] Velikost v bajtech `pbPublicKey`.</span><span class="sxs-lookup"><span data-stu-id="53126-108">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `ulHashAlgId`  
 <span data-ttu-id="53126-109">[v] Identifikátor algoritmu hash používaného hodnoty hash souborů sestavení.</span><span class="sxs-lookup"><span data-stu-id="53126-109">[in] The identifier for the hash algorithm used to hash the assembly files.</span></span>  
  
 `szName`  
 <span data-ttu-id="53126-110">[v] Čitelný text název sestavení.</span><span class="sxs-lookup"><span data-stu-id="53126-110">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="53126-111">[v] Ukazatel na assemblymetadata –, který obsahuje informace o verzi, platformy a národní prostředí pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="53126-111">[in] A pointer to the ASSEMBLYMETADATA that contains version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="53126-112">[v] Bitovou kombinaci [AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md) hodnoty, které určují různé atributy sestavení.</span><span class="sxs-lookup"><span data-stu-id="53126-112">[in] A bitwise combination of [AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md) values that specify various attributes of the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53126-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="53126-113">Remarks</span></span>  
 <span data-ttu-id="53126-114">Chcete-li vytvořit `Assembly` strukturu metadat, použijte [imetadataassemblyemit::defineassembly –](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="53126-114">To create an `Assembly` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssembly](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53126-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="53126-115">Requirements</span></span>  
 <span data-ttu-id="53126-116">**Platforma:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53126-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53126-117">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="53126-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="53126-118">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="53126-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="53126-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53126-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53126-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="53126-120">See Also</span></span>  
 [<span data-ttu-id="53126-121">Imetadataassemblyemit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="53126-121">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
