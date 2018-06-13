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
ms.openlocfilehash: 6f8132296035e9ddcdcad76d93ed05358beb0b81
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448230"
---
# <a name="imetadataassemblyemitsetassemblyprops-method"></a><span data-ttu-id="08334-102">IMetaDataAssemblyEmit::SetAssemblyProps – metoda</span><span class="sxs-lookup"><span data-stu-id="08334-102">IMetaDataAssemblyEmit::SetAssemblyProps Method</span></span>
<span data-ttu-id="08334-103">Upraví zadaný `Assembly` strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="08334-103">Modifies the specified `Assembly` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08334-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08334-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="08334-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="08334-105">Parameters</span></span>  
 `pma`  
 <span data-ttu-id="08334-106">[v] Metadata token, který určuje `Assembly` strukturu metadat má být změněn.</span><span class="sxs-lookup"><span data-stu-id="08334-106">[in] The metadata token that specifies the `Assembly` metadata structure to be modified.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="08334-107">[v] Ukazatel na veřejný klíč vydavatele sestavení.</span><span class="sxs-lookup"><span data-stu-id="08334-107">[in] A pointer to the public key of the publisher of the assembly.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="08334-108">[v] Velikost v bajtech `pbPublicKey`.</span><span class="sxs-lookup"><span data-stu-id="08334-108">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `ulHashAlgId`  
 <span data-ttu-id="08334-109">[v] Identifikátor algoritmu hash používaného hodnoty hash souborů sestavení.</span><span class="sxs-lookup"><span data-stu-id="08334-109">[in] The identifier for the hash algorithm used to hash the assembly files.</span></span>  
  
 `szName`  
 <span data-ttu-id="08334-110">[v] Čitelný text název sestavení.</span><span class="sxs-lookup"><span data-stu-id="08334-110">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="08334-111">[v] Ukazatel na assemblymetadata –, který obsahuje informace o verzi, platformy a národní prostředí pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="08334-111">[in] A pointer to the ASSEMBLYMETADATA that contains version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="08334-112">[v] Bitovou kombinaci [AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md) hodnoty, které určují různé atributy sestavení.</span><span class="sxs-lookup"><span data-stu-id="08334-112">[in] A bitwise combination of [AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md) values that specify various attributes of the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08334-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="08334-113">Remarks</span></span>  
 <span data-ttu-id="08334-114">Chcete-li vytvořit `Assembly` strukturu metadat, použijte [imetadataassemblyemit::defineassembly –](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="08334-114">To create an `Assembly` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssembly](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08334-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="08334-115">Requirements</span></span>  
 <span data-ttu-id="08334-116">**Platforma:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08334-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08334-117">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="08334-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="08334-118">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="08334-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="08334-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08334-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08334-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="08334-120">See Also</span></span>  
 [<span data-ttu-id="08334-121">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="08334-121">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
