---
title: "CorMethodImpl – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorMethodImpl
api_location: mscoree.dll
api_type: COM
f1_keywords: CorMethodImpl
helpviewer_keywords: CorMethodImpl enumeration [.NET Framework metadata]
ms.assetid: ffbb3caf-20da-4a4b-8983-77376e72b990
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 85ee55c0d4ec0d3fb8c18dff570afefeb2eaf25e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="cormethodimpl-enumeration"></a><span data-ttu-id="a9b0e-102">CorMethodImpl – výčet</span><span class="sxs-lookup"><span data-stu-id="a9b0e-102">CorMethodImpl Enumeration</span></span>
<span data-ttu-id="a9b0e-103">Obsahuje hodnoty, které popisují způsob implementace funkce.</span><span class="sxs-lookup"><span data-stu-id="a9b0e-103">Contains values that describe method implementation features.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9b0e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a9b0e-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="a9b0e-105">Členové</span><span class="sxs-lookup"><span data-stu-id="a9b0e-105">Members</span></span>  
  
|<span data-ttu-id="a9b0e-106">Člen</span><span class="sxs-lookup"><span data-stu-id="a9b0e-106">Member</span></span>|<span data-ttu-id="a9b0e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a9b0e-107">Description</span></span>|  
|------------|-----------------|  
|`miCodeTypeMask`|<span data-ttu-id="a9b0e-108">Příznaky, které popisují typ kódu.</span><span class="sxs-lookup"><span data-stu-id="a9b0e-108">Flags that describe code type.</span></span>|  
|`miIL`|<span data-ttu-id="a9b0e-109">Určuje, že je metoda implementace Microsoft (MSIL intermediate language).</span><span class="sxs-lookup"><span data-stu-id="a9b0e-109">Specifies that the method implementation is Microsoft intermediate language (MSIL).</span></span>|  
|`miNative`|<span data-ttu-id="a9b0e-110">Určuje, že je nativní implementace metod.</span><span class="sxs-lookup"><span data-stu-id="a9b0e-110">Specifies that the method implementation is native.</span></span>|  
|`miOPTIL`|<span data-ttu-id="a9b0e-111">Určuje, že je metoda implementace OPTIL.</span><span class="sxs-lookup"><span data-stu-id="a9b0e-111">Specifies that the method implementation is OPTIL.</span></span>|  
|`miRuntime`|<span data-ttu-id="a9b0e-112">Určuje, že implementace metod poskytuje modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="a9b0e-112">Specifies that the method implementation is provided by the common language runtime.</span></span>|  
|`miManagedMask`|<span data-ttu-id="a9b0e-113">Příznaky, které označuje, zda kód je spravované nebo nespravované.</span><span class="sxs-lookup"><span data-stu-id="a9b0e-113">Flags that indicate whether the code is managed or unmanaged.</span></span>|  
|`miUnmanaged`|<span data-ttu-id="a9b0e-114">Určuje, že je metoda implementace nespravované.</span><span class="sxs-lookup"><span data-stu-id="a9b0e-114">Specifies that the method implementation is unmanaged.</span></span>|  
|`miManaged`|<span data-ttu-id="a9b0e-115">Určuje, že je spravovaný implementace metod.</span><span class="sxs-lookup"><span data-stu-id="a9b0e-115">Specifies that the method implementation is managed.</span></span>|  
|`miForwardRef`|<span data-ttu-id="a9b0e-116">Určuje, že metoda je definována.</span><span class="sxs-lookup"><span data-stu-id="a9b0e-116">Specifies that the method is defined.</span></span> <span data-ttu-id="a9b0e-117">Tento příznak se používá hlavně ve scénářích sloučení.</span><span class="sxs-lookup"><span data-stu-id="a9b0e-117">This flag is used primarily in merge scenarios.</span></span>|  
|`miPreserveSig`|<span data-ttu-id="a9b0e-118">Určuje, zda podpis metody nemůže být pro konverzi HRESULT pozměněny.</span><span class="sxs-lookup"><span data-stu-id="a9b0e-118">Specifies that the method signature cannot be mangled for an HRESULT conversion.</span></span>|  
|`miInternalCall`|<span data-ttu-id="a9b0e-119">Modul common language runtime vyhrazené pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="a9b0e-119">Reserved for internal use by the common language runtime.</span></span>|  
|`miSynchronized`|<span data-ttu-id="a9b0e-120">Určuje, že metoda je jednovláknové prostřednictvím jeho obsahu.</span><span class="sxs-lookup"><span data-stu-id="a9b0e-120">Specifies that the method is single-threaded through its body.</span></span>|  
|`miNoInlining`|<span data-ttu-id="a9b0e-121">Určuje, že metoda nemůže být vložená.</span><span class="sxs-lookup"><span data-stu-id="a9b0e-121">Specifies that the method cannot be inlined.</span></span>|  
|`miAggressiveInlining`|<span data-ttu-id="a9b0e-122">Určuje, že metoda by měla být vložená Pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="a9b0e-122">Specifies that the method should be inlined if possible.</span></span>|  
|`miNoOptimization`|<span data-ttu-id="a9b0e-123">Určuje, že by neměl být optimalizována metodu.</span><span class="sxs-lookup"><span data-stu-id="a9b0e-123">Specifies that the method should not be optimized.</span></span>|  
|`miMaxMethodImplVal`|<span data-ttu-id="a9b0e-124">Maximální hodnota platná `CorMethodImpl`.</span><span class="sxs-lookup"><span data-stu-id="a9b0e-124">The maximum valid value for a `CorMethodImpl`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a9b0e-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a9b0e-125">Requirements</span></span>  
 <span data-ttu-id="a9b0e-126">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9b0e-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9b0e-127">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="a9b0e-127">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="a9b0e-128">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9b0e-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9b0e-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="a9b0e-129">See Also</span></span>  
 [<span data-ttu-id="a9b0e-130">Výčty metadat</span><span class="sxs-lookup"><span data-stu-id="a9b0e-130">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
