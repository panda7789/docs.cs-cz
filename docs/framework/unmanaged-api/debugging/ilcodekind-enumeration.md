---
title: Výčet ILCodeKind
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ILCodeKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b91765e4-82db-46f9-a6dc-6b80610276af
topic_type:
- apiref
ms.openlocfilehash: 0586b9e184a0958b978837601db002e035881cbc
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421030"
---
# <a name="ilcodekind-enumeration"></a><span data-ttu-id="441d9-102">Výčet ILCodeKind</span><span class="sxs-lookup"><span data-stu-id="441d9-102">ILCodeKind Enumeration</span></span>
<span data-ttu-id="441d9-103">[Podporované v .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="441d9-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="441d9-104">Poskytuje hodnoty, které určují, jestli má ladicí program přístup k místním proměnným nebo kódu přidanému v profileru ReJIT instrumentace.</span><span class="sxs-lookup"><span data-stu-id="441d9-104">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="441d9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="441d9-105">Syntax</span></span>  
  
```cpp
typedef enum ILCodeKind {  
   ILCODE_ORIGINAL_IL = 0x1,  
   ILCODE_REJIT_IL = 0x2,  
} ILCodeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="441d9-106">Členové</span><span class="sxs-lookup"><span data-stu-id="441d9-106">Members</span></span>  
  
|<span data-ttu-id="441d9-107">Název členu</span><span class="sxs-lookup"><span data-stu-id="441d9-107">Member name</span></span>|<span data-ttu-id="441d9-108">Popis</span><span class="sxs-lookup"><span data-stu-id="441d9-108">Description</span></span>|  
|-----------------|-----------------|  
|`ILCODE_ORIGINAL_IL`|<span data-ttu-id="441d9-109">Ladicí program nemá přístup k informacím z instrumentace ReJIT.</span><span class="sxs-lookup"><span data-stu-id="441d9-109">The debugger does not have access to information from ReJIT instrumentation.</span></span>|  
|`ILCODE_REJIT_IL`|<span data-ttu-id="441d9-110">Ladicí program má přístup k informacím z instrumentace ReJIT.</span><span class="sxs-lookup"><span data-stu-id="441d9-110">The debugger has access to information from ReJIT instrumentation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="441d9-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="441d9-111">Remarks</span></span>  
 <span data-ttu-id="441d9-112">Člen `ILCodeKind` výčtu může být předán metodám [Enumeratelocalvariablesex –](icordebugilframe4-enumeratelocalvariablesex-method.md) a [getlocalvariableex –](icordebugilframe4-getlocalvariableex-method.md) k určení, zda ladicí program může přistupovat k proměnným přidaným do instrumentace ReJIT profileru a k metodě [getcodeex –](icordebugilframe4-getcodeex-method.md) k určení, zda ladicí program může získat přístup k instrumentované Il.</span><span class="sxs-lookup"><span data-stu-id="441d9-112">A member of the `ILCodeKind` enumeration can be passed to the [EnumerateLocalVariablesEx](icordebugilframe4-enumeratelocalvariablesex-method.md) and [GetLocalVariableEx](icordebugilframe4-getlocalvariableex-method.md) methods to determine whether the debugger can access variables added in profiler ReJIT instrumentation, and to the [GetCodeEx](icordebugilframe4-getcodeex-method.md) method to determine whether the debugger can access instrumented IL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="441d9-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="441d9-113">Requirements</span></span>  
 <span data-ttu-id="441d9-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="441d9-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="441d9-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="441d9-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="441d9-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="441d9-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="441d9-117">**Verze .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="441d9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="441d9-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="441d9-118">See also</span></span>

- [<span data-ttu-id="441d9-119">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="441d9-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="441d9-120">Rozhraní ICorDebugILFrame4</span><span class="sxs-lookup"><span data-stu-id="441d9-120">ICorDebugILFrame4 Interface</span></span>](icordebugilframe4-interface.md)
- [<span data-ttu-id="441d9-121">ReJIT: Průvodce</span><span class="sxs-lookup"><span data-stu-id="441d9-121">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
