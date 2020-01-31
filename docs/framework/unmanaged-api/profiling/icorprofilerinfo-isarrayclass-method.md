---
title: ICorProfilerInfo::IsArrayClass – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.IsArrayClass
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::IsArrayClass
helpviewer_keywords:
- IsArrayClass method [.NET Framework profiling]
- ICorProfilerInfo::IsArrayClass method [.NET Framework profiling]
ms.assetid: 7f230961-23a6-4d56-ad2d-7a876d65705f
topic_type:
- apiref
ms.openlocfilehash: a6e483d820d183afc8ba6a68fc4635730ffd1e51
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76869314"
---
# <a name="icorprofilerinfoisarrayclass-method"></a><span data-ttu-id="776bc-102">ICorProfilerInfo::IsArrayClass – metoda</span><span class="sxs-lookup"><span data-stu-id="776bc-102">ICorProfilerInfo::IsArrayClass Method</span></span>
<span data-ttu-id="776bc-103">Určuje, zda je zadaná třída třídou Array.</span><span class="sxs-lookup"><span data-stu-id="776bc-103">Determines whether the specified class is an array class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="776bc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="776bc-104">Syntax</span></span>  
  
```cpp  
HRESULT IsArrayClass(  
    [in]  ClassID        classId,  
    [out] CorElementType *pBaseElemType,  
    [out] ClassID        *pBaseClassId,  
    [out] ULONG          *pcRank);  
```  
  
## <a name="parameters"></a><span data-ttu-id="776bc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="776bc-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="776bc-106">pro ID třídy, která se má prozkoumat</span><span class="sxs-lookup"><span data-stu-id="776bc-106">[in] The ID of the class to be examined.</span></span>  
  
 `pBaseElemType`  
 <span data-ttu-id="776bc-107">mimo Ukazatel na hodnotu výčtu CorElementType –, která určuje typ prvků pole.</span><span class="sxs-lookup"><span data-stu-id="776bc-107">[out] A pointer to a value of the CorElementType enumeration that indicates the type of the array elements.</span></span>  
  
 `pBaseClassId`  
 <span data-ttu-id="776bc-108">mimo Ukazatel na ID třídy prvků pole, je-li k dispozici.</span><span class="sxs-lookup"><span data-stu-id="776bc-108">[out] A pointer to the class ID of the array elements, when available.</span></span>  
  
 `pcRank`  
 <span data-ttu-id="776bc-109">mimo Ukazatel na celé číslo, které určuje pořadí (tj. počet rozměrů) pole.</span><span class="sxs-lookup"><span data-stu-id="776bc-109">[out] A pointer to an integer that indicates the rank (that is, number of dimensions) of the array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="776bc-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="776bc-110">Remarks</span></span>  
 <span data-ttu-id="776bc-111">Pokud je zadaná třída třídou Array, metoda `IsArrayClass` vrátí S_OK HRESULT a hodnoty pro výstupní parametry, které nejsou null.</span><span class="sxs-lookup"><span data-stu-id="776bc-111">If the specified class is an array class, the `IsArrayClass` method returns an S_OK HRESULT and values for any non-null output parameters.</span></span> <span data-ttu-id="776bc-112">V opačném případě vrátí S_FALSE.</span><span class="sxs-lookup"><span data-stu-id="776bc-112">Otherwise, it returns S_FALSE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="776bc-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="776bc-113">Requirements</span></span>  
 <span data-ttu-id="776bc-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="776bc-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="776bc-115">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="776bc-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="776bc-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="776bc-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="776bc-117">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="776bc-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="776bc-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="776bc-118">See also</span></span>

- [<span data-ttu-id="776bc-119">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="776bc-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
