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
ms.openlocfilehash: fb96949e22b4edfc0e64780a54bb38da44eb8369
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129550"
---
# <a name="icordebugmodulegetmetadatainterface-method"></a><span data-ttu-id="bc9ef-102">ICorDebugModule::GetMetaDataInterface – metoda</span><span class="sxs-lookup"><span data-stu-id="bc9ef-102">ICorDebugModule::GetMetaDataInterface Method</span></span>
<span data-ttu-id="bc9ef-103">Získá objekt rozhraní metadat, který lze použít k prohlédnutí metadat pro modul.</span><span class="sxs-lookup"><span data-stu-id="bc9ef-103">Gets a metadata interface object that can be used to examine the metadata for the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc9ef-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bc9ef-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataInterface (  
    [in] REFIID      riid,  
    [out] IUnknown **ppObj  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc9ef-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bc9ef-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="bc9ef-106">pro Referenční ID, které určuje rozhraní metadat.</span><span class="sxs-lookup"><span data-stu-id="bc9ef-106">[in] The reference ID that specifies the metadata interface.</span></span>  
  
 `ppObj`  
 <span data-ttu-id="bc9ef-107">mimo Ukazatel na adresu `T:IUnknown` objektu, který je jedním z [rozhraní metadat](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="bc9ef-107">[out] A pointer to the address of an `T:IUnknown` object that is one of the [metadata interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc9ef-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bc9ef-108">Remarks</span></span>  
 <span data-ttu-id="bc9ef-109">Ladicí program může pomocí metody `GetMetaDataInterface` vytvořit kopii původních metadat pro modul, který musí provést, aby bylo možné tento modul upravit.</span><span class="sxs-lookup"><span data-stu-id="bc9ef-109">The debugger can use the `GetMetaDataInterface` method to make a copy of the original metadata for a module, which it must do in order to edit that module.</span></span> <span data-ttu-id="bc9ef-110">Ladicí program volá `GetMetaDataInterface` pro získání objektu rozhraní [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) pro modul, volá [IMetaDataEmit:: SaveToMemory –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md) , aby uložil kopii metadat modulu do paměti.</span><span class="sxs-lookup"><span data-stu-id="bc9ef-110">The debugger calls `GetMetaDataInterface` to get an [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface object for the module, then calls [IMetaDataEmit::SaveToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md) to save a copy of the module's metadata to memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc9ef-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bc9ef-111">Requirements</span></span>  
 <span data-ttu-id="bc9ef-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc9ef-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc9ef-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bc9ef-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bc9ef-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="bc9ef-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc9ef-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc9ef-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc9ef-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bc9ef-116">See also</span></span>

- [<span data-ttu-id="bc9ef-117">Metadata</span><span class="sxs-lookup"><span data-stu-id="bc9ef-117">Metadata</span></span>](../../../../docs/framework/unmanaged-api/metadata/index.md)
