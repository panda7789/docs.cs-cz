---
title: ICorDebugProcess::WriteMemory – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.WriteMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::WriteMemory
helpviewer_keywords:
- ICorDebugProcess::WriteMemory method [.NET Framework debugging]
- WriteMemory method [.NET Framework debugging]
ms.assetid: d5c07d86-045d-4391-893b-0bcd2959f90e
topic_type:
- apiref
ms.openlocfilehash: 0a433ccb81ef62ac92a4553a838a2c98a04fc7c1
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212812"
---
# <a name="icordebugprocesswritememory-method"></a><span data-ttu-id="1cde7-102">ICorDebugProcess::WriteMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="1cde7-102">ICorDebugProcess::WriteMemory Method</span></span>
<span data-ttu-id="1cde7-103">Zapisuje data do oblasti paměti v tomto procesu.</span><span class="sxs-lookup"><span data-stu-id="1cde7-103">Writes data to an area of memory in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cde7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1cde7-104">Syntax</span></span>  
  
```cpp  
HRESULT WriteMemory(  
    [in]  CORDB_ADDRESS address,  
    [in]  DWORD size,  
    [in, size_is(size)] BYTE buffer[],  
    [out] SIZE_T *written);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1cde7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1cde7-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="1cde7-106">pro `CORDB_ADDRESS`Hodnota, která je základní adresou oblasti paměti, do které se zapisují data.</span><span class="sxs-lookup"><span data-stu-id="1cde7-106">[in] A `CORDB_ADDRESS` value that is the base address of the memory area to which data is written.</span></span> <span data-ttu-id="1cde7-107">Než dojde k přenosu dat, systém ověří, že oblast paměti zadané velikosti, která začíná na základní adrese, je přístupná pro zápis.</span><span class="sxs-lookup"><span data-stu-id="1cde7-107">Before data transfer occurs, the system verifies that the memory area of the specified size, beginning at the base address, is accessible for writing.</span></span> <span data-ttu-id="1cde7-108">Pokud není k dispozici, metoda se nezdařila.</span><span class="sxs-lookup"><span data-stu-id="1cde7-108">If it is not accessible, the method fails.</span></span>  
  
 `size`  
 <span data-ttu-id="1cde7-109">pro Počet bajtů, které mají být zapsány do oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="1cde7-109">[in] The number of bytes to be written to the memory area.</span></span>  
  
 `buffer`  
 <span data-ttu-id="1cde7-110">pro Vyrovnávací paměť obsahující data, která mají být zapsána.</span><span class="sxs-lookup"><span data-stu-id="1cde7-110">[in] A buffer that contains data to be written.</span></span>  
  
 `written`  
 <span data-ttu-id="1cde7-111">mimo Ukazatel na proměnnou, která přijímá počet bajtů zapsaných do oblasti paměti v tomto procesu.</span><span class="sxs-lookup"><span data-stu-id="1cde7-111">[out] A pointer to a variable that receives the number of bytes written to the memory area in this process.</span></span> <span data-ttu-id="1cde7-112">Pokud `written` má hodnotu null, tento parametr je ignorován.</span><span class="sxs-lookup"><span data-stu-id="1cde7-112">If `written` is NULL, this parameter is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1cde7-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1cde7-113">Remarks</span></span>  
 <span data-ttu-id="1cde7-114">Data se automaticky zapisují za všechny zarážky.</span><span class="sxs-lookup"><span data-stu-id="1cde7-114">Data is automatically written behind any breakpoints.</span></span> <span data-ttu-id="1cde7-115">V .NET Framework verze 2,0 by nativní ladicí program neměl tuto metodu použít pro vložení zarážek do datového proudu instrukcí.</span><span class="sxs-lookup"><span data-stu-id="1cde7-115">In the .NET Framework version 2.0, native debuggers should not use this method to inject breakpoints into the instruction stream.</span></span> <span data-ttu-id="1cde7-116">Místo toho použijte [ICorDebugProcess2:: SetUnmanagedBreakpoint –](icordebugprocess2-setunmanagedbreakpoint-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1cde7-116">Use [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md) instead.</span></span>  
  
 <span data-ttu-id="1cde7-117">`WriteMemory`Metoda by měla být použita pouze mimo spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="1cde7-117">The `WriteMemory` method should be used only outside of managed code.</span></span> <span data-ttu-id="1cde7-118">Tato metoda může poškodit modul runtime, pokud je použit nesprávně.</span><span class="sxs-lookup"><span data-stu-id="1cde7-118">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1cde7-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1cde7-119">Requirements</span></span>  
 <span data-ttu-id="1cde7-120">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1cde7-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1cde7-121">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1cde7-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1cde7-122">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1cde7-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1cde7-123">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1cde7-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
