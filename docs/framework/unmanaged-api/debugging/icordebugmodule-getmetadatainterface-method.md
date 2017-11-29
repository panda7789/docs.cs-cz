---
title: "ICorDebugModule::GetMetaDataInterface – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.GetMetaDataInterface
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::GetMetaDataInterface
helpviewer_keywords:
- ICorDebugModule::GetMetaDatainterface method [.NET Framework debugging]
- GetMetaDatainterface method [.NET Framework debugging]
ms.assetid: 30d906f2-cf35-4fa9-9d4c-0c31b58c9f3a
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f4b1944c68db0cbdd8eb49e10433defc953e4494
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodulegetmetadatainterface-method"></a><span data-ttu-id="996c0-102">ICorDebugModule::GetMetaDataInterface – metoda</span><span class="sxs-lookup"><span data-stu-id="996c0-102">ICorDebugModule::GetMetaDataInterface Method</span></span>
<span data-ttu-id="996c0-103">Získá objekt rozhraní metadat, který můžete použít k prozkoumání metadata pro modul.</span><span class="sxs-lookup"><span data-stu-id="996c0-103">Gets a metadata interface object that can be used to examine the metadata for the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="996c0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="996c0-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataInterface (  
    [in] REFIID      riid,  
    [out] IUnknown **ppObj  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="996c0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="996c0-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="996c0-106">[v] ID odkazu, který určuje rozhraní metadat.</span><span class="sxs-lookup"><span data-stu-id="996c0-106">[in] The reference ID that specifies the metadata interface.</span></span>  
  
 `ppObj`  
 <span data-ttu-id="996c0-107">[out] Ukazatel na adresu `T:IUnknown` objekt, který je jedním z [rozhraní metadat](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="996c0-107">[out] A pointer to the address of an `T:IUnknown` object that is one of the [metadata interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="996c0-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="996c0-108">Remarks</span></span>  
 <span data-ttu-id="996c0-109">Ladicí program můžete použít `GetMetaDataInterface` metoda vytvořit kopii původní metadata pro modul, který musí to, aby bylo možné upravit tento modul.</span><span class="sxs-lookup"><span data-stu-id="996c0-109">The debugger can use the `GetMetaDataInterface` method to make a copy of the original metadata for a module, which it must do in order to edit that module.</span></span> <span data-ttu-id="996c0-110">Ladicí program volání `GetMetaDataInterface` získat [imetadataemit –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) rozhraní objektu pro modul, pak zavolá [imetadataemit::savetomemory –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md) pro uložení kopie metadat modulu do paměti.</span><span class="sxs-lookup"><span data-stu-id="996c0-110">The debugger calls `GetMetaDataInterface` to get an [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface object for the module, then calls [IMetaDataEmit::SaveToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md) to save a copy of the module's metadata to memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="996c0-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="996c0-111">Requirements</span></span>  
 <span data-ttu-id="996c0-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="996c0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="996c0-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="996c0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="996c0-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="996c0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="996c0-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="996c0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="996c0-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="996c0-116">See Also</span></span>  
 [<span data-ttu-id="996c0-117">Metadata</span><span class="sxs-lookup"><span data-stu-id="996c0-117">Metadata</span></span>](../../../../docs/framework/unmanaged-api/metadata/index.md)
