---
title: "ICorDebugProcess7::SetWriteableMetadataUpdateMode – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugProcess7.SetWriteableMetadataUpdateMode
api_location: mscordbi.dll
api_type: COM
ms.assetid: 8589bba7-7304-45ba-9e31-7bf43dfd5c19
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 635792962e259f181a1ff3e0c46438951e4223db
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess7setwriteablemetadataupdatemode-method"></a><span data-ttu-id="17e58-102">ICorDebugProcess7::SetWriteableMetadataUpdateMode – metoda</span><span class="sxs-lookup"><span data-stu-id="17e58-102">ICorDebugProcess7::SetWriteableMetadataUpdateMode Method</span></span>
<span data-ttu-id="17e58-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="17e58-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="17e58-104">Konfiguruje, jak ladicí program zpracovává v paměti aktualizace metadat v rámci tento cílový proces.</span><span class="sxs-lookup"><span data-stu-id="17e58-104">Configures how the debugger handles in-memory updates to metadata within the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17e58-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17e58-105">Syntax</span></span>  
  
```cpp
HRESULT SetWriteableMetadataUpdateMode(  
   WriteableMetadataUpdateMode flags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="17e58-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="17e58-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="17e58-107">A [WriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md) hodnota výčtu, která určuje, zda jsou viditelné v paměti aktualizace metadat v tento cílový proces (`WriteableMetadataUpdateMode::AlwaysShowUpdates`) nebo nejsou viditelné (`WriteableMetadataUpdateMode::LegacyCompatPolicy`) pro ladicí program.</span><span class="sxs-lookup"><span data-stu-id="17e58-107">A [WriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md) enumeration value that specifies whether in-memory updates to metadata in the target process are visible (`WriteableMetadataUpdateMode::AlwaysShowUpdates`) or not visible (`WriteableMetadataUpdateMode::LegacyCompatPolicy`) to the debugger.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17e58-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="17e58-108">Remarks</span></span>  
 <span data-ttu-id="17e58-109">Aktualizace k metadatům tento cílový proces mohou pocházet z upravit a pokračovat, profileru, nebo <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="17e58-109">Updates to the metadata of the target process can come from Edit and Continue, a profiler, or <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17e58-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="17e58-110">Requirements</span></span>  
 <span data-ttu-id="17e58-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17e58-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17e58-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="17e58-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="17e58-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17e58-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17e58-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17e58-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17e58-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="17e58-115">See Also</span></span>  
 [<span data-ttu-id="17e58-116">Rozhraní ICorDebugProcess7</span><span class="sxs-lookup"><span data-stu-id="17e58-116">ICorDebugProcess7 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-interface.md)  
 [<span data-ttu-id="17e58-117">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="17e58-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
