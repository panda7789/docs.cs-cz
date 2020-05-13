---
title: 'ICorDebugSymbolProvider:: GetMergedAssemblyRecords – metoda'
ms.date: 03/30/2017
ms.assetid: cc4c510d-550d-4941-af34-81987caf3425
ms.openlocfilehash: b7d26fa80a7a8ebe7b4606b914c8cd09c52df1e4
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379625"
---
# <a name="icordebugsymbolprovidergetmergedassemblyrecords-method"></a><span data-ttu-id="301a1-102">ICorDebugSymbolProvider:: GetMergedAssemblyRecords – metoda</span><span class="sxs-lookup"><span data-stu-id="301a1-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords Method</span></span>
<span data-ttu-id="301a1-103">Získá záznamy symbolů pro všechna Sloučená sestavení.</span><span class="sxs-lookup"><span data-stu-id="301a1-103">Gets the symbol records for all the merged assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="301a1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="301a1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMergedAssemblyRecords(  
   [in] ULONG32 cRequestedRecords,  
   [out] ULONG32 *pcFetchedRecords,  
   [out, size_is(cRequestedRecords), length_is(*pcFetchedRecords)] ICorDebugMergedAssemblyRecord *pRecords[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="301a1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="301a1-105">Parameters</span></span>  
 `cRequestedRecords`  
 <span data-ttu-id="301a1-106">pro Počet vyžádaných záznamů symbolů.</span><span class="sxs-lookup"><span data-stu-id="301a1-106">[in] The number of symbol records requested.</span></span>  
  
 `pcFetchedRecords`  
 <span data-ttu-id="301a1-107">mimo Ukazatel na počet záznamů symbolů načtených metodou.</span><span class="sxs-lookup"><span data-stu-id="301a1-107">[out] A pointer to the number of symbol records retrieved by the method.</span></span>  
  
 `pRecords`  
 <span data-ttu-id="301a1-108">Ukazatel na pole objektů [ICorDebugMergedAssemblyRecord](icordebugmergedassemblyrecord-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="301a1-108">A pointer to an array of [ICorDebugMergedAssemblyRecord](icordebugmergedassemblyrecord-interface.md) objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="301a1-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="301a1-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="301a1-110">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="301a1-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="301a1-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="301a1-111">Requirements</span></span>  
 <span data-ttu-id="301a1-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="301a1-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="301a1-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="301a1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="301a1-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="301a1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="301a1-115">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="301a1-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="301a1-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="301a1-116">See also</span></span>

- [<span data-ttu-id="301a1-117">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="301a1-117">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="301a1-118">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="301a1-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
