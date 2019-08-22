---
title: ICorProfilerInfo8::GetDynamicFunctionInfo
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetDynamicFunctionInfo
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: d59de04e6af6cfec473899e0a3edadcb3257d385
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69665684"
---
# <a name="icorprofilerinfo8getdynamicfunctioninfo-method"></a><span data-ttu-id="d8845-102">ICorProfilerInfo8:: GetDynamicFunctionInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="d8845-102">ICorProfilerInfo8::GetDynamicFunctionInfo Method</span></span>

<span data-ttu-id="d8845-103">Načte informace o dynamických metodách.</span><span class="sxs-lookup"><span data-stu-id="d8845-103">Retrieves information about dynamic methods.</span></span>

## <a name="syntax"></a><span data-ttu-id="d8845-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8845-104">Syntax</span></span>

```cpp
HRESULT GetDynamicFunctionInfo( [in]  FunctionID              functionId,
                                [out] ModuleID                *moduleId,
                                [out] PCCOR_SIGNATURE         *ppvSig,
                                [out] ULONG                   *pbSig,
                                [in]  ULONG                   cchName,
                                [out] ULONG                   *pcchName,
                                [out] WCHAR                   wszName[]);
```

#### <a name="parameters"></a><span data-ttu-id="d8845-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8845-105">Parameters</span></span>

`functionId` \
<span data-ttu-id="d8845-106">pro ID funkce, pro kterou mají být načteny informace</span><span class="sxs-lookup"><span data-stu-id="d8845-106">[in] The ID of the function for which to retrieve information.</span></span>

`moduleId` \
<span data-ttu-id="d8845-107">pro Ukazatel na modul, ve kterém je definována nadřazená třída funkce.</span><span class="sxs-lookup"><span data-stu-id="d8845-107">[in] A pointer to the module in which the function's parent class is defined.</span></span>

`ppvSig` \
<span data-ttu-id="d8845-108">mimo Ukazatel na signaturu funkce.</span><span class="sxs-lookup"><span data-stu-id="d8845-108">[out] A pointer to the signature for the function.</span></span>

`pbSig` \
<span data-ttu-id="d8845-109">mimo Ukazatel na počet bajtů pro podpis funkce.</span><span class="sxs-lookup"><span data-stu-id="d8845-109">[out] A pointer to the count of bytes for the function signature.</span></span>

`cchName` \
<span data-ttu-id="d8845-110">pro Maximální velikost `wszName` pole.</span><span class="sxs-lookup"><span data-stu-id="d8845-110">[in] The maximum size of the `wszName` array.</span></span>

`pcchName` \
<span data-ttu-id="d8845-111">mimo Počet znaků v `wszName` poli.</span><span class="sxs-lookup"><span data-stu-id="d8845-111">[out] The number of characters in the `wszName` array.</span></span>

`wszName` \
<span data-ttu-id="d8845-112">mimo Pole `WCHAR` , které je názvem funkce, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="d8845-112">[out] An array of `WCHAR` which is the name of the function, if one exists.</span></span>

## <a name="remarks"></a><span data-ttu-id="d8845-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d8845-113">Remarks</span></span>

<span data-ttu-id="d8845-114">Některé metody, jako jsou zástupné procedury IL nebo LCG, nemají přidružená metadata, která lze načíst pomocí rozhraní API [IMetaDataImport](../metadata/imetadataimport-interface.md) a [IMetaDataImport2](../metadata/imetadataimport2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="d8845-114">Certain methods like IL Stubs or LCG do not have associated metadata that can be retrieved using the [IMetaDataImport](../metadata/imetadataimport-interface.md) and [IMetaDataImport2](../metadata/imetadataimport2-interface.md) APIs.</span></span> <span data-ttu-id="d8845-115">Tyto metody mohou být v profilerech zjištěny prostřednictvím ukazatelů instrukcí nebo naslouchat [ICorProfilerCallback8::D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span><span class="sxs-lookup"><span data-stu-id="d8845-115">Such methods can be encountered by profilers through instruction pointers or by listening to [ICorProfilerCallback8::DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span></span>

<span data-ttu-id="d8845-116">Toto rozhraní API je možné použít k načtení informací o dynamických metodách, včetně popisného názvu, pokud je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="d8845-116">This API can be used to retrieve information about dynamic methods, including a friendly name, if available.</span></span>

## <a name="requirements"></a><span data-ttu-id="d8845-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d8845-117">Requirements</span></span>

<span data-ttu-id="d8845-118">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8845-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="d8845-119">**Hlaviček** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d8845-119">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="d8845-120">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8845-120">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="d8845-121">**Verze .NET Framework:** [! ZAHRNOUT[net_current_v472plus](../../../../includes/net-current-v472plus.md)</span><span class="sxs-lookup"><span data-stu-id="d8845-121">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="d8845-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d8845-122">See also</span></span>

- [<span data-ttu-id="d8845-123">Rozhraní ICorProfilerInfo8</span><span class="sxs-lookup"><span data-stu-id="d8845-123">ICorProfilerInfo8 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md)
