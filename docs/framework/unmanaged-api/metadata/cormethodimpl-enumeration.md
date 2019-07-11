---
title: CorMethodImpl – výčet
ms.date: 03/30/2017
api_name:
- CorMethodImpl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodImpl
helpviewer_keywords:
- CorMethodImpl enumeration [.NET Framework metadata]
ms.assetid: ffbb3caf-20da-4a4b-8983-77376e72b990
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0c88c12646a13e5a24f2475bd2db04c8c831141c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781755"
---
# <a name="cormethodimpl-enumeration"></a><span data-ttu-id="f631c-102">CorMethodImpl – výčet</span><span class="sxs-lookup"><span data-stu-id="f631c-102">CorMethodImpl Enumeration</span></span>
<span data-ttu-id="f631c-103">Obsahuje hodnoty, které popisují způsob implementace funkce.</span><span class="sxs-lookup"><span data-stu-id="f631c-103">Contains values that describe method implementation features.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f631c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f631c-104">Syntax</span></span>  
  
```cpp  
typedef enum CorMethodImpl {  
  
    miCodeTypeMask      =   0x0003,  
    miIL                =   0x0000,  
    miNative            =   0x0001,  
    miOPTIL             =   0x0002,  
    miRuntime           =   0x0003,  
  
    miManagedMask       =   0x0004,  
    miUnmanaged         =   0x0004,  
    miManaged           =   0x0000,  
  
    miForwardRef        =   0x0010,  
    miPreserveSig       =   0x0080,  
  
    miInternalCall      =   0x1000,  
    miSynchronized      =   0x0020,  
    miNoInlining        =   0x0008,  
    miAggressiveInlining =  0x0100,  
    miNoOptimization     =  0x0040,  
    miMaxMethodImplVal  =   0xffff  
  
} CorMethodImpl;  
```  
  
## <a name="members"></a><span data-ttu-id="f631c-105">Členové</span><span class="sxs-lookup"><span data-stu-id="f631c-105">Members</span></span>  
  
|<span data-ttu-id="f631c-106">Člen</span><span class="sxs-lookup"><span data-stu-id="f631c-106">Member</span></span>|<span data-ttu-id="f631c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f631c-107">Description</span></span>|  
|------------|-----------------|  
|`miCodeTypeMask`|<span data-ttu-id="f631c-108">Příznaky, které popisují typ kódu.</span><span class="sxs-lookup"><span data-stu-id="f631c-108">Flags that describe code type.</span></span>|  
|`miIL`|<span data-ttu-id="f631c-109">Určuje, že implementace metody je jazyk Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="f631c-109">Specifies that the method implementation is Microsoft intermediate language (MSIL).</span></span>|  
|`miNative`|<span data-ttu-id="f631c-110">Určuje, že je nativní implementace metody.</span><span class="sxs-lookup"><span data-stu-id="f631c-110">Specifies that the method implementation is native.</span></span>|  
|`miOPTIL`|<span data-ttu-id="f631c-111">Určuje, že implementace metody OPTIL.</span><span class="sxs-lookup"><span data-stu-id="f631c-111">Specifies that the method implementation is OPTIL.</span></span>|  
|`miRuntime`|<span data-ttu-id="f631c-112">Určuje, že implementace metody poskytuje modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="f631c-112">Specifies that the method implementation is provided by the common language runtime.</span></span>|  
|`miManagedMask`|<span data-ttu-id="f631c-113">Příznaky, které označují, zda kód je spravovaná nebo nespravovaná.</span><span class="sxs-lookup"><span data-stu-id="f631c-113">Flags that indicate whether the code is managed or unmanaged.</span></span>|  
|`miUnmanaged`|<span data-ttu-id="f631c-114">Určuje, že implementace metody nespravované.</span><span class="sxs-lookup"><span data-stu-id="f631c-114">Specifies that the method implementation is unmanaged.</span></span>|  
|`miManaged`|<span data-ttu-id="f631c-115">Určuje, že je spravovaná implementace metody.</span><span class="sxs-lookup"><span data-stu-id="f631c-115">Specifies that the method implementation is managed.</span></span>|  
|`miForwardRef`|<span data-ttu-id="f631c-116">Určuje, že metoda je definována.</span><span class="sxs-lookup"><span data-stu-id="f631c-116">Specifies that the method is defined.</span></span> <span data-ttu-id="f631c-117">Tento příznak se používá především ve scénářích sloučení.</span><span class="sxs-lookup"><span data-stu-id="f631c-117">This flag is used primarily in merge scenarios.</span></span>|  
|`miPreserveSig`|<span data-ttu-id="f631c-118">Určuje, že podpis metody nemůže být pozměnění pro konverzi HRESULT.</span><span class="sxs-lookup"><span data-stu-id="f631c-118">Specifies that the method signature cannot be mangled for an HRESULT conversion.</span></span>|  
|`miInternalCall`|<span data-ttu-id="f631c-119">Modul common language runtime vyhrazené pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="f631c-119">Reserved for internal use by the common language runtime.</span></span>|  
|`miSynchronized`|<span data-ttu-id="f631c-120">Určuje, že metoda je jednovláknový prostřednictvím svého těla.</span><span class="sxs-lookup"><span data-stu-id="f631c-120">Specifies that the method is single-threaded through its body.</span></span>|  
|`miNoInlining`|<span data-ttu-id="f631c-121">Určuje, že metoda nemůže být vložená.</span><span class="sxs-lookup"><span data-stu-id="f631c-121">Specifies that the method cannot be inlined.</span></span>|  
|`miAggressiveInlining`|<span data-ttu-id="f631c-122">Určuje, že metoda by měla být vložit. Pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="f631c-122">Specifies that the method should be inlined if possible.</span></span>|  
|`miNoOptimization`|<span data-ttu-id="f631c-123">Určuje, že metoda neměl optimalizovat.</span><span class="sxs-lookup"><span data-stu-id="f631c-123">Specifies that the method should not be optimized.</span></span>|  
|`miMaxMethodImplVal`|<span data-ttu-id="f631c-124">Největší platná hodnota pro `CorMethodImpl`.</span><span class="sxs-lookup"><span data-stu-id="f631c-124">The maximum valid value for a `CorMethodImpl`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f631c-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f631c-125">Requirements</span></span>  
 <span data-ttu-id="f631c-126">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f631c-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f631c-127">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="f631c-127">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="f631c-128">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f631c-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f631c-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f631c-129">See also</span></span>

- [<span data-ttu-id="f631c-130">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="f631c-130">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
