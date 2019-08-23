---
title: 'ICorDebugMergedAssemblyRecord:: getssdp – metoda'
ms.date: 03/30/2017
ms.assetid: bc3410f6-ebca-4bca-9b45-fc38c74fa9cb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f3256a1a50b66be74561bfc992380669a4495dde
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939988"
---
# <a name="icordebugmergedassemblyrecordgetsimplename-method"></a><span data-ttu-id="aad49-102">ICorDebugMergedAssemblyRecord:: getssdp – metoda</span><span class="sxs-lookup"><span data-stu-id="aad49-102">ICorDebugMergedAssemblyRecord::GetSimpleName Method</span></span>
<span data-ttu-id="aad49-103">Získá jednoduchý název sestavení.</span><span class="sxs-lookup"><span data-stu-id="aad49-103">Gets the simple name of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aad49-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aad49-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSimpleName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aad49-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aad49-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="aad49-106">pro Počet znaků ve `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="aad49-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="aad49-107">mimo Ukazatel na počet znaků skutečně zapsaných do `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="aad49-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="aad49-108">Ukazatel na pole znaků.</span><span class="sxs-lookup"><span data-stu-id="aad49-108">A pointer to a character array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aad49-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aad49-109">Remarks</span></span>  
 <span data-ttu-id="aad49-110">Tato metoda načte jednoduchý název sestavení (například System. Collections) bez přípony souboru, verze, jazykové verze nebo tokenu veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="aad49-110">This method retrieves the simple name of an assembly (such as "System.Collections"), without a file extension, version, culture, or public key token.</span></span> <span data-ttu-id="aad49-111">Odpovídá <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> vlastnosti ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="aad49-111">It corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property in managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aad49-112">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="aad49-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aad49-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aad49-113">Requirements</span></span>  
 <span data-ttu-id="aad49-114">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aad49-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aad49-115">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="aad49-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aad49-116">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aad49-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aad49-117">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aad49-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aad49-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aad49-118">See also</span></span>

- [<span data-ttu-id="aad49-119">ICorDebugMergedAssemblyRecord – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aad49-119">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="aad49-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="aad49-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
