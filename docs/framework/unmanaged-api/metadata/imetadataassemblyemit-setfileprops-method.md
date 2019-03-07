---
title: IMetaDataAssemblyEmit::SetFileProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetFileProps
helpviewer_keywords:
- IMetaDataAssemblyEmit::SetFileProps method [.NET Framework metadata]
- SetFileProps method [.NET Framework metadata]
ms.assetid: 85667d38-611c-45a9-938d-930ac7a7b681
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a04162a870833ff409c93527733e2380d9c3eed2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474731"
---
# <a name="imetadataassemblyemitsetfileprops-method"></a><span data-ttu-id="f037e-102">IMetaDataAssemblyEmit::SetFileProps – metoda</span><span class="sxs-lookup"><span data-stu-id="f037e-102">IMetaDataAssemblyEmit::SetFileProps Method</span></span>
<span data-ttu-id="f037e-103">Upraví zadaný `File` struktury metadat.</span><span class="sxs-lookup"><span data-stu-id="f037e-103">Modifies the specified `File` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f037e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f037e-104">Syntax</span></span>  
  
```  
HRESULT SetFileProps (  
    [in] mdFile        file,  
    [in] const void    *pbHashValue,   
    [in] ULONG         cbHashValue,  
    [in] DWORD         dwFileFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f037e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f037e-105">Parameters</span></span>  
 `file`  
 <span data-ttu-id="f037e-106">[in] Token metadat, který určuje `File` struktury metadat má být upraven.</span><span class="sxs-lookup"><span data-stu-id="f037e-106">[in] The metadata token that specifies the `File` metadata structure to be modified.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="f037e-107">[in] Ukazatel na hodnotu hash dat přidružené k souboru.</span><span class="sxs-lookup"><span data-stu-id="f037e-107">[in] A pointer to the hash data associated with the file.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="f037e-108">[in] Velikost v bajtech `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="f037e-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="f037e-109">[in] Bitová kombinace hodnot [corfileflags –](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) hodnoty, které určují různé atributy souboru.</span><span class="sxs-lookup"><span data-stu-id="f037e-109">[in] A bitwise combination of [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) values that specify various attributes of the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f037e-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f037e-110">Remarks</span></span>  
 <span data-ttu-id="f037e-111">Vytvoření `File` struktury metadat, použijte [imetadataassemblyemit::definefile –](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="f037e-111">To create a `File` metadata structure, use the [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f037e-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f037e-112">Requirements</span></span>  
 <span data-ttu-id="f037e-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f037e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f037e-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f037e-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f037e-115">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f037e-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f037e-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f037e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f037e-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f037e-117">See also</span></span>
- [<span data-ttu-id="f037e-118">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f037e-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
