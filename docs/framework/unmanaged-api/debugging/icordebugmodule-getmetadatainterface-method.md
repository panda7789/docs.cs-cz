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
ms.openlocfilehash: f5d0dd7a99087b21a5f827e4dce0f6342ae7b25a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501765"
---
# <a name="icordebugmodulegetmetadatainterface-method"></a><span data-ttu-id="59bca-102">ICorDebugModule::GetMetaDataInterface – metoda</span><span class="sxs-lookup"><span data-stu-id="59bca-102">ICorDebugModule::GetMetaDataInterface Method</span></span>
<span data-ttu-id="59bca-103">Získá objekt rozhraní metadat, který lze použít k prohlédnutí metadat pro modul.</span><span class="sxs-lookup"><span data-stu-id="59bca-103">Gets a metadata interface object that can be used to examine the metadata for the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59bca-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59bca-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataInterface (  
    [in] REFIID      riid,  
    [out] IUnknown **ppObj  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="59bca-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="59bca-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="59bca-106">pro Referenční ID, které určuje rozhraní metadat.</span><span class="sxs-lookup"><span data-stu-id="59bca-106">[in] The reference ID that specifies the metadata interface.</span></span>  
  
 `ppObj`  
 <span data-ttu-id="59bca-107">mimo Ukazatel na adresu `T:IUnknown` objektu, který je jedním z [rozhraní metadat](../metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="59bca-107">[out] A pointer to the address of an `T:IUnknown` object that is one of the [metadata interfaces](../metadata/metadata-interfaces.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59bca-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="59bca-108">Remarks</span></span>  
 <span data-ttu-id="59bca-109">Ladicí program může použít `GetMetaDataInterface` metodu k vytvoření kopie původních metadat pro modul, který musí provést, aby bylo možné tento modul upravit.</span><span class="sxs-lookup"><span data-stu-id="59bca-109">The debugger can use the `GetMetaDataInterface` method to make a copy of the original metadata for a module, which it must do in order to edit that module.</span></span> <span data-ttu-id="59bca-110">Ladicí program volá `GetMetaDataInterface` k získání objektu rozhraní [IMetaDataEmit](../metadata/imetadataemit-interface.md) pro modul a pak zavolá [IMetaDataEmit:: SaveToMemory –](../metadata/imetadataemit-savetomemory-method.md) , aby uložil kopii metadat modulu do paměti.</span><span class="sxs-lookup"><span data-stu-id="59bca-110">The debugger calls `GetMetaDataInterface` to get an [IMetaDataEmit](../metadata/imetadataemit-interface.md) interface object for the module, then calls [IMetaDataEmit::SaveToMemory](../metadata/imetadataemit-savetomemory-method.md) to save a copy of the module's metadata to memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59bca-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="59bca-111">Requirements</span></span>  
 <span data-ttu-id="59bca-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59bca-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59bca-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="59bca-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="59bca-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="59bca-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59bca-115">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59bca-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59bca-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="59bca-116">See also</span></span>

- [<span data-ttu-id="59bca-117">Metadata</span><span class="sxs-lookup"><span data-stu-id="59bca-117">Metadata</span></span>](../metadata/index.md)
