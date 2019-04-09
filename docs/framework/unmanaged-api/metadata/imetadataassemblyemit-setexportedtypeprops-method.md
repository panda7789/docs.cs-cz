---
title: IMetaDataAssemblyEmit::SetExportedTypeProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetExportedTypeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetExportedTypeProps
helpviewer_keywords:
- SetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 1c090153-fd5f-46c7-9cff-39a78d992c8f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5c09140488730179616d11932faa3542f704958a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59123738"
---
# <a name="imetadataassemblyemitsetexportedtypeprops-method"></a><span data-ttu-id="958ad-102">IMetaDataAssemblyEmit::SetExportedTypeProps – metoda</span><span class="sxs-lookup"><span data-stu-id="958ad-102">IMetaDataAssemblyEmit::SetExportedTypeProps Method</span></span>
<span data-ttu-id="958ad-103">Upraví zadaný `ExportedType` struktury metadat.</span><span class="sxs-lookup"><span data-stu-id="958ad-103">Modifies the specified `ExportedType` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="958ad-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="958ad-104">Syntax</span></span>  
  
```  
HRESULT SetExportedTypeProps (  
    [in] mdExportedType   ct,   
    [in] mdToken          tkImplementation,  
    [in] mdTypeDef        tkTypeDef,  
    [in] DWORD            dwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="958ad-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="958ad-105">Parameters</span></span>  
 `ct`  
 <span data-ttu-id="958ad-106">[in] Token metadat, který určuje `ExportedType` struktury metadat má být upraven.</span><span class="sxs-lookup"><span data-stu-id="958ad-106">[in] The metadata token that specifies the `ExportedType` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="958ad-107">[in] Token typu `File`, `AssemblyRef`, nebo `ExportedType`, která určuje, jak je implementovaná tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="958ad-107">[in] The token, of type `File`, `AssemblyRef`, or `ExportedType`, that specifies how this type is implemented.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="958ad-108">[in] `TypeDef` Token popsána v souboru kódu.</span><span class="sxs-lookup"><span data-stu-id="958ad-108">[in] The `TypeDef` token referenced in the code file.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="958ad-109">[in] Bitová kombinace hodnot, které určují atributy typu.</span><span class="sxs-lookup"><span data-stu-id="958ad-109">[in] A bitwise combination of values that specify attributes of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="958ad-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="958ad-110">Remarks</span></span>  
 <span data-ttu-id="958ad-111">K vytvoření `ExportedType` struktury metadat, použijte [imetadataassemblyemit::defineexportedtype –](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="958ad-111">To create an `ExportedType` metadata structure, use the [IMetaDataAssemblyEmit::DefineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="958ad-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="958ad-112">Requirements</span></span>  
 <span data-ttu-id="958ad-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="958ad-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="958ad-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="958ad-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="958ad-115">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="958ad-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="958ad-116">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="958ad-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="958ad-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="958ad-117">See also</span></span>

- [<span data-ttu-id="958ad-118">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="958ad-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
