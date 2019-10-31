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
ms.openlocfilehash: c324019e1e62701f4f2aaba1c00948b292ba6847
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127915"
---
# <a name="icordebugmodule2applychanges-method"></a><span data-ttu-id="4cac8-102">ICorDebugModule2::ApplyChanges – metoda</span><span class="sxs-lookup"><span data-stu-id="4cac8-102">ICorDebugModule2::ApplyChanges Method</span></span>
<span data-ttu-id="4cac8-103">Aplikuje změny v metadatech a změny v kódu jazyka MSIL (Microsoft Intermediate Language) na běžící proces.</span><span class="sxs-lookup"><span data-stu-id="4cac8-103">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cac8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4cac8-104">Syntax</span></span>  
  
```cpp  
HRESULT ApplyChanges (  
    [in] ULONG                       cbMetadata,  
    [in, size_is(cbMetadata)] BYTE   pbMetadata[],  
    [in] ULONG                       cbIL,  
    [in, size_is(cbIL)] BYTE         pbIL[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4cac8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4cac8-105">Parameters</span></span>  
 `cbMetadata`  
 <span data-ttu-id="4cac8-106">pro Velikost rozdílových metadat v bajtech.</span><span class="sxs-lookup"><span data-stu-id="4cac8-106">[in] Size, in bytes, of the delta metadata.</span></span>  
  
 `pbMetadata`  
 <span data-ttu-id="4cac8-107">pro Vyrovnávací paměť obsahující rozdílová metadata</span><span class="sxs-lookup"><span data-stu-id="4cac8-107">[in] Buffer that contains the delta metadata.</span></span> <span data-ttu-id="4cac8-108">Adresa vyrovnávací paměti se vrátí z metody [IMetaDataEmit2:: SaveDeltaToMemory –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4cac8-108">The address of the buffer is returned from the [IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md) method.</span></span>  
  
 <span data-ttu-id="4cac8-109">Relativní virtuální adresy (RVA) v metadatech by měly být relativní vzhledem ke spuštění kódu jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="4cac8-109">The relative virtual addresses (RVAs) in the metadata should be relative to the start of the MSIL code.</span></span>  
  
 `cbIL`  
 <span data-ttu-id="4cac8-110">pro Velikost rozdílového kódu jazyka MSIL v bajtech.</span><span class="sxs-lookup"><span data-stu-id="4cac8-110">[in] Size, in bytes, of the delta MSIL code.</span></span>  
  
 `pbIL`  
 <span data-ttu-id="4cac8-111">pro Vyrovnávací paměť obsahující aktualizovaný kód jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="4cac8-111">[in] Buffer that contains the updated MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4cac8-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4cac8-112">Remarks</span></span>  
 <span data-ttu-id="4cac8-113">Parametr `pbMetadata` je ve speciálním formátu rozdílové metadat (jako výstup pomocí [IMetaDataEmit2:: SaveDeltaToMemory –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)).</span><span class="sxs-lookup"><span data-stu-id="4cac8-113">The `pbMetadata` parameter is in a special delta metadata format (as output by [IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)).</span></span> <span data-ttu-id="4cac8-114">`pbMetadata` přebírá předchozí metadata jako základní a popisuje jednotlivé změny, které se vztahují k tomuto základu.</span><span class="sxs-lookup"><span data-stu-id="4cac8-114">`pbMetadata` takes previous metadata as a base and describes individual changes to apply to that base.</span></span>  
  
 <span data-ttu-id="4cac8-115">Naproti tomu parametr `pbIL[`] obsahuje nový jazyk MSIL pro aktualizovanou metodu a je určen k úplnému nahrazení předchozího jazyka MSIL pro danou metodu.</span><span class="sxs-lookup"><span data-stu-id="4cac8-115">In contrast, the `pbIL[`] parameter contains the new MSIL for the updated method, and is meant to completely replace the previous MSIL for that method</span></span>  
  
 <span data-ttu-id="4cac8-116">Při vytvoření rozdílového jazyka MSIL a metadat v paměti ladicího programu volá ladicí program `ApplyChanges` k odeslání změn do modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="4cac8-116">When the delta MSIL and the metadata have been created in the debugger’s memory, the debugger calls `ApplyChanges` to send the changes into the common language runtime (CLR).</span></span> <span data-ttu-id="4cac8-117">Modul runtime aktualizuje své tabulky metadat, umístí nový jazyk MSIL do procesu a nastaví kompilaci JIT (just-in-time) nového jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="4cac8-117">The runtime updates its metadata tables, places the new MSIL into the process, and sets up a just-in-time (JIT) compilation of the new MSIL.</span></span> <span data-ttu-id="4cac8-118">Po použití změn by ladicí program měl zavolat [IMetaDataEmit2:: ResetENCLog –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md) , aby se připravil k další relaci úprav.</span><span class="sxs-lookup"><span data-stu-id="4cac8-118">When the changes have been applied, the debugger should call [IMetaDataEmit2::ResetENCLog](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md) to prepare for the next editing session.</span></span> <span data-ttu-id="4cac8-119">Ladicí program může pokračovat v procesu.</span><span class="sxs-lookup"><span data-stu-id="4cac8-119">The debugger may then continue the process.</span></span>  
  
 <span data-ttu-id="4cac8-120">Pokaždé, když ladicí program volá `ApplyChanges` v modulu, který má rozdílová metadata, měla by také volat [IMetaDataEmit:: ApplyEditAndContinue –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md) se stejnými rozdílovou metadaty na všech svých kopiích tohoto modulu, s výjimkou kopie použité k vygenerování změn.</span><span class="sxs-lookup"><span data-stu-id="4cac8-120">Whenever the debugger calls `ApplyChanges` on a module that has delta metadata, it should also call [IMetaDataEmit::ApplyEditAndContinue](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md) with the same delta metadata on all of its copies of that module’s metadata except for the copy used to emit the changes.</span></span> <span data-ttu-id="4cac8-121">Pokud se kopie metadat nějakým způsobem nesynchronizuje se skutečnými metadaty, ladicí program může vždycky vyvolat kopírování a získat novou kopii.</span><span class="sxs-lookup"><span data-stu-id="4cac8-121">If a copy of the metadata somehow becomes out-of-sync with the actual metadata, the debugger can always throw away that copy and obtain a new copy.</span></span>  
  
 <span data-ttu-id="4cac8-122">Pokud se metoda `ApplyChanges` nezdařila, relace ladění je v neplatném stavu a je nutné ji restartovat.</span><span class="sxs-lookup"><span data-stu-id="4cac8-122">If the `ApplyChanges` method fails, the debug session is in an invalid state and must be restarted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4cac8-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4cac8-123">Requirements</span></span>  
 <span data-ttu-id="4cac8-124">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4cac8-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4cac8-125">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4cac8-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4cac8-126">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4cac8-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4cac8-127">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4cac8-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
