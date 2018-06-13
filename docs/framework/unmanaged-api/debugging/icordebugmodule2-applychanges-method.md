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
ms.openlocfilehash: 5a406e945a67352bc7f126b40bd56f4a11dd693b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419540"
---
# <a name="icordebugmodule2applychanges-method"></a><span data-ttu-id="bc4ea-102">ICorDebugModule2::ApplyChanges – metoda</span><span class="sxs-lookup"><span data-stu-id="bc4ea-102">ICorDebugModule2::ApplyChanges Method</span></span>
<span data-ttu-id="bc4ea-103">Změny v metadatech a změny v kódu Microsoft (MSIL intermediate language) se vztahuje na běžící proces.</span><span class="sxs-lookup"><span data-stu-id="bc4ea-103">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc4ea-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bc4ea-104">Syntax</span></span>  
  
```  
HRESULT ApplyChanges (  
    [in] ULONG                       cbMetadata,  
    [in, size_is(cbMetadata)] BYTE   pbMetadata[],  
    [in] ULONG                       cbIL,  
    [in, size_is(cbIL)] BYTE         pbIL[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bc4ea-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bc4ea-105">Parameters</span></span>  
 `cbMetadata`  
 <span data-ttu-id="bc4ea-106">[v] Velikost v bajtech, rozdílů metadat.</span><span class="sxs-lookup"><span data-stu-id="bc4ea-106">[in] Size, in bytes, of the delta metadata.</span></span>  
  
 `pbMetadata`  
 <span data-ttu-id="bc4ea-107">[v] Vyrovnávací paměti, který obsahuje delta metadata.</span><span class="sxs-lookup"><span data-stu-id="bc4ea-107">[in] Buffer that contains the delta metadata.</span></span> <span data-ttu-id="bc4ea-108">Vrátí adresu vyrovnávací paměti [imetadataemit2::savedeltatomemory –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="bc4ea-108">The address of the buffer is returned from the [IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md) method.</span></span>  
  
 <span data-ttu-id="bc4ea-109">Vzhledem k začátku MSIL kódu by měla být relativní virtuální adresy (RVAs) v metadatech.</span><span class="sxs-lookup"><span data-stu-id="bc4ea-109">The relative virtual addresses (RVAs) in the metadata should be relative to the start of the MSIL code.</span></span>  
  
 `cbIL`  
 <span data-ttu-id="bc4ea-110">[v] Velikost v bajtech, rozdílové MSIL kódu.</span><span class="sxs-lookup"><span data-stu-id="bc4ea-110">[in] Size, in bytes, of the delta MSIL code.</span></span>  
  
 `pbIL`  
 <span data-ttu-id="bc4ea-111">[v] Vyrovnávací paměť, která obsahuje aktualizované MSIL kód.</span><span class="sxs-lookup"><span data-stu-id="bc4ea-111">[in] Buffer that contains the updated MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc4ea-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bc4ea-112">Remarks</span></span>  
 <span data-ttu-id="bc4ea-113">`pbMetadata` Parametr je ve formátu metadat speciální delta (jako výstupní podle [imetadataemit2::savedeltatomemory –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)).</span><span class="sxs-lookup"><span data-stu-id="bc4ea-113">The `pbMetadata` parameter is in a special delta metadata format (as output by [IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)).</span></span> <span data-ttu-id="bc4ea-114">`pbMetadata` přebírá předchozí metadat jako základ a popisuje jednotlivé změny, které chcete použít pro tento základní.</span><span class="sxs-lookup"><span data-stu-id="bc4ea-114">`pbMetadata` takes previous metadata as a base and describes individual changes to apply to that base.</span></span>  
  
 <span data-ttu-id="bc4ea-115">Naopak `pbIL[`] parametr obsahuje nové MSIL pro metodu aktualizované a měl by úplně nahradit předchozí MSIL pro danou metodu</span><span class="sxs-lookup"><span data-stu-id="bc4ea-115">In contrast, the `pbIL[`] parameter contains the new MSIL for the updated method, and is meant to completely replace the previous MSIL for that method</span></span>  
  
 <span data-ttu-id="bc4ea-116">Když rozdíl MSIL a metadat byla vytvořena v paměti ladicím programu, ladicí program volá `ApplyChanges` a odešlete změny do modulu common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="bc4ea-116">When the delta MSIL and the metadata have been created in the debugger’s memory, the debugger calls `ApplyChanges` to send the changes into the common language runtime (CLR).</span></span> <span data-ttu-id="bc4ea-117">Modul runtime aktualizací jeho tabulky metadat, umístí nové MSIL do procesu a nastaví nové MSIL kompilací za běhu (JIT).</span><span class="sxs-lookup"><span data-stu-id="bc4ea-117">The runtime updates its metadata tables, places the new MSIL into the process, and sets up a just-in-time (JIT) compilation of the new MSIL.</span></span> <span data-ttu-id="bc4ea-118">Při použití změny by měly volat ladicího programu [imetadataemit2::resetenclog –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md) připravit pro další úpravy relace.</span><span class="sxs-lookup"><span data-stu-id="bc4ea-118">When the changes have been applied, the debugger should call [IMetaDataEmit2::ResetENCLog](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md) to prepare for the next editing session.</span></span> <span data-ttu-id="bc4ea-119">Ladicí program může pak pokračovat v procesu.</span><span class="sxs-lookup"><span data-stu-id="bc4ea-119">The debugger may then continue the process.</span></span>  
  
 <span data-ttu-id="bc4ea-120">Vždy, když ladicí program volá `ApplyChanges` na modul, který obsahuje metadata rozdílů, by také zavolat [imetadataemit::applyeditandcontinue –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md) s metadaty rozdílů na všech jeho kopie metadata tohoto modulu s výjimkou kopie použít pro vydávání změny.</span><span class="sxs-lookup"><span data-stu-id="bc4ea-120">Whenever the debugger calls `ApplyChanges` on a module that has delta metadata, it should also call [IMetaDataEmit::ApplyEditAndContinue](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md) with the same delta metadata on all of its copies of that module’s metadata except for the copy used to emit the changes.</span></span> <span data-ttu-id="bc4ea-121">Pokud se kopie metadat nějakým způsobem stane se na synchronizaci s metadaty skutečné ladicího programu můžete kdykoli throw rychle tuto kopii nebo požádejte o novou kopii.</span><span class="sxs-lookup"><span data-stu-id="bc4ea-121">If a copy of the metadata somehow becomes out-of-sync with the actual metadata, the debugger can always throw away that copy and obtain a new copy.</span></span>  
  
 <span data-ttu-id="bc4ea-122">Pokud `ApplyChanges` metoda selže, ladění relace je v neplatném stavu a musí být restartován.</span><span class="sxs-lookup"><span data-stu-id="bc4ea-122">If the `ApplyChanges` method fails, the debug session is in an invalid state and must be restarted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc4ea-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bc4ea-123">Requirements</span></span>  
 <span data-ttu-id="bc4ea-124">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc4ea-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc4ea-125">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bc4ea-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bc4ea-126">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bc4ea-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc4ea-127">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc4ea-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
