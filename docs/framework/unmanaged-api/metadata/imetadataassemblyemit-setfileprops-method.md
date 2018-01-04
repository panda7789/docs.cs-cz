---
title: "IMetaDataAssemblyEmit::SetFileProps – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.SetFileProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::SetFileProps
helpviewer_keywords:
- IMetaDataAssemblyEmit::SetFileProps method [.NET Framework metadata]
- SetFileProps method [.NET Framework metadata]
ms.assetid: 85667d38-611c-45a9-938d-930ac7a7b681
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bc0f0b2cbc22a7e9d6dcac6e359f36f365d368af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemitsetfileprops-method"></a><span data-ttu-id="8fffe-102">IMetaDataAssemblyEmit::SetFileProps – metoda</span><span class="sxs-lookup"><span data-stu-id="8fffe-102">IMetaDataAssemblyEmit::SetFileProps Method</span></span>
<span data-ttu-id="8fffe-103">Upraví zadaný `File` strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="8fffe-103">Modifies the specified `File` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fffe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8fffe-104">Syntax</span></span>  
  
```  
HRESULT SetFileProps (  
    [in] mdFile        file,  
    [in] const void    *pbHashValue,   
    [in] ULONG         cbHashValue,  
    [in] DWORD         dwFileFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8fffe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8fffe-105">Parameters</span></span>  
 `file`  
 <span data-ttu-id="8fffe-106">[v] Metadata token, který určuje `File` strukturu metadat má být změněn.</span><span class="sxs-lookup"><span data-stu-id="8fffe-106">[in] The metadata token that specifies the `File` metadata structure to be modified.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="8fffe-107">[v] Ukazatel na hodnotu hash dat přidružené k souboru.</span><span class="sxs-lookup"><span data-stu-id="8fffe-107">[in] A pointer to the hash data associated with the file.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="8fffe-108">[v] Velikost v bajtech `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="8fffe-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="8fffe-109">[v] Bitovou kombinaci [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) hodnoty, které určují různé atributy souboru.</span><span class="sxs-lookup"><span data-stu-id="8fffe-109">[in] A bitwise combination of [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) values that specify various attributes of the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8fffe-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8fffe-110">Remarks</span></span>  
 <span data-ttu-id="8fffe-111">Chcete-li vytvořit `File` strukturu metadat, použijte [imetadataassemblyemit::definefile –](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="8fffe-111">To create a `File` metadata structure, use the [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fffe-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8fffe-112">Requirements</span></span>  
 <span data-ttu-id="8fffe-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fffe-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fffe-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8fffe-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8fffe-115">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8fffe-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8fffe-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fffe-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fffe-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="8fffe-117">See Also</span></span>  
 [<span data-ttu-id="8fffe-118">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8fffe-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
