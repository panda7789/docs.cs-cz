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
ms.openlocfilehash: 35767529d9433764b7eed0b3b4acdd806f399962
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792184"
---
# <a name="icordebugprocess7setwriteablemetadataupdatemode-method"></a><span data-ttu-id="e625d-102">ICorDebugProcess7::SetWriteableMetadataUpdateMode – metoda</span><span class="sxs-lookup"><span data-stu-id="e625d-102">ICorDebugProcess7::SetWriteableMetadataUpdateMode Method</span></span>
<span data-ttu-id="e625d-103">[Podporované v .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="e625d-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="e625d-104">Konfiguruje, jak ladicí program zpracovává aktualizace v paměti na metadata v rámci cílového procesu.</span><span class="sxs-lookup"><span data-stu-id="e625d-104">Configures how the debugger handles in-memory updates to metadata within the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e625d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e625d-105">Syntax</span></span>  
  
```cpp
HRESULT SetWriteableMetadataUpdateMode(  
   WriteableMetadataUpdateMode flags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e625d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e625d-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="e625d-107">Hodnota výčtu [WriteableMetadataUpdateMode](writeablemetadataupdatemode-enumeration.md) , která určuje, zda jsou aktualizace metadat v paměti v cílovém procesu viditelné (`WriteableMetadataUpdateMode::AlwaysShowUpdates`) nebo nejsou viditelné (`WriteableMetadataUpdateMode::LegacyCompatPolicy`) do ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="e625d-107">A [WriteableMetadataUpdateMode](writeablemetadataupdatemode-enumeration.md) enumeration value that specifies whether in-memory updates to metadata in the target process are visible (`WriteableMetadataUpdateMode::AlwaysShowUpdates`) or not visible (`WriteableMetadataUpdateMode::LegacyCompatPolicy`) to the debugger.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e625d-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e625d-108">Remarks</span></span>  
 <span data-ttu-id="e625d-109">Aktualizace metadat cílového procesu můžou pocházet z části Upravit a pokračovat, profileru nebo <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e625d-109">Updates to the metadata of the target process can come from Edit and Continue, a profiler, or <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e625d-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e625d-110">Requirements</span></span>  
 <span data-ttu-id="e625d-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e625d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e625d-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e625d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e625d-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e625d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e625d-114">**Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e625d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e625d-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e625d-115">See also</span></span>

- [<span data-ttu-id="e625d-116">ICorDebugProcess7 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e625d-116">ICorDebugProcess7 Interface</span></span>](icordebugprocess7-interface.md)
- [<span data-ttu-id="e625d-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="e625d-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
