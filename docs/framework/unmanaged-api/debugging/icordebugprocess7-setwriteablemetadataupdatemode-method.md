---
title: ICorDebugProcess7::SetWriteableMetadataUpdateMode – metoda
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugProcess7.SetWriteableMetadataUpdateMode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 8589bba7-7304-45ba-9e31-7bf43dfd5c19
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a67f93a3f3f75b89bc3f0240995471bc0bf44992
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419754"
---
# <a name="icordebugprocess7setwriteablemetadataupdatemode-method"></a><span data-ttu-id="0f9dc-102">ICorDebugProcess7::SetWriteableMetadataUpdateMode – metoda</span><span class="sxs-lookup"><span data-stu-id="0f9dc-102">ICorDebugProcess7::SetWriteableMetadataUpdateMode Method</span></span>
<span data-ttu-id="0f9dc-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="0f9dc-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="0f9dc-104">Konfiguruje, jak ladicí program zpracovává v paměti aktualizace metadat v rámci tento cílový proces.</span><span class="sxs-lookup"><span data-stu-id="0f9dc-104">Configures how the debugger handles in-memory updates to metadata within the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f9dc-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f9dc-105">Syntax</span></span>  
  
```cpp
HRESULT SetWriteableMetadataUpdateMode(  
   WriteableMetadataUpdateMode flags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0f9dc-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0f9dc-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="0f9dc-107">A [WriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md) hodnota výčtu, která určuje, zda jsou viditelné v paměti aktualizace metadat v tento cílový proces (`WriteableMetadataUpdateMode::AlwaysShowUpdates`) nebo nejsou viditelné (`WriteableMetadataUpdateMode::LegacyCompatPolicy`) pro ladicí program.</span><span class="sxs-lookup"><span data-stu-id="0f9dc-107">A [WriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md) enumeration value that specifies whether in-memory updates to metadata in the target process are visible (`WriteableMetadataUpdateMode::AlwaysShowUpdates`) or not visible (`WriteableMetadataUpdateMode::LegacyCompatPolicy`) to the debugger.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f9dc-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0f9dc-108">Remarks</span></span>  
 <span data-ttu-id="0f9dc-109">Aktualizace k metadatům tento cílový proces mohou pocházet z upravit a pokračovat, profileru, nebo <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0f9dc-109">Updates to the metadata of the target process can come from Edit and Continue, a profiler, or <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f9dc-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0f9dc-110">Requirements</span></span>  
 <span data-ttu-id="0f9dc-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f9dc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f9dc-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0f9dc-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0f9dc-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0f9dc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f9dc-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f9dc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f9dc-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="0f9dc-115">See Also</span></span>  
 [<span data-ttu-id="0f9dc-116">ICorDebugProcess7 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0f9dc-116">ICorDebugProcess7 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-interface.md)  
 [<span data-ttu-id="0f9dc-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="0f9dc-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
