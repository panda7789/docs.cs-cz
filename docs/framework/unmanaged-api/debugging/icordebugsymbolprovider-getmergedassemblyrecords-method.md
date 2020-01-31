---
title: 'ICorDebugSymbolProvider:: GetMergedAssemblyRecords – metoda'
ms.date: 03/30/2017
ms.assetid: cc4c510d-550d-4941-af34-81987caf3425
ms.openlocfilehash: 6a537a88bd4ab666eff8b5dda994da96bfcc5e52
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791615"
---
# <a name="icordebugsymbolprovidergetmergedassemblyrecords-method"></a><span data-ttu-id="86d28-102">ICorDebugSymbolProvider:: GetMergedAssemblyRecords – metoda</span><span class="sxs-lookup"><span data-stu-id="86d28-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords Method</span></span>
<span data-ttu-id="86d28-103">Získá záznamy symbolů pro všechna Sloučená sestavení.</span><span class="sxs-lookup"><span data-stu-id="86d28-103">Gets the symbol records for all the merged assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86d28-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86d28-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMergedAssemblyRecords(  
   [in] ULONG32 cRequestedRecords,  
   [out] ULONG32 *pcFetchedRecords,  
   [out, size_is(cRequestedRecords), length_is(*pcFetchedRecords)] ICorDebugMergedAssemblyRecord *pRecords[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86d28-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="86d28-105">Parameters</span></span>  
 `cRequestedRecords`  
 <span data-ttu-id="86d28-106">pro Počet vyžádaných záznamů symbolů.</span><span class="sxs-lookup"><span data-stu-id="86d28-106">[in] The number of symbol records requested.</span></span>  
  
 `pcFetchedRecords`  
 <span data-ttu-id="86d28-107">mimo Ukazatel na počet záznamů symbolů načtených metodou.</span><span class="sxs-lookup"><span data-stu-id="86d28-107">[out] A pointer to the number of symbol records retrieved by the method.</span></span>  
  
 `pRecords`  
 <span data-ttu-id="86d28-108">Ukazatel na pole objektů [ICorDebugMergedAssemblyRecord](icordebugmergedassemblyrecord-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="86d28-108">A pointer to an array of [ICorDebugMergedAssemblyRecord](icordebugmergedassemblyrecord-interface.md) objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86d28-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="86d28-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="86d28-110">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="86d28-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86d28-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="86d28-111">Requirements</span></span>  
 <span data-ttu-id="86d28-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86d28-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86d28-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="86d28-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86d28-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="86d28-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86d28-115">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86d28-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86d28-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="86d28-116">See also</span></span>

- [<span data-ttu-id="86d28-117">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="86d28-117">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="86d28-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="86d28-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
