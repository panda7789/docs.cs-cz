---
title: ICorDebugSymbolProvider2 – rozhraní
ms.date: 03/30/2017
ms.assetid: 1c9c3d92-f0de-4d4d-87f1-0c702a4808af
ms.openlocfilehash: e6712dca776bf4c20ce7fc8568e94399a81beecb
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379290"
---
# <a name="icordebugsymbolprovider2-interface"></a><span data-ttu-id="e852e-102">ICorDebugSymbolProvider2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e852e-102">ICorDebugSymbolProvider2 Interface</span></span>
<span data-ttu-id="e852e-103">Logicky rozšiřuje rozhraní [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) a načítá Další informace o symbolech ladění.</span><span class="sxs-lookup"><span data-stu-id="e852e-103">Logically extends the [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e852e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e852e-104">Methods</span></span>  
  
|<span data-ttu-id="e852e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e852e-105">Method</span></span>|<span data-ttu-id="e852e-106">Popis</span><span class="sxs-lookup"><span data-stu-id="e852e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e852e-107">GetFrameProps – metoda</span><span class="sxs-lookup"><span data-stu-id="e852e-107">GetFrameProps Method</span></span>](icordebugsymbolprovider2-getframeprops-method.md)|<span data-ttu-id="e852e-108">Vrátí metodu, která spouští relativní virtuální adresu metody a nadřazený rámec pro relativní virtuální adresu kódu.</span><span class="sxs-lookup"><span data-stu-id="e852e-108">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>|  
|[<span data-ttu-id="e852e-109">GetGenericDictionaryInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="e852e-109">GetGenericDictionaryInfo Method</span></span>](icordebugsymbolprovider2-getgenericdictionaryinfo-method.md)|<span data-ttu-id="e852e-110">Načte mapu obecného slovníku.</span><span class="sxs-lookup"><span data-stu-id="e852e-110">Retrieves a generic dictionary map.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e852e-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e852e-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e852e-112">Toto rozhraní je dostupné jenom pro .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e852e-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="e852e-113">Pokud implementujete Toto rozhraní pro ICorDebug scénáře mimo .NET Native, modul CLR (Common Language Runtime) bude toto rozhraní ignorovat.</span><span class="sxs-lookup"><span data-stu-id="e852e-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e852e-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e852e-114">Requirements</span></span>  
 <span data-ttu-id="e852e-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e852e-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e852e-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e852e-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e852e-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e852e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e852e-118">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e852e-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e852e-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="e852e-119">See also</span></span>

- [<span data-ttu-id="e852e-120">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e852e-120">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="e852e-121">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e852e-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="e852e-122">Ladění</span><span class="sxs-lookup"><span data-stu-id="e852e-122">Debugging</span></span>](index.md)
