---
title: ICorDebugModule2::ApplyChanges – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.ApplyChanges
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::ApplyChanges
helpviewer_keywords:
- ApplyChanges method [.NET Framework debugging]
- ICorDebugModule2::ApplyChanges method [.NET Framework debugging]
ms.assetid: 96fa3406-6a6f-41a1-88c6-d9bc5d1a16d1
topic_type:
- apiref
ms.openlocfilehash: 99824e9a7fd759fb30bfa377156fc28eb934a2b4
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212214"
---
# <a name="icordebugmodule2applychanges-method"></a><span data-ttu-id="4b8a1-102">ICorDebugModule2::ApplyChanges – metoda</span><span class="sxs-lookup"><span data-stu-id="4b8a1-102">ICorDebugModule2::ApplyChanges Method</span></span>
<span data-ttu-id="4b8a1-103">Aplikuje změny v metadatech a změny v kódu jazyka MSIL (Microsoft Intermediate Language) na běžící proces.</span><span class="sxs-lookup"><span data-stu-id="4b8a1-103">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b8a1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b8a1-104">Syntax</span></span>  
  
```cpp  
HRESULT ApplyChanges (  
    [in] ULONG                       cbMetadata,  
    [in, size_is(cbMetadata)] BYTE   pbMetadata[],  
    [in] ULONG                       cbIL,  
    [in, size_is(cbIL)] BYTE         pbIL[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b8a1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4b8a1-105">Parameters</span></span>  
 `cbMetadata`  
 <span data-ttu-id="4b8a1-106">pro Velikost rozdílových metadat v bajtech.</span><span class="sxs-lookup"><span data-stu-id="4b8a1-106">[in] Size, in bytes, of the delta metadata.</span></span>  
  
 `pbMetadata`  
 <span data-ttu-id="4b8a1-107">pro Vyrovnávací paměť obsahující rozdílová metadata</span><span class="sxs-lookup"><span data-stu-id="4b8a1-107">[in] Buffer that contains the delta metadata.</span></span> <span data-ttu-id="4b8a1-108">Adresa vyrovnávací paměti se vrátí z metody [IMetaDataEmit2:: SaveDeltaToMemory –](../metadata/imetadataemit2-savedeltatomemory-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4b8a1-108">The address of the buffer is returned from the [IMetaDataEmit2::SaveDeltaToMemory](../metadata/imetadataemit2-savedeltatomemory-method.md) method.</span></span>  
  
 <span data-ttu-id="4b8a1-109">Relativní virtuální adresy (RVA) v metadatech by měly být relativní vzhledem ke spuštění kódu jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="4b8a1-109">The relative virtual addresses (RVAs) in the metadata should be relative to the start of the MSIL code.</span></span>  
  
 `cbIL`  
 <span data-ttu-id="4b8a1-110">pro Velikost rozdílového kódu jazyka MSIL v bajtech.</span><span class="sxs-lookup"><span data-stu-id="4b8a1-110">[in] Size, in bytes, of the delta MSIL code.</span></span>  
  
 `pbIL`  
 <span data-ttu-id="4b8a1-111">pro Vyrovnávací paměť obsahující aktualizovaný kód jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="4b8a1-111">[in] Buffer that contains the updated MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b8a1-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4b8a1-112">Remarks</span></span>  
 <span data-ttu-id="4b8a1-113">`pbMetadata`Parametr je ve speciálním formátu rozdílové metadat (jako výstup pomocí [IMetaDataEmit2:: SaveDeltaToMemory –](../metadata/imetadataemit2-savedeltatomemory-method.md)).</span><span class="sxs-lookup"><span data-stu-id="4b8a1-113">The `pbMetadata` parameter is in a special delta metadata format (as output by [IMetaDataEmit2::SaveDeltaToMemory](../metadata/imetadataemit2-savedeltatomemory-method.md)).</span></span> <span data-ttu-id="4b8a1-114">`pbMetadata`bere předchozí metadata jako základní a popisuje jednotlivé změny, které se vztahují k tomuto základu.</span><span class="sxs-lookup"><span data-stu-id="4b8a1-114">`pbMetadata` takes previous metadata as a base and describes individual changes to apply to that base.</span></span>  
  
 <span data-ttu-id="4b8a1-115">Naproti tomu `pbIL[` parametr] obsahuje nový jazyk MSIL pro aktualizovanou metodu a je určen k úplnému nahrazení předchozího jazyka MSIL pro danou metodu.</span><span class="sxs-lookup"><span data-stu-id="4b8a1-115">In contrast, the `pbIL[`] parameter contains the new MSIL for the updated method, and is meant to completely replace the previous MSIL for that method</span></span>  
  
 <span data-ttu-id="4b8a1-116">Když se rozdílové rozhraní MSIL a metadata v paměti ladicího programu vytvoří, ladicí program zavolá `ApplyChanges` k odeslání změn do modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="4b8a1-116">When the delta MSIL and the metadata have been created in the debugger’s memory, the debugger calls `ApplyChanges` to send the changes into the common language runtime (CLR).</span></span> <span data-ttu-id="4b8a1-117">Modul runtime aktualizuje své tabulky metadat, umístí nový jazyk MSIL do procesu a nastaví kompilaci JIT (just-in-time) nového jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="4b8a1-117">The runtime updates its metadata tables, places the new MSIL into the process, and sets up a just-in-time (JIT) compilation of the new MSIL.</span></span> <span data-ttu-id="4b8a1-118">Po použití změn by ladicí program měl zavolat [IMetaDataEmit2:: ResetENCLog –](../metadata/imetadataemit2-resetenclog-method.md) , aby se připravil k další relaci úprav.</span><span class="sxs-lookup"><span data-stu-id="4b8a1-118">When the changes have been applied, the debugger should call [IMetaDataEmit2::ResetENCLog](../metadata/imetadataemit2-resetenclog-method.md) to prepare for the next editing session.</span></span> <span data-ttu-id="4b8a1-119">Ladicí program může pokračovat v procesu.</span><span class="sxs-lookup"><span data-stu-id="4b8a1-119">The debugger may then continue the process.</span></span>  
  
 <span data-ttu-id="4b8a1-120">Vždy, když ladicí program volá `ApplyChanges` modul, který má rozdílová metadata, by měl také volat [IMetaDataEmit:: ApplyEditAndContinue –](../metadata/imetadataemit-applyeditandcontinue-method.md) se stejnými rozdílová metadata na všech svých kopiích tohoto modulu, s výjimkou kopie použité k vygenerování změn.</span><span class="sxs-lookup"><span data-stu-id="4b8a1-120">Whenever the debugger calls `ApplyChanges` on a module that has delta metadata, it should also call [IMetaDataEmit::ApplyEditAndContinue](../metadata/imetadataemit-applyeditandcontinue-method.md) with the same delta metadata on all of its copies of that module’s metadata except for the copy used to emit the changes.</span></span> <span data-ttu-id="4b8a1-121">Pokud se kopie metadat nějakým způsobem nesynchronizuje se skutečnými metadaty, ladicí program může vždycky vyvolat kopírování a získat novou kopii.</span><span class="sxs-lookup"><span data-stu-id="4b8a1-121">If a copy of the metadata somehow becomes out-of-sync with the actual metadata, the debugger can always throw away that copy and obtain a new copy.</span></span>  
  
 <span data-ttu-id="4b8a1-122">Pokud se `ApplyChanges` Metoda nezdařila, ladicí relace je v neplatném stavu a je nutné ji restartovat.</span><span class="sxs-lookup"><span data-stu-id="4b8a1-122">If the `ApplyChanges` method fails, the debug session is in an invalid state and must be restarted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b8a1-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4b8a1-123">Requirements</span></span>  
 <span data-ttu-id="4b8a1-124">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b8a1-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b8a1-125">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4b8a1-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4b8a1-126">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4b8a1-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b8a1-127">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b8a1-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
