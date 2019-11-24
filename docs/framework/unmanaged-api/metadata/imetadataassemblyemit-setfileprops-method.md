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
ms.openlocfilehash: 106ffeee521f69a73628b1fb6a611abc733583f9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431869"
---
# <a name="imetadataassemblyemitsetfileprops-method"></a><span data-ttu-id="03251-102">IMetaDataAssemblyEmit::SetFileProps – metoda</span><span class="sxs-lookup"><span data-stu-id="03251-102">IMetaDataAssemblyEmit::SetFileProps Method</span></span>
<span data-ttu-id="03251-103">Modifies the specified `File` metadata structure.</span><span class="sxs-lookup"><span data-stu-id="03251-103">Modifies the specified `File` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03251-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03251-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFileProps (  
    [in] mdFile        file,  
    [in] const void    *pbHashValue,   
    [in] ULONG         cbHashValue,  
    [in] DWORD         dwFileFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03251-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="03251-105">Parameters</span></span>  
 `file`  
 <span data-ttu-id="03251-106">[in] The metadata token that specifies the `File` metadata structure to be modified.</span><span class="sxs-lookup"><span data-stu-id="03251-106">[in] The metadata token that specifies the `File` metadata structure to be modified.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="03251-107">[in] A pointer to the hash data associated with the file.</span><span class="sxs-lookup"><span data-stu-id="03251-107">[in] A pointer to the hash data associated with the file.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="03251-108">[in] The size in bytes of `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="03251-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="03251-109">[in] A bitwise combination of [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) values that specify various attributes of the file.</span><span class="sxs-lookup"><span data-stu-id="03251-109">[in] A bitwise combination of [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) values that specify various attributes of the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03251-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="03251-110">Remarks</span></span>  
 <span data-ttu-id="03251-111">To create a `File` metadata structure, use the [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md) method.</span><span class="sxs-lookup"><span data-stu-id="03251-111">To create a `File` metadata structure, use the [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03251-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="03251-112">Requirements</span></span>  
 <span data-ttu-id="03251-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03251-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03251-114">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="03251-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="03251-115">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="03251-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="03251-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03251-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03251-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="03251-117">See also</span></span>

- [<span data-ttu-id="03251-118">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="03251-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
