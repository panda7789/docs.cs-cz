---
title: ICorProfilerInfo::GetClassIDInfo – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetClassIDInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassIDInfo
helpviewer_keywords:
- GetClassIDInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetClassIDInfo method [.NET Framework profiling]
ms.assetid: 9e93b99e-5aca-415c-8e37-7f33753b612d
topic_type:
- apiref
ms.openlocfilehash: 4b9c577fab91e9527a1edc6c93e0618c8fe4e662
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864066"
---
# <a name="icorprofilerinfogetclassidinfo-method"></a><span data-ttu-id="0bea8-102">ICorProfilerInfo::GetClassIDInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="0bea8-102">ICorProfilerInfo::GetClassIDInfo Method</span></span>
<span data-ttu-id="0bea8-103">Získá nadřazený modul a token metadat pro určenou třídu.</span><span class="sxs-lookup"><span data-stu-id="0bea8-103">Gets the parent module and the metadata token for the specified class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bea8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0bea8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassIDInfo(  
    [in]  ClassID   classId,  
    [out] ModuleID  *pModuleId,  
    [out] mdTypeDef *pTypeDefToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0bea8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0bea8-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="0bea8-106">pro ID třídy, pro kterou chcete získat informace.</span><span class="sxs-lookup"><span data-stu-id="0bea8-106">[in] The ID of the class for which to get the information.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="0bea8-107">mimo Ukazatel na ID nadřazeného modulu třídy.</span><span class="sxs-lookup"><span data-stu-id="0bea8-107">[out] A pointer to the ID of the parent module of the class.</span></span>  
  
 `pTypeDefToken`  
 <span data-ttu-id="0bea8-108">mimo Ukazatel na token metadat pro třídu.</span><span class="sxs-lookup"><span data-stu-id="0bea8-108">[out] A pointer to the metadata token for the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0bea8-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0bea8-109">Remarks</span></span>  
 <span data-ttu-id="0bea8-110">Kód profileru může zavolat [ICorProfilerInfo:: GetModuleMetaData –](icorprofilerinfo-getmodulemetadata-method.md) a získat rozhraní metadat pro daný modul.</span><span class="sxs-lookup"><span data-stu-id="0bea8-110">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) to obtain a metadata interface for a given module.</span></span> <span data-ttu-id="0bea8-111">Token metadat, který je vrácen do umístění odkazovaného `pTypeDefToken` lze následně použít pro přístup k metadatům třídy.</span><span class="sxs-lookup"><span data-stu-id="0bea8-111">The metadata token that is returned to the location referenced by `pTypeDefToken` can then be used to access the metadata for the class.</span></span>  
  
 <span data-ttu-id="0bea8-112">Chcete-li získat další informace pro obecné typy, použijte [ICorProfilerInfo2:: GetClassIDInfo2 –](icorprofilerinfo2-getclassidinfo2-method.md).</span><span class="sxs-lookup"><span data-stu-id="0bea8-112">To get more information for generic types, use [ICorProfilerInfo2::GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0bea8-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0bea8-113">Requirements</span></span>  
 <span data-ttu-id="0bea8-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0bea8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bea8-115">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0bea8-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0bea8-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0bea8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0bea8-117">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bea8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bea8-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0bea8-118">See also</span></span>

- [<span data-ttu-id="0bea8-119">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0bea8-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
