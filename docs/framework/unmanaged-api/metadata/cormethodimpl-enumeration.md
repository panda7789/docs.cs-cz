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
ms.openlocfilehash: a76a7a2d4ad68e367e38e175377aff40ce399346
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450208"
---
# <a name="cormethodimpl-enumeration"></a><span data-ttu-id="b8954-102">CorMethodImpl – výčet</span><span class="sxs-lookup"><span data-stu-id="b8954-102">CorMethodImpl Enumeration</span></span>
<span data-ttu-id="b8954-103">Contains values that describe method implementation features.</span><span class="sxs-lookup"><span data-stu-id="b8954-103">Contains values that describe method implementation features.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8954-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8954-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="b8954-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b8954-105">Members</span></span>  
  
|<span data-ttu-id="b8954-106">Člen</span><span class="sxs-lookup"><span data-stu-id="b8954-106">Member</span></span>|<span data-ttu-id="b8954-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b8954-107">Description</span></span>|  
|------------|-----------------|  
|`miCodeTypeMask`|<span data-ttu-id="b8954-108">Flags that describe code type.</span><span class="sxs-lookup"><span data-stu-id="b8954-108">Flags that describe code type.</span></span>|  
|`miIL`|<span data-ttu-id="b8954-109">Specifies that the method implementation is Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="b8954-109">Specifies that the method implementation is Microsoft intermediate language (MSIL).</span></span>|  
|`miNative`|<span data-ttu-id="b8954-110">Specifies that the method implementation is native.</span><span class="sxs-lookup"><span data-stu-id="b8954-110">Specifies that the method implementation is native.</span></span>|  
|`miOPTIL`|<span data-ttu-id="b8954-111">Specifies that the method implementation is OPTIL.</span><span class="sxs-lookup"><span data-stu-id="b8954-111">Specifies that the method implementation is OPTIL.</span></span>|  
|`miRuntime`|<span data-ttu-id="b8954-112">Specifies that the method implementation is provided by the common language runtime.</span><span class="sxs-lookup"><span data-stu-id="b8954-112">Specifies that the method implementation is provided by the common language runtime.</span></span>|  
|`miManagedMask`|<span data-ttu-id="b8954-113">Flags that indicate whether the code is managed or unmanaged.</span><span class="sxs-lookup"><span data-stu-id="b8954-113">Flags that indicate whether the code is managed or unmanaged.</span></span>|  
|`miUnmanaged`|<span data-ttu-id="b8954-114">Specifies that the method implementation is unmanaged.</span><span class="sxs-lookup"><span data-stu-id="b8954-114">Specifies that the method implementation is unmanaged.</span></span>|  
|`miManaged`|<span data-ttu-id="b8954-115">Specifies that the method implementation is managed.</span><span class="sxs-lookup"><span data-stu-id="b8954-115">Specifies that the method implementation is managed.</span></span>|  
|`miForwardRef`|<span data-ttu-id="b8954-116">Specifies that the method is defined.</span><span class="sxs-lookup"><span data-stu-id="b8954-116">Specifies that the method is defined.</span></span> <span data-ttu-id="b8954-117">This flag is used primarily in merge scenarios.</span><span class="sxs-lookup"><span data-stu-id="b8954-117">This flag is used primarily in merge scenarios.</span></span>|  
|`miPreserveSig`|<span data-ttu-id="b8954-118">Specifies that the method signature cannot be mangled for an HRESULT conversion.</span><span class="sxs-lookup"><span data-stu-id="b8954-118">Specifies that the method signature cannot be mangled for an HRESULT conversion.</span></span>|  
|`miInternalCall`|<span data-ttu-id="b8954-119">Reserved for internal use by the common language runtime.</span><span class="sxs-lookup"><span data-stu-id="b8954-119">Reserved for internal use by the common language runtime.</span></span>|  
|`miSynchronized`|<span data-ttu-id="b8954-120">Specifies that the method is single-threaded through its body.</span><span class="sxs-lookup"><span data-stu-id="b8954-120">Specifies that the method is single-threaded through its body.</span></span>|  
|`miNoInlining`|<span data-ttu-id="b8954-121">Specifies that the method cannot be inlined.</span><span class="sxs-lookup"><span data-stu-id="b8954-121">Specifies that the method cannot be inlined.</span></span>|  
|`miAggressiveInlining`|<span data-ttu-id="b8954-122">Specifies that the method should be inlined if possible.</span><span class="sxs-lookup"><span data-stu-id="b8954-122">Specifies that the method should be inlined if possible.</span></span>|  
|`miNoOptimization`|<span data-ttu-id="b8954-123">Specifies that the method should not be optimized.</span><span class="sxs-lookup"><span data-stu-id="b8954-123">Specifies that the method should not be optimized.</span></span>|  
|`miMaxMethodImplVal`|<span data-ttu-id="b8954-124">The maximum valid value for a `CorMethodImpl`.</span><span class="sxs-lookup"><span data-stu-id="b8954-124">The maximum valid value for a `CorMethodImpl`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b8954-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b8954-125">Requirements</span></span>  
 <span data-ttu-id="b8954-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8954-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8954-127">**Header:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="b8954-127">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="b8954-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8954-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8954-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b8954-129">See also</span></span>

- [<span data-ttu-id="b8954-130">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="b8954-130">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
