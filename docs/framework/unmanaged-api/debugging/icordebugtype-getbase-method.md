---
title: ICorDebugType::GetBase – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetBase
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetBase
helpviewer_keywords:
- ICorDebugType::GetBase method [.NET Framework debugging]
- GetBase method [.NET Framework debugging]
ms.assetid: f24e1af9-c220-4f79-ae62-4153ec17ea81
topic_type:
- apiref
ms.openlocfilehash: fc406f6e87e5b2be48c6fe7d5fc988774ac5cd11
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379988"
---
# <a name="icordebugtypegetbase-method"></a><span data-ttu-id="fbd6c-102">ICorDebugType::GetBase – metoda</span><span class="sxs-lookup"><span data-stu-id="fbd6c-102">ICorDebugType::GetBase Method</span></span>
<span data-ttu-id="fbd6c-103">Získá ukazatel rozhraní na ICorDebugType, který představuje základní typ, pokud existuje, typu reprezentovaného tímto `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="fbd6c-103">Gets an interface pointer to an ICorDebugType that represents the base type, if one exists, of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbd6c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fbd6c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBase (  
    [out] ICorDebugType   **pBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fbd6c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fbd6c-105">Parameters</span></span>  
 `pBase`  
 <span data-ttu-id="fbd6c-106">mimo Ukazatel na adresu `ICorDebugType` objektu, který představuje základní typ.</span><span class="sxs-lookup"><span data-stu-id="fbd6c-106">[out] A pointer to the address of an `ICorDebugType` object that represents the base type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fbd6c-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fbd6c-107">Remarks</span></span>  
 <span data-ttu-id="fbd6c-108">Vyhledávání základního typu pro typ je užitečné pro implementaci běžných funkcí ladicího programu, jako je například tisk všech polí objektu nebo jeho nadřazených tříd.</span><span class="sxs-lookup"><span data-stu-id="fbd6c-108">Looking up the base type for a type is useful to implement common debugger functionality, such as printing out all the fields of an object or its parent classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbd6c-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fbd6c-109">Requirements</span></span>  
 <span data-ttu-id="fbd6c-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbd6c-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbd6c-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fbd6c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fbd6c-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="fbd6c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fbd6c-113">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbd6c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
