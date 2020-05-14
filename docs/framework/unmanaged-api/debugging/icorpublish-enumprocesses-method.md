---
title: ICorPublish::EnumProcesses – metoda
ms.date: 03/30/2017
api_name:
- ICorPublish.EnumProcesses
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::EnumProcesses
helpviewer_keywords:
- ICorPublish::EnumProcesses method [.NET Framework debugging]
- EnumProcesses method [.NET Framework debugging]
ms.assetid: 4ae765f0-93b2-4b6f-aea1-7b0cf44e04a7
topic_type:
- apiref
ms.openlocfilehash: 70255a89cee13abfe63b01351f8ffba51e54665a
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396393"
---
# <a name="icorpublishenumprocesses-method"></a><span data-ttu-id="36d46-102">ICorPublish::EnumProcesses – metoda</span><span class="sxs-lookup"><span data-stu-id="36d46-102">ICorPublish::EnumProcesses Method</span></span>
<span data-ttu-id="36d46-103">Získá enumerátor pro spravované procesy, které jsou spuštěny na tomto počítači.</span><span class="sxs-lookup"><span data-stu-id="36d46-103">Gets an enumerator for the managed processes running on this computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36d46-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36d46-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumProcesses (  
    [in] COR_PUB_ENUMPROCESS       Type,  
    [out] ICorPublishProcessEnum   **ppIEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="36d46-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="36d46-105">Parameters</span></span>  
 `Type`  
 <span data-ttu-id="36d46-106">Hodnota výčtu [COR_PUB_ENUMPROCESS](cor-pub-enumprocess-enumeration.md) , která určuje typ procesu, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="36d46-106">A value of the [COR_PUB_ENUMPROCESS](cor-pub-enumprocess-enumeration.md) enumeration that specifies the type of process to be retrieved.</span></span> <span data-ttu-id="36d46-107">V aktuální verzi je platná pouze COR_PUB_MANAGEDONLY.</span><span class="sxs-lookup"><span data-stu-id="36d46-107">In the current version, only COR_PUB_MANAGEDONLY is valid.</span></span>  
  
 `ppIEnum`  
 <span data-ttu-id="36d46-108">Ukazatel na adresu instance [ICorPublishProcessEnum –](icorpublishprocessenum-interface.md) , která je enumerátorem procesů.</span><span class="sxs-lookup"><span data-stu-id="36d46-108">A pointer to the address of an [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) instance that is the enumerator of the processes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36d46-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="36d46-109">Remarks</span></span>  
 <span data-ttu-id="36d46-110">Kolekce procesů čítače výčtu je založena na snímku procesů, které jsou spuštěny při `EnumProcesses` volání metody.</span><span class="sxs-lookup"><span data-stu-id="36d46-110">The enumerator's collection of processes is based on a snapshot of the processes that are running when the `EnumProcesses` method is called.</span></span> <span data-ttu-id="36d46-111">Enumerátor nebude zahrnovat žádné procesy, které se ukončí nebo spustí po `EnumProcesses` volání metody.</span><span class="sxs-lookup"><span data-stu-id="36d46-111">The enumerator will not include any processes that terminate before or start after `EnumProcesses` is called.</span></span>  
  
 <span data-ttu-id="36d46-112">`EnumProcesses`Metodu lze v této instanci [ICorPublish –](icorpublish-interface.md) volat více než jednou, aby bylo možné vytvořit novou aktuální kolekci procesů.</span><span class="sxs-lookup"><span data-stu-id="36d46-112">The `EnumProcesses` method may be called more than once on this [ICorPublish](icorpublish-interface.md) instance to create a new up-to-date collection of processes.</span></span> <span data-ttu-id="36d46-113">Existující kolekce nebudou ovlivněny následnými voláními `EnumProcesses` metody.</span><span class="sxs-lookup"><span data-stu-id="36d46-113">Existing collections will not be affected by subsequent calls of the `EnumProcesses` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36d46-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="36d46-114">Requirements</span></span>  
 <span data-ttu-id="36d46-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36d46-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36d46-116">**Hlavička:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="36d46-116">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="36d46-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="36d46-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36d46-118">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36d46-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36d46-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="36d46-119">See also</span></span>

- [<span data-ttu-id="36d46-120">ICorPublish – rozhraní</span><span class="sxs-lookup"><span data-stu-id="36d46-120">ICorPublish Interface</span></span>](icorpublish-interface.md)
