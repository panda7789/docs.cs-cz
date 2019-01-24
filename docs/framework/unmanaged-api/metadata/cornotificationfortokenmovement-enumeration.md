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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 745ba18fd1a36789f06bcd3dd4d183c9b28b9875
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54650103"
---
# <a name="cornotificationfortokenmovement-enumeration"></a><span data-ttu-id="d0c37-102">CorNotificationForTokenMovement – výčet</span><span class="sxs-lookup"><span data-stu-id="d0c37-102">CorNotificationForTokenMovement Enumeration</span></span>
<span data-ttu-id="d0c37-103">Určuje oznámení, které se odešlou do metadat rozhraní API klienta, když dojde k tokenu přemapování.</span><span class="sxs-lookup"><span data-stu-id="d0c37-103">Specifies the notifications that will be sent to the metadata API client when a token remap occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0c37-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0c37-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="d0c37-105">Členové</span><span class="sxs-lookup"><span data-stu-id="d0c37-105">Members</span></span>  
  
|<span data-ttu-id="d0c37-106">Člen</span><span class="sxs-lookup"><span data-stu-id="d0c37-106">Member</span></span>|<span data-ttu-id="d0c37-107">Popis</span><span class="sxs-lookup"><span data-stu-id="d0c37-107">Description</span></span>|  
|------------|-----------------|  
|`MDNotifyDefault`|<span data-ttu-id="d0c37-108">Upozornit při `mdTypeRef`, `mdMethodDef`, `mdMemberRef`, nebo `mdFieldDef` přesunout tokeny.</span><span class="sxs-lookup"><span data-stu-id="d0c37-108">Notify when `mdTypeRef`, `mdMethodDef`, `mdMemberRef`, or `mdFieldDef` tokens move.</span></span>|  
|`MDNotifyAll`|<span data-ttu-id="d0c37-109">Upozorněte při přesunu žádný token.</span><span class="sxs-lookup"><span data-stu-id="d0c37-109">Notify when any token moves.</span></span>|  
|`MDNotifyNone`|<span data-ttu-id="d0c37-110">Upozorňován přesunout tokeny.</span><span class="sxs-lookup"><span data-stu-id="d0c37-110">Do not notify when tokens move.</span></span>|  
|`MDNotifyMethodDef`|<span data-ttu-id="d0c37-111">Upozornit při `mdMethodDef` přesune token.</span><span class="sxs-lookup"><span data-stu-id="d0c37-111">Notify when an `mdMethodDef` token moves.</span></span>|  
|`MDNotifyMemberRef`|<span data-ttu-id="d0c37-112">Upozornit při `mdMemberRef` přesune token.</span><span class="sxs-lookup"><span data-stu-id="d0c37-112">Notify when an `mdMemberRef` token moves.</span></span>|  
|`MDNotifyFieldDef`|<span data-ttu-id="d0c37-113">Upozornit při `mdFieldDef` přesune token.</span><span class="sxs-lookup"><span data-stu-id="d0c37-113">Notify when an `mdFieldDef` token moves.</span></span>|  
|`MDNotifyTypeRef`|<span data-ttu-id="d0c37-114">Upozornit při `mdTypeRef` přesune token.</span><span class="sxs-lookup"><span data-stu-id="d0c37-114">Notify when an `mdTypeRef` token moves.</span></span>|  
|`MDNotifyTypeDef`|<span data-ttu-id="d0c37-115">Upozornit při `mdTypeDef` přesune token.</span><span class="sxs-lookup"><span data-stu-id="d0c37-115">Notify when an `mdTypeDef` token moves.</span></span>|  
|`MDNotifyParamDef`|<span data-ttu-id="d0c37-116">Upozornit při `mdParamDef` přesune token.</span><span class="sxs-lookup"><span data-stu-id="d0c37-116">Notify when an `mdParamDef` token moves.</span></span>|  
|`MDNotifyInterfaceImpl`|<span data-ttu-id="d0c37-117">Upozornit při `mdInterfaceImpl` přesune token.</span><span class="sxs-lookup"><span data-stu-id="d0c37-117">Notify when an `mdInterfaceImpl` token moves.</span></span>|  
|`MDNotifyProperty`|<span data-ttu-id="d0c37-118">Upozornit při `mdProperty` přesune token.</span><span class="sxs-lookup"><span data-stu-id="d0c37-118">Notify when an `mdProperty` token moves.</span></span>|  
|`MDNotifyEvent`|<span data-ttu-id="d0c37-119">Upozornit při `mdEvent` přesune token.</span><span class="sxs-lookup"><span data-stu-id="d0c37-119">Notify when an `mdEvent` token moves.</span></span>|  
|`MDNotifySignature`|<span data-ttu-id="d0c37-120">Upozornit při `mdSignature` přesune token.</span><span class="sxs-lookup"><span data-stu-id="d0c37-120">Notify when an `mdSignature` token moves.</span></span>|  
|`MDNotifyTypeSpec`|<span data-ttu-id="d0c37-121">Upozornit při `mdTypeSpec` přesune token.</span><span class="sxs-lookup"><span data-stu-id="d0c37-121">Notify when an `mdTypeSpec` token moves.</span></span>|  
|`MDNotifyCustomAttribute`|<span data-ttu-id="d0c37-122">Upozornit při `mdCustomAttribute` přesune token.</span><span class="sxs-lookup"><span data-stu-id="d0c37-122">Notify when an `mdCustomAttribute` token moves.</span></span>|  
|`MDNotifySecurityValue`|<span data-ttu-id="d0c37-123">Upozornit při `mdSecurityValue` přesune token.</span><span class="sxs-lookup"><span data-stu-id="d0c37-123">Notify when an `mdSecurityValue` token moves.</span></span>|  
|`MDNotifyPermission`|<span data-ttu-id="d0c37-124">Upozornit při `mdPermission` přesune token.</span><span class="sxs-lookup"><span data-stu-id="d0c37-124">Notify when an `mdPermission` token moves.</span></span>|  
|`MDNotifyModuleRef`|<span data-ttu-id="d0c37-125">Upozornit při `mdModuleRef` přesune token.</span><span class="sxs-lookup"><span data-stu-id="d0c37-125">Notify when an `mdModuleRef` token moves.</span></span>|  
|`MDNotifyNameSpace`|<span data-ttu-id="d0c37-126">Upozornit při `mdNameSpace` přesune token.</span><span class="sxs-lookup"><span data-stu-id="d0c37-126">Notify when an `mdNameSpace` token moves.</span></span>|  
|`MDNotifyAssemblyRef`|<span data-ttu-id="d0c37-127">Upozornit při `mdAssemblyRef` přesune token.</span><span class="sxs-lookup"><span data-stu-id="d0c37-127">Notify when an `mdAssemblyRef` token moves.</span></span>|  
|`MDNotifyFile`|<span data-ttu-id="d0c37-128">Upozornit při `mdFile` přesune token.</span><span class="sxs-lookup"><span data-stu-id="d0c37-128">Notify when an `mdFile` token moves.</span></span>|  
|`MDNotifyExportedType`|<span data-ttu-id="d0c37-129">Upozornit při `mdExportedType` přesune token.</span><span class="sxs-lookup"><span data-stu-id="d0c37-129">Notify when an `mdExportedType` token moves.</span></span>|  
|`MDNotifyResource`|<span data-ttu-id="d0c37-130">Upozornit při `mdManifestResource` přesune token.</span><span class="sxs-lookup"><span data-stu-id="d0c37-130">Notify when an `mdManifestResource` token moves.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0c37-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d0c37-131">Remarks</span></span>  
 <span data-ttu-id="d0c37-132">Token může být znovu namapována (přesunuté,) během metadat sloučení.</span><span class="sxs-lookup"><span data-stu-id="d0c37-132">A token may be re-mapped (that is, moved) during a metadata merge.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0c37-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d0c37-133">Requirements</span></span>  
 <span data-ttu-id="d0c37-134">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0c37-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0c37-135">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="d0c37-135">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="d0c37-136">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0c37-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0c37-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d0c37-137">See also</span></span>
- [<span data-ttu-id="d0c37-138">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="d0c37-138">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
