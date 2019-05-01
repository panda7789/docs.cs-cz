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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab0e28bd21b66f370a1a1e82359fe474574fd7bb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987958"
---
# <a name="icordebugmodule2applychanges-method"></a><span data-ttu-id="8440e-102">ICorDebugModule2::ApplyChanges – metoda</span><span class="sxs-lookup"><span data-stu-id="8440e-102">ICorDebugModule2::ApplyChanges Method</span></span>
<span data-ttu-id="8440e-103">Změny v metadatech a změny v kódu Microsoft intermediate language (MSIL) se vztahuje na běžící proces.</span><span class="sxs-lookup"><span data-stu-id="8440e-103">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8440e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8440e-104">Syntax</span></span>  
  
```  
HRESULT ApplyChanges (  
    [in] ULONG                       cbMetadata,  
    [in, size_is(cbMetadata)] BYTE   pbMetadata[],  
    [in] ULONG                       cbIL,  
    [in, size_is(cbIL)] BYTE         pbIL[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8440e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8440e-105">Parameters</span></span>  
 `cbMetadata`  
 <span data-ttu-id="8440e-106">[in] Velikost v bajtech, rozdílové metadat.</span><span class="sxs-lookup"><span data-stu-id="8440e-106">[in] Size, in bytes, of the delta metadata.</span></span>  
  
 `pbMetadata`  
 <span data-ttu-id="8440e-107">[in] Vyrovnávací paměť, která obsahuje delta metadata.</span><span class="sxs-lookup"><span data-stu-id="8440e-107">[in] Buffer that contains the delta metadata.</span></span> <span data-ttu-id="8440e-108">Adresa vyrovnávací paměti je vrácen z [imetadataemit2::savedeltatomemory –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="8440e-108">The address of the buffer is returned from the [IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md) method.</span></span>  
  
 <span data-ttu-id="8440e-109">Relativních virtuálních adres (RVA) v metadatech by měla být relativní vzhledem k začátku kód jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="8440e-109">The relative virtual addresses (RVAs) in the metadata should be relative to the start of the MSIL code.</span></span>  
  
 `cbIL`  
 <span data-ttu-id="8440e-110">[in] Velikost v bajtech, rozdílových kód jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="8440e-110">[in] Size, in bytes, of the delta MSIL code.</span></span>  
  
 `pbIL`  
 <span data-ttu-id="8440e-111">[in] Vyrovnávací paměť, která obsahuje aktualizovaný kód jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="8440e-111">[in] Buffer that contains the updated MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8440e-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8440e-112">Remarks</span></span>  
 <span data-ttu-id="8440e-113">`pbMetadata` Parametr má formát metadat speciální delta (jako výstupní podle [imetadataemit2::savedeltatomemory –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)).</span><span class="sxs-lookup"><span data-stu-id="8440e-113">The `pbMetadata` parameter is in a special delta metadata format (as output by [IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)).</span></span> <span data-ttu-id="8440e-114">`pbMetadata` má předchozí metadat jako základ a popisuje jednotlivé změny se můžou použít k této základní třídě.</span><span class="sxs-lookup"><span data-stu-id="8440e-114">`pbMetadata` takes previous metadata as a base and describes individual changes to apply to that base.</span></span>  
  
 <span data-ttu-id="8440e-115">Oproti tomu, `pbIL[`] parametr obsahuje nový jazyk MSIL pro metodu aktualizované a slouží k úplnému nahrazení předchozí MSIL pro metody</span><span class="sxs-lookup"><span data-stu-id="8440e-115">In contrast, the `pbIL[`] parameter contains the new MSIL for the updated method, and is meant to completely replace the previous MSIL for that method</span></span>  
  
 <span data-ttu-id="8440e-116">Při rozdílové jazyk MSIL a metadata byly vytvořeny v paměti ladicího programu, ladicí program volá `ApplyChanges` k odeslání změn do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="8440e-116">When the delta MSIL and the metadata have been created in the debugger’s memory, the debugger calls `ApplyChanges` to send the changes into the common language runtime (CLR).</span></span> <span data-ttu-id="8440e-117">Modul runtime aktualizuje její tabulky metadat, umístí nový jazyk MSIL do procesu a nastaví just-in-time (JIT) kompilaci nového MSIL.</span><span class="sxs-lookup"><span data-stu-id="8440e-117">The runtime updates its metadata tables, places the new MSIL into the process, and sets up a just-in-time (JIT) compilation of the new MSIL.</span></span> <span data-ttu-id="8440e-118">Když změny se použily, ladicí program by měly volat [imetadataemit2::resetenclog –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md) připravit pro další relaci.</span><span class="sxs-lookup"><span data-stu-id="8440e-118">When the changes have been applied, the debugger should call [IMetaDataEmit2::ResetENCLog](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md) to prepare for the next editing session.</span></span> <span data-ttu-id="8440e-119">Ladicí program může potom pokračujte v procesu.</span><span class="sxs-lookup"><span data-stu-id="8440e-119">The debugger may then continue the process.</span></span>  
  
 <span data-ttu-id="8440e-120">Vždy, když ladicí program volá `ApplyChanges` na modul, který má delta metadata, měla by také zavolat [imetadataemit::applyeditandcontinue –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md) s na stejná metadata delta ve všech jeho kopie metadat tohoto modulu s výjimkou kopie použít ke generování změny.</span><span class="sxs-lookup"><span data-stu-id="8440e-120">Whenever the debugger calls `ApplyChanges` on a module that has delta metadata, it should also call [IMetaDataEmit::ApplyEditAndContinue](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md) with the same delta metadata on all of its copies of that module’s metadata except for the copy used to emit the changes.</span></span> <span data-ttu-id="8440e-121">Pokud kopie metadat nějakým způsobem stane mimo synchronizace skutečné metadata, ladicí program můžete kdykoli se zbavovat tuto kopii nebo získat nové kopie.</span><span class="sxs-lookup"><span data-stu-id="8440e-121">If a copy of the metadata somehow becomes out-of-sync with the actual metadata, the debugger can always throw away that copy and obtain a new copy.</span></span>  
  
 <span data-ttu-id="8440e-122">Pokud `ApplyChanges` metoda selže, ladění relace je v neplatném stavu a je nutné restartovat.</span><span class="sxs-lookup"><span data-stu-id="8440e-122">If the `ApplyChanges` method fails, the debug session is in an invalid state and must be restarted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8440e-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8440e-123">Requirements</span></span>  
 <span data-ttu-id="8440e-124">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8440e-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8440e-125">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8440e-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8440e-126">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8440e-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8440e-127">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8440e-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
