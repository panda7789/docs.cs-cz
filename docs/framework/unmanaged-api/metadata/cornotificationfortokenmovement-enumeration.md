---
title: CorNotificationForTokenMovement – výčet
ms.date: 03/30/2017
api_name:
- CorNotificationForTokenMovement
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNotificationForTokenMovement
helpviewer_keywords:
- CorNotificationForTokenMovement enumeration [.NET Framework metadata]
ms.assetid: 1edd1670-976a-4fc8-bef7-7c41e60ad989
topic_type:
- apiref
ms.openlocfilehash: e8065a5492884a4b7f5d662737e4beddc6fca5b3
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007595"
---
# <a name="cornotificationfortokenmovement-enumeration"></a><span data-ttu-id="9f55b-102">CorNotificationForTokenMovement – výčet</span><span class="sxs-lookup"><span data-stu-id="9f55b-102">CorNotificationForTokenMovement Enumeration</span></span>
<span data-ttu-id="9f55b-103">Určuje oznámení, která se odešlou do klienta rozhraní API pro metadata, když dojde k přemapování tokenu.</span><span class="sxs-lookup"><span data-stu-id="9f55b-103">Specifies the notifications that will be sent to the metadata API client when a token remap occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f55b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f55b-104">Syntax</span></span>  
  
```cpp  
typedef enum CorNotificationForTokenMovement {  
  
    MDNotifyDefault             = 0x0000000f,  
    MDNotifyAll                 = 0xffffffff,  
    MDNotifyNone                = 0x00000000,  
    MDNotifyMethodDef           = 0x00000001,  
    MDNotifyMemberRef           = 0x00000002,  
    MDNotifyFieldDef            = 0x00000004,  
    MDNotifyTypeRef             = 0x00000008,  
  
    MDNotifyTypeDef             = 0x00000010,  
    MDNotifyParamDef            = 0x00000020,  
    MDNotifyInterfaceImpl       = 0x00000040,  
    MDNotifyProperty            = 0x00000080,  
    MDNotifyEvent               = 0x00000100,  
    MDNotifySignature           = 0x00000200,  
    MDNotifyTypeSpec            = 0x00000400,  
    MDNotifyCustomAttribute     = 0x00000800,  
    MDNotifySecurityValue       = 0x00001000,  
    MDNotifyPermission          = 0x00002000,  
    MDNotifyModuleRef           = 0x00004000,  
  
    MDNotifyNameSpace           = 0x00008000,  
  
    MDNotifyAssemblyRef         = 0x01000000,  
    MDNotifyFile                = 0x02000000,  
    MDNotifyExportedType        = 0x04000000,  
    MDNotifyResource            = 0x08000000  
  
} CorNotificationForTokenMovement;  
```  
  
## <a name="members"></a><span data-ttu-id="9f55b-105">Členové</span><span class="sxs-lookup"><span data-stu-id="9f55b-105">Members</span></span>  
  
