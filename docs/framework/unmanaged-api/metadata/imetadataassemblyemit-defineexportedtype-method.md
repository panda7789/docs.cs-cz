---
title: "IMetaDataAssemblyEmit::DefineExportedType – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataAssemblyEmit.DefineExportedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineExportedType
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineExportedType method [.NET Framework metadata]
- DefineExportedType method [.NET Framework metadata]
ms.assetid: fad01d7a-3178-4c8c-9f0a-4641e3701c9b
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 59aae188e404ebc717a140fb7918e3fbf69f3f70
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a><span data-ttu-id="6e5d7-102">IMetaDataAssemblyEmit::DefineExportedType – metoda</span><span class="sxs-lookup"><span data-stu-id="6e5d7-102">IMetaDataAssemblyEmit::DefineExportedType Method</span></span>
<span data-ttu-id="6e5d7-103">Vytvoří `ExportedType` struktura obsahující metadata pro zadaný typ exportovat a vrátí token přidružených metadat.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-103">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e5d7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e5d7-104">Syntax</span></span>  
  
```  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,   
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6e5d7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6e5d7-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="6e5d7-106">[v] Název typu export.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-106">[in] The name of type to be exported.</span></span> <span data-ttu-id="6e5d7-107">Pro verze 1.1 modul common language runtime, název typu exportovaný musí přesně shodovat s názvem uvedenému v `TypeDef` typu.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-107">For version 1.1 of the common language runtime, the name of the exported type must exactly match the name given in the `TypeDef` for the type.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="6e5d7-108">[v] Token určující, kde je implementováno exportovaný typu.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-108">[in] A token specifying where the exported type is implemented.</span></span> <span data-ttu-id="6e5d7-109">Platné hodnoty a jejich přidružené význam jsou:</span><span class="sxs-lookup"><span data-stu-id="6e5d7-109">The valid values and their associated meanings are:</span></span>  
  
-   <span data-ttu-id="6e5d7-110">`mdFile`Typ je implementována v jiném souboru v rámci této položky assembly.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-110">`mdFile` The type is implemented in a different file within this assembly.</span></span>  
  
-   <span data-ttu-id="6e5d7-111">`mdAssemblyRef`Typ je implementovaná v jiném sestavení.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-111">`mdAssemblyRef` The type is implemented in a different assembly.</span></span>  
  
-   <span data-ttu-id="6e5d7-112">`mdExportedTYpe`Typ vnořen v rámci některého jiného typu.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-112">`mdExportedTYpe` The type is nested within some other type.</span></span>  
  
-   <span data-ttu-id="6e5d7-113">`mdFileNil`Typ je ve stejném souboru jako manifest a není typu vnořené.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-113">`mdFileNil` The type is in the same file as the manifest and is not a nested type.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="6e5d7-114">[v] Token pro metadata, která určuje typ export.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-114">[in] A token to the metadata that specifies the type to be exported.</span></span> <span data-ttu-id="6e5d7-115">Tato hodnota je zadána v `TypeDef` tabulky v souboru, který implementuje typu a se týkají jenom v případě, že soubor je v tomto sestavení.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-115">This value is entered in the `TypeDef` table in the file that implements the type and is relevant only if that file is in this assembly.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="6e5d7-116">[v] Bitovou kombinaci [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) hodnot výčtu, které definují nastavení vlastností pro exportovaný typu.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-116">[in] A bitwise combination of [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeration values that define the property settings for the exported type.</span></span>  
  
 `pmdct`  
 <span data-ttu-id="6e5d7-117">[out] Ukazatel na token vrácený metadata, který určuje typ exportovaný.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-117">[out] A pointer to the returned metadata token that indicates the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e5d7-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6e5d7-118">Remarks</span></span>  
 <span data-ttu-id="6e5d7-119">`ExportedType` Pro každý typ, který je zveřejněný prostřednictvím toto sestavení a která je implementovaná v modulu než obsahující manifest musí být definován strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-119">An `ExportedType` metadata structure must be defined for each type that is exposed by this assembly and that is implemented in a module other than the one containing the manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e5d7-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6e5d7-120">Requirements</span></span>  
 <span data-ttu-id="6e5d7-121">**Platforma:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e5d7-121">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e5d7-122">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6e5d7-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6e5d7-123">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6e5d7-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6e5d7-124">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e5d7-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e5d7-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="6e5d7-125">See Also</span></span>  
 [<span data-ttu-id="6e5d7-126">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6e5d7-126">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
