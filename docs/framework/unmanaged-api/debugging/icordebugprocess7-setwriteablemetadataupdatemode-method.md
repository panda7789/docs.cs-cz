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
ms.openlocfilehash: 70d8f5bf23b5cdf0714bfbb8c8571f9412ad7115
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487278"
---
# <a name="icordebugprocess7setwriteablemetadataupdatemode-method"></a><span data-ttu-id="865e7-102">ICorDebugProcess7::SetWriteableMetadataUpdateMode – metoda</span><span class="sxs-lookup"><span data-stu-id="865e7-102">ICorDebugProcess7::SetWriteableMetadataUpdateMode Method</span></span>
<span data-ttu-id="865e7-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="865e7-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="865e7-104">Nakonfiguruje, zpracování v paměti aktualizace metadata v rámci cílového procesu ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="865e7-104">Configures how the debugger handles in-memory updates to metadata within the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="865e7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="865e7-105">Syntax</span></span>  
  
```cpp
HRESULT SetWriteableMetadataUpdateMode(  
   WriteableMetadataUpdateMode flags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="865e7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="865e7-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="865e7-107">A [WriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md) hodnota výčtu, která určuje, zda jsou viditelné v paměti aktualizace metadat v cílovém procesu (`WriteableMetadataUpdateMode::AlwaysShowUpdates`) nebo nejsou viditelné (`WriteableMetadataUpdateMode::LegacyCompatPolicy`) v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="865e7-107">A [WriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md) enumeration value that specifies whether in-memory updates to metadata in the target process are visible (`WriteableMetadataUpdateMode::AlwaysShowUpdates`) or not visible (`WriteableMetadataUpdateMode::LegacyCompatPolicy`) to the debugger.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="865e7-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="865e7-108">Remarks</span></span>  
 <span data-ttu-id="865e7-109">Aktualizace metadat cílového procesu můžou pocházet z funkce upravit a pokračovat, profiler, nebo <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="865e7-109">Updates to the metadata of the target process can come from Edit and Continue, a profiler, or <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="865e7-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="865e7-110">Requirements</span></span>  
 <span data-ttu-id="865e7-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="865e7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="865e7-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="865e7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="865e7-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="865e7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="865e7-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="865e7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="865e7-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="865e7-115">See also</span></span>
- [<span data-ttu-id="865e7-116">ICorDebugProcess7 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="865e7-116">ICorDebugProcess7 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-interface.md)
- [<span data-ttu-id="865e7-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="865e7-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