|<span data-ttu-id="9f55b-106">Člen</span><span class="sxs-lookup"><span data-stu-id="9f55b-106">Member</span></span>|<span data-ttu-id="9f55b-107">Description</span><span class="sxs-lookup"><span data-stu-id="9f55b-107">Description</span></span>|  
|------------|-----------------|  
|`MDNotifyDefault`|<span data-ttu-id="9f55b-108">Upozorní, `mdTypeRef` Když `mdMethodDef` se `mdMemberRef` `mdFieldDef` tokeny přesunou,, nebo.</span><span class="sxs-lookup"><span data-stu-id="9f55b-108">Notify when `mdTypeRef`, `mdMethodDef`, `mdMemberRef`, or `mdFieldDef` tokens move.</span></span>|  
|`MDNotifyAll`|<span data-ttu-id="9f55b-109">Upozorní, když se libovolný token přesune.</span><span class="sxs-lookup"><span data-stu-id="9f55b-109">Notify when any token moves.</span></span>|  
|`MDNotifyNone`|<span data-ttu-id="9f55b-110">Neupozorňovat při přesunu tokenů</span><span class="sxs-lookup"><span data-stu-id="9f55b-110">Do not notify when tokens move.</span></span>|  
|`MDNotifyMethodDef`|<span data-ttu-id="9f55b-111">Upozorní, když se `mdMethodDef` token přesune.</span><span class="sxs-lookup"><span data-stu-id="9f55b-111">Notify when an `mdMethodDef` token moves.</span></span>|  
|`MDNotifyMemberRef`|<span data-ttu-id="9f55b-112">Upozorní, když se `mdMemberRef` token přesune.</span><span class="sxs-lookup"><span data-stu-id="9f55b-112">Notify when an `mdMemberRef` token moves.</span></span>|  
|`MDNotifyFieldDef`|<span data-ttu-id="9f55b-113">Upozorní, když se `mdFieldDef` token přesune.</span><span class="sxs-lookup"><span data-stu-id="9f55b-113">Notify when an `mdFieldDef` token moves.</span></span>|  
|`MDNotifyTypeRef`|<span data-ttu-id="9f55b-114">Upozorní, když se `mdTypeRef` token přesune.</span><span class="sxs-lookup"><span data-stu-id="9f55b-114">Notify when an `mdTypeRef` token moves.</span></span>|  
|`MDNotifyTypeDef`|<span data-ttu-id="9f55b-115">Upozorní, když se `mdTypeDef` token přesune.</span><span class="sxs-lookup"><span data-stu-id="9f55b-115">Notify when an `mdTypeDef` token moves.</span></span>|  
|`MDNotifyParamDef`|<span data-ttu-id="9f55b-116">Upozorní, když se `mdParamDef` token přesune.</span><span class="sxs-lookup"><span data-stu-id="9f55b-116">Notify when an `mdParamDef` token moves.</span></span>|  
|`MDNotifyInterfaceImpl`|<span data-ttu-id="9f55b-117">Upozorní, když se `mdInterfaceImpl` token přesune.</span><span class="sxs-lookup"><span data-stu-id="9f55b-117">Notify when an `mdInterfaceImpl` token moves.</span></span>|  
|`MDNotifyProperty`|<span data-ttu-id="9f55b-118">Upozorní, když se `mdProperty` token přesune.</span><span class="sxs-lookup"><span data-stu-id="9f55b-118">Notify when an `mdProperty` token moves.</span></span>|  
|`MDNotifyEvent`|<span data-ttu-id="9f55b-119">Upozorní, když se `mdEvent` token přesune.</span><span class="sxs-lookup"><span data-stu-id="9f55b-119">Notify when an `mdEvent` token moves.</span></span>|  
|`MDNotifySignature`|<span data-ttu-id="9f55b-120">Upozorní, když se `mdSignature` token přesune.</span><span class="sxs-lookup"><span data-stu-id="9f55b-120">Notify when an `mdSignature` token moves.</span></span>|  
|`MDNotifyTypeSpec`|<span data-ttu-id="9f55b-121">Upozorní, když se `mdTypeSpec` token přesune.</span><span class="sxs-lookup"><span data-stu-id="9f55b-121">Notify when an `mdTypeSpec` token moves.</span></span>|  
|`MDNotifyCustomAttribute`|<span data-ttu-id="9f55b-122">Upozorní, když se `mdCustomAttribute` token přesune.</span><span class="sxs-lookup"><span data-stu-id="9f55b-122">Notify when an `mdCustomAttribute` token moves.</span></span>|  
|`MDNotifySecurityValue`|<span data-ttu-id="9f55b-123">Upozorní, když se `mdSecurityValue` token přesune.</span><span class="sxs-lookup"><span data-stu-id="9f55b-123">Notify when an `mdSecurityValue` token moves.</span></span>|  
|`MDNotifyPermission`|<span data-ttu-id="9f55b-124">Upozorní, když se `mdPermission` token přesune.</span><span class="sxs-lookup"><span data-stu-id="9f55b-124">Notify when an `mdPermission` token moves.</span></span>|  
|`MDNotifyModuleRef`|<span data-ttu-id="9f55b-125">Upozorní, když se `mdModuleRef` token přesune.</span><span class="sxs-lookup"><span data-stu-id="9f55b-125">Notify when an `mdModuleRef` token moves.</span></span>|  
|`MDNotifyNameSpace`|<span data-ttu-id="9f55b-126">Upozorní, když se `mdNameSpace` token přesune.</span><span class="sxs-lookup"><span data-stu-id="9f55b-126">Notify when an `mdNameSpace` token moves.</span></span>|  
|`MDNotifyAssemblyRef`|<span data-ttu-id="9f55b-127">Upozorní, když se `mdAssemblyRef` token přesune.</span><span class="sxs-lookup"><span data-stu-id="9f55b-127">Notify when an `mdAssemblyRef` token moves.</span></span>|  
|`MDNotifyFile`|<span data-ttu-id="9f55b-128">Upozorní, když se `mdFile` token přesune.</span><span class="sxs-lookup"><span data-stu-id="9f55b-128">Notify when an `mdFile` token moves.</span></span>|  
|`MDNotifyExportedType`|<span data-ttu-id="9f55b-129">Upozorní, když se `mdExportedType` token přesune.</span><span class="sxs-lookup"><span data-stu-id="9f55b-129">Notify when an `mdExportedType` token moves.</span></span>|  
|`MDNotifyResource`|<span data-ttu-id="9f55b-130">Upozorní, když se `mdManifestResource` token přesune.</span><span class="sxs-lookup"><span data-stu-id="9f55b-130">Notify when an `mdManifestResource` token moves.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f55b-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9f55b-131">Remarks</span></span>  
 <span data-ttu-id="9f55b-132">Token se dá při sloučení metadat znovu namapovat (tj., to je přesunutý).</span><span class="sxs-lookup"><span data-stu-id="9f55b-132">A token may be re-mapped (that is, moved) during a metadata merge.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f55b-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9f55b-133">Requirements</span></span>  
 <span data-ttu-id="9f55b-134">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f55b-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f55b-135">**Hlavička:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="9f55b-135">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="9f55b-136">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f55b-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f55b-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="9f55b-137">See also</span></span>

- [<span data-ttu-id="9f55b-138">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="9f55b-138">Metadata Enumerations</span></span>](metadata-enumerations.md)
