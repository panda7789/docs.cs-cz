---
title: IMetaDataAssemblyEmit::DefineExportedType – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 984eef16ff576d63a445b199eba8c2364285f62e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57483866"
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a><span data-ttu-id="eeedc-102">IMetaDataAssemblyEmit::DefineExportedType – metoda</span><span class="sxs-lookup"><span data-stu-id="eeedc-102">IMetaDataAssemblyEmit::DefineExportedType Method</span></span>
<span data-ttu-id="eeedc-103">Vytvoří `ExportedType` struktura obsahující metadata pro zadanou exportovat typ a vrátí token metadat.</span><span class="sxs-lookup"><span data-stu-id="eeedc-103">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eeedc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eeedc-104">Syntax</span></span>  
  
```  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,   
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eeedc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eeedc-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="eeedc-106">[in] Název typu nelze exportovat.</span><span class="sxs-lookup"><span data-stu-id="eeedc-106">[in] The name of type to be exported.</span></span> <span data-ttu-id="eeedc-107">Pro verze 1.1 modul common language runtime, název typu exportované musí přesně shodovat s názvem podle `TypeDef` typu.</span><span class="sxs-lookup"><span data-stu-id="eeedc-107">For version 1.1 of the common language runtime, the name of the exported type must exactly match the name given in the `TypeDef` for the type.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="eeedc-108">[in] Token určující, kde se exportovaný typ implementuje.</span><span class="sxs-lookup"><span data-stu-id="eeedc-108">[in] A token specifying where the exported type is implemented.</span></span> <span data-ttu-id="eeedc-109">Platné hodnoty a jejich přidružené vysvětlení jsou:</span><span class="sxs-lookup"><span data-stu-id="eeedc-109">The valid values and their associated meanings are:</span></span>  
  
-   <span data-ttu-id="eeedc-110">`mdFile` Typ je implementována do jiného souboru v rámci tohoto sestavení.</span><span class="sxs-lookup"><span data-stu-id="eeedc-110">`mdFile` The type is implemented in a different file within this assembly.</span></span>  
  
-   <span data-ttu-id="eeedc-111">`mdAssemblyRef` Typ je implementované v jiném sestavení.</span><span class="sxs-lookup"><span data-stu-id="eeedc-111">`mdAssemblyRef` The type is implemented in a different assembly.</span></span>  
  
-   <span data-ttu-id="eeedc-112">`mdExportedTYpe` Typ je vnořená v rámci některého jiného typu.</span><span class="sxs-lookup"><span data-stu-id="eeedc-112">`mdExportedTYpe` The type is nested within some other type.</span></span>  
  
-   <span data-ttu-id="eeedc-113">`mdFileNil` Typ je ve stejném souboru jako manifest a není vnořeného typu.</span><span class="sxs-lookup"><span data-stu-id="eeedc-113">`mdFileNil` The type is in the same file as the manifest and is not a nested type.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="eeedc-114">[in] Token pro metadata, která určuje typ, který chcete exportovat.</span><span class="sxs-lookup"><span data-stu-id="eeedc-114">[in] A token to the metadata that specifies the type to be exported.</span></span> <span data-ttu-id="eeedc-115">Tato hodnota se zadá v `TypeDef` tabulky v souboru, který implementuje typ a je relevantní pouze v případě, že tento soubor je v tomto sestavení.</span><span class="sxs-lookup"><span data-stu-id="eeedc-115">This value is entered in the `TypeDef` table in the file that implements the type and is relevant only if that file is in this assembly.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="eeedc-116">[in] Bitová kombinace hodnot [cortypeattr –](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) hodnot výčtu, která definují nastavení vlastností pro exportovaný typ.</span><span class="sxs-lookup"><span data-stu-id="eeedc-116">[in] A bitwise combination of [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeration values that define the property settings for the exported type.</span></span>  
  
 `pmdct`  
 <span data-ttu-id="eeedc-117">[out] Ukazatel na token vrácených metadat, který určuje exportovaný typ.</span><span class="sxs-lookup"><span data-stu-id="eeedc-117">[out] A pointer to the returned metadata token that indicates the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eeedc-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eeedc-118">Remarks</span></span>  
 <span data-ttu-id="eeedc-119">`ExportedType` Struktury metadat musí být definované pro každý typ, který je zveřejněný prostřednictvím tohoto sestavení a je implementována v modulu než ten, který obsahuje manifest.</span><span class="sxs-lookup"><span data-stu-id="eeedc-119">An `ExportedType` metadata structure must be defined for each type that is exposed by this assembly and that is implemented in a module other than the one containing the manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eeedc-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eeedc-120">Requirements</span></span>  
 <span data-ttu-id="eeedc-121">**Platforma:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eeedc-121">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eeedc-122">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="eeedc-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="eeedc-123">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="eeedc-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="eeedc-124">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eeedc-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eeedc-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eeedc-125">See also</span></span>
- [<span data-ttu-id="eeedc-126">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eeedc-126">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
