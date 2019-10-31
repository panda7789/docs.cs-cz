---
title: 'ICorDebugMergedAssemblyRecord:: getssdp – metoda'
ms.date: 03/30/2017
ms.assetid: bc3410f6-ebca-4bca-9b45-fc38c74fa9cb
ms.openlocfilehash: 565e27b47f2454dec1e4c2b89ee46ac5279b08b7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130553"
---
# <a name="icordebugmergedassemblyrecordgetsimplename-method"></a><span data-ttu-id="4cdfb-102">ICorDebugMergedAssemblyRecord:: getssdp – metoda</span><span class="sxs-lookup"><span data-stu-id="4cdfb-102">ICorDebugMergedAssemblyRecord::GetSimpleName Method</span></span>
<span data-ttu-id="4cdfb-103">Získá jednoduchý název sestavení.</span><span class="sxs-lookup"><span data-stu-id="4cdfb-103">Gets the simple name of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cdfb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4cdfb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSimpleName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4cdfb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4cdfb-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="4cdfb-106">pro Počet znaků ve vyrovnávací paměti `szName`.</span><span class="sxs-lookup"><span data-stu-id="4cdfb-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="4cdfb-107">mimo Ukazatel na počet znaků skutečně zapsaných do vyrovnávací paměti `szName`.</span><span class="sxs-lookup"><span data-stu-id="4cdfb-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="4cdfb-108">Ukazatel na pole znaků.</span><span class="sxs-lookup"><span data-stu-id="4cdfb-108">A pointer to a character array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4cdfb-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4cdfb-109">Remarks</span></span>  
 <span data-ttu-id="4cdfb-110">Tato metoda načte jednoduchý název sestavení (například System. Collections) bez přípony souboru, verze, jazykové verze nebo tokenu veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="4cdfb-110">This method retrieves the simple name of an assembly (such as "System.Collections"), without a file extension, version, culture, or public key token.</span></span> <span data-ttu-id="4cdfb-111">Odpovídá vlastnosti <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="4cdfb-111">It corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property in managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4cdfb-112">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4cdfb-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4cdfb-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4cdfb-113">Requirements</span></span>  
 <span data-ttu-id="4cdfb-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4cdfb-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4cdfb-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4cdfb-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4cdfb-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4cdfb-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4cdfb-117">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4cdfb-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cdfb-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4cdfb-118">See also</span></span>

- [<span data-ttu-id="4cdfb-119">ICorDebugMergedAssemblyRecord – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4cdfb-119">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="4cdfb-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="4cdfb-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
