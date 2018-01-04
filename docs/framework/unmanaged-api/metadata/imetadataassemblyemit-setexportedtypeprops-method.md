---
title: "IMetaDataAssemblyEmit::SetExportedTypeProps – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.SetExportedTypeProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::SetExportedTypeProps
helpviewer_keywords:
- SetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 1c090153-fd5f-46c7-9cff-39a78d992c8f
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bebcf827488912431cb0f94f5527d3445fc41125
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemitsetexportedtypeprops-method"></a><span data-ttu-id="dd457-102">IMetaDataAssemblyEmit::SetExportedTypeProps – metoda</span><span class="sxs-lookup"><span data-stu-id="dd457-102">IMetaDataAssemblyEmit::SetExportedTypeProps Method</span></span>
<span data-ttu-id="dd457-103">Upraví zadaný `ExportedType` strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="dd457-103">Modifies the specified `ExportedType` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd457-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dd457-104">Syntax</span></span>  
  
```  
HRESULT SetExportedTypeProps (  
    [in] mdExportedType   ct,   
    [in] mdToken          tkImplementation,  
    [in] mdTypeDef        tkTypeDef,  
    [in] DWORD            dwExportedTypeFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dd457-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dd457-105">Parameters</span></span>  
 `ct`  
 <span data-ttu-id="dd457-106">[v] Metadata token, který určuje `ExportedType` strukturu metadat má být změněn.</span><span class="sxs-lookup"><span data-stu-id="dd457-106">[in] The metadata token that specifies the `ExportedType` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="dd457-107">[v] Token, typu `File`, `AssemblyRef`, nebo `ExportedType`, který určuje, jak je implementována tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="dd457-107">[in] The token, of type `File`, `AssemblyRef`, or `ExportedType`, that specifies how this type is implemented.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="dd457-108">[v] `TypeDef` Token v souboru kódu odkazovat.</span><span class="sxs-lookup"><span data-stu-id="dd457-108">[in] The `TypeDef` token referenced in the code file.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="dd457-109">[v] Bitová kombinace hodnot, které určují atributy typu.</span><span class="sxs-lookup"><span data-stu-id="dd457-109">[in] A bitwise combination of values that specify attributes of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd457-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dd457-110">Remarks</span></span>  
 <span data-ttu-id="dd457-111">Chcete-li vytvořit `ExportedType` strukturu metadat, použijte [imetadataassemblyemit::defineexportedtype –](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="dd457-111">To create an `ExportedType` metadata structure, use the [IMetaDataAssemblyEmit::DefineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd457-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dd457-112">Requirements</span></span>  
 <span data-ttu-id="dd457-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd457-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd457-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dd457-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dd457-115">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dd457-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dd457-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd457-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd457-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="dd457-117">See Also</span></span>  
 [<span data-ttu-id="dd457-118">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dd457-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
