---
title: CorFieldAttr – výčet
ms.date: 03/30/2017
api_name:
- CorFieldAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFieldAttr
helpviewer_keywords:
- CorFieldAttr enumeration [.NET Framework metadata]
ms.assetid: 6ae2c4be-212c-4e74-9288-40a11dc26522
topic_type:
- apiref
ms.openlocfilehash: d28a0c8b7ee85f023026dde6f3cc8f3a8406aa64
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450313"
---
# <a name="corfieldattr-enumeration"></a><span data-ttu-id="3ccd1-102">CorFieldAttr – výčet</span><span class="sxs-lookup"><span data-stu-id="3ccd1-102">CorFieldAttr Enumeration</span></span>
<span data-ttu-id="3ccd1-103">Contains values that describe metadata about a field.</span><span class="sxs-lookup"><span data-stu-id="3ccd1-103">Contains values that describe metadata about a field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ccd1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ccd1-104">Syntax</span></span>  
  
```cpp  
typedef enum CorFieldAttr {  
  
    fdFieldAccessMask           =   0x0007,  
    fdPrivateScope              =   0x0000,  
    fdPrivate                   =   0x0001,  
    fdFamANDAssem               =   0x0002,  
    fdAssembly                  =   0x0003,  
    fdFamily                    =   0x0004,  
    fdFamORAssem                =   0x0005,  
    fdPublic                    =   0x0006,  
  
    fdStatic                    =   0x0010,  
    fdInitOnly                  =   0x0020,  
    fdLiteral                   =   0x0040,  
    fdNotSerialized             =   0x0080,  
  
    fdSpecialName               =   0x0200,  
  
    fdPinvokeImpl               =   0x2000,  
  
    fdReservedMask              =   0x9500,  
    fdRTSpecialName             =   0x0400,  
    fdHasFieldMarshal           =   0x1000,  
    fdHasDefault                =   0x8000,  
    fdHasFieldRVA               =   0x0100  
  
} CorFieldAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="3ccd1-105">Členové</span><span class="sxs-lookup"><span data-stu-id="3ccd1-105">Members</span></span>  
  
|<span data-ttu-id="3ccd1-106">Člen</span><span class="sxs-lookup"><span data-stu-id="3ccd1-106">Member</span></span>|<span data-ttu-id="3ccd1-107">Popis</span><span class="sxs-lookup"><span data-stu-id="3ccd1-107">Description</span></span>|  
|------------|-----------------|  
|`fdFieldAccessMask`|<span data-ttu-id="3ccd1-108">Specifies accessibility information.</span><span class="sxs-lookup"><span data-stu-id="3ccd1-108">Specifies accessibility information.</span></span>|  
|`fdPrivateScope`|<span data-ttu-id="3ccd1-109">Specifies that the field cannot be referenced.</span><span class="sxs-lookup"><span data-stu-id="3ccd1-109">Specifies that the field cannot be referenced.</span></span>|  
|`fdPrivate`|<span data-ttu-id="3ccd1-110">Specifies that the field is accessible only by its parent type.</span><span class="sxs-lookup"><span data-stu-id="3ccd1-110">Specifies that the field is accessible only by its parent type.</span></span>|  
|`fdFamANDAssem`|<span data-ttu-id="3ccd1-111">Specifies that the field is accessible by derived classes in its assembly.</span><span class="sxs-lookup"><span data-stu-id="3ccd1-111">Specifies that the field is accessible by derived classes in its assembly.</span></span>|  
|`fdAssembly`|<span data-ttu-id="3ccd1-112">Specifies that the field is accessible by all types in its assembly.</span><span class="sxs-lookup"><span data-stu-id="3ccd1-112">Specifies that the field is accessible by all types in its assembly.</span></span>|  
|`fdFamily`|<span data-ttu-id="3ccd1-113">Specifies that the field is accessible only by its type and derived classes.</span><span class="sxs-lookup"><span data-stu-id="3ccd1-113">Specifies that the field is accessible only by its type and derived classes.</span></span>|  
|`fdFamORAssem`|<span data-ttu-id="3ccd1-114">Specifies that the field is accessible by derived classes and by all types in its assembly.</span><span class="sxs-lookup"><span data-stu-id="3ccd1-114">Specifies that the field is accessible by derived classes and by all types in its assembly.</span></span>|  
|`fdPublic`|<span data-ttu-id="3ccd1-115">Specifies that the field is accessible by all types with visibility of this scope.</span><span class="sxs-lookup"><span data-stu-id="3ccd1-115">Specifies that the field is accessible by all types with visibility of this scope.</span></span>|  
|`fdStatic`|<span data-ttu-id="3ccd1-116">Specifies that the field is a member of its type rather than an instance member.</span><span class="sxs-lookup"><span data-stu-id="3ccd1-116">Specifies that the field is a member of its type rather than an instance member.</span></span>|  
|`fdInitOnly`|<span data-ttu-id="3ccd1-117">Specifies that the field cannot be changed after it is initialized.</span><span class="sxs-lookup"><span data-stu-id="3ccd1-117">Specifies that the field cannot be changed after it is initialized.</span></span>|  
|`fdLiteral`|<span data-ttu-id="3ccd1-118">Specifies that the field value is a compile-time constant.</span><span class="sxs-lookup"><span data-stu-id="3ccd1-118">Specifies that the field value is a compile-time constant.</span></span>|  
|`fdNotSerialized`|<span data-ttu-id="3ccd1-119">Specifies that the field is not serialized when its type is remoted.</span><span class="sxs-lookup"><span data-stu-id="3ccd1-119">Specifies that the field is not serialized when its type is remoted.</span></span>|  
|`fdSpecialName`|<span data-ttu-id="3ccd1-120">Specifies that the field is special, and that its name describes how.</span><span class="sxs-lookup"><span data-stu-id="3ccd1-120">Specifies that the field is special, and that its name describes how.</span></span>|  
|`fdPinvokeImpl`|<span data-ttu-id="3ccd1-121">Specifies that the field implementation is forwarded through PInvoke.</span><span class="sxs-lookup"><span data-stu-id="3ccd1-121">Specifies that the field implementation is forwarded through PInvoke.</span></span>|  
|`fdReservedMask`|<span data-ttu-id="3ccd1-122">Reserved for internal use by the common language runtime.</span><span class="sxs-lookup"><span data-stu-id="3ccd1-122">Reserved for internal use by the common language runtime.</span></span>|  
|`fdRTSpecialName`|<span data-ttu-id="3ccd1-123">Specifies that the common language runtime metadata internal APIs should check the encoding of the name.</span><span class="sxs-lookup"><span data-stu-id="3ccd1-123">Specifies that the common language runtime metadata internal APIs should check the encoding of the name.</span></span>|  
|`fdHasFieldMarshal`|<span data-ttu-id="3ccd1-124">Specifies that the field contains marshaling information.</span><span class="sxs-lookup"><span data-stu-id="3ccd1-124">Specifies that the field contains marshaling information.</span></span>|  
|`fdHasDefault`|<span data-ttu-id="3ccd1-125">Specifies that the field has a default value.</span><span class="sxs-lookup"><span data-stu-id="3ccd1-125">Specifies that the field has a default value.</span></span>|  
|`fdHasFieldRVA`|<span data-ttu-id="3ccd1-126">Specifies that the field has a relative virtual address.</span><span class="sxs-lookup"><span data-stu-id="3ccd1-126">Specifies that the field has a relative virtual address.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3ccd1-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3ccd1-127">Requirements</span></span>  
 <span data-ttu-id="3ccd1-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ccd1-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ccd1-129">**Header:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="3ccd1-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="3ccd1-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ccd1-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ccd1-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3ccd1-131">See also</span></span>

- [<span data-ttu-id="3ccd1-132">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="3ccd1-132">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
