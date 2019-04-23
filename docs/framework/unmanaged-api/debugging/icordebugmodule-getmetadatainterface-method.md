---
title: ICorDebugModule::GetMetaDataInterface – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetMetaDataInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetMetaDataInterface
helpviewer_keywords:
- ICorDebugModule::GetMetaDatainterface method [.NET Framework debugging]
- GetMetaDatainterface method [.NET Framework debugging]
ms.assetid: 30d906f2-cf35-4fa9-9d4c-0c31b58c9f3a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 37710fbb7acc50b80d7acebe4194b019c0b64660
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59102593"
---
# <a name="icordebugmodulegetmetadatainterface-method"></a><span data-ttu-id="558cd-102">ICorDebugModule::GetMetaDataInterface – metoda</span><span class="sxs-lookup"><span data-stu-id="558cd-102">ICorDebugModule::GetMetaDataInterface Method</span></span>
<span data-ttu-id="558cd-103">Získá objekt rozhraní metadat, který slouží k přezkoumání metadat pro modul.</span><span class="sxs-lookup"><span data-stu-id="558cd-103">Gets a metadata interface object that can be used to examine the metadata for the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="558cd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="558cd-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataInterface (  
    [in] REFIID      riid,  
    [out] IUnknown **ppObj  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="558cd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="558cd-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="558cd-106">[in] ID odkazu, který určuje rozhraní metadat.</span><span class="sxs-lookup"><span data-stu-id="558cd-106">[in] The reference ID that specifies the metadata interface.</span></span>  
  
 `ppObj`  
 <span data-ttu-id="558cd-107">[out] Ukazatel na adresu `T:IUnknown` objekt, který je součástí [rozhraní metadat](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="558cd-107">[out] A pointer to the address of an `T:IUnknown` object that is one of the [metadata interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="558cd-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="558cd-108">Remarks</span></span>  
 <span data-ttu-id="558cd-109">Ladicí program můžete použít `GetMetaDataInterface` metoda vytvořit kopii původní metadata pro některý z modulů, které musíte udělat aby bylo možné upravit tento modul.</span><span class="sxs-lookup"><span data-stu-id="558cd-109">The debugger can use the `GetMetaDataInterface` method to make a copy of the original metadata for a module, which it must do in order to edit that module.</span></span> <span data-ttu-id="558cd-110">Ladicí program volání `GetMetaDataInterface` získat [imetadataemit –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) objektu rozhraní modulu, pak zavolá [imetadataemit::savetomemory –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md) uložte kopii metadata modulu do paměti.</span><span class="sxs-lookup"><span data-stu-id="558cd-110">The debugger calls `GetMetaDataInterface` to get an [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface object for the module, then calls [IMetaDataEmit::SaveToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md) to save a copy of the module's metadata to memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="558cd-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="558cd-111">Requirements</span></span>  
 <span data-ttu-id="558cd-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="558cd-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="558cd-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="558cd-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="558cd-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="558cd-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="558cd-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="558cd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="558cd-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="558cd-116">See also</span></span>

- [<span data-ttu-id="558cd-117">Metadata</span><span class="sxs-lookup"><span data-stu-id="558cd-117">Metadata</span></span>](../../../../docs/framework/unmanaged-api/metadata/index.md)
