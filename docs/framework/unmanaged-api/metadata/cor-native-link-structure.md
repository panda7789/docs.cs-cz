---
title: "COR_NATIVE_LINK – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_NATIVE_LINK
api_location: mscoree.dll
api_type: COM
f1_keywords: COR_NATIVE_LINK
helpviewer_keywords: COR_NATIVE_LINK structure [.NET Framework metadata]
ms.assetid: 6ef78d3c-1c69-4141-b687-dcb065b7a74d
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e27b66fce8a78ef0feb7ed10e77cc51fc1fe83c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="cornativelink-structure"></a><span data-ttu-id="a87bf-102">COR_NATIVE_LINK – struktura</span><span class="sxs-lookup"><span data-stu-id="a87bf-102">COR_NATIVE_LINK Structure</span></span>
<span data-ttu-id="a87bf-103">Obsahuje informace, které slouží k propojení nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="a87bf-103">Contains information that is used to link native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a87bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a87bf-104">Syntax</span></span>  
  
```  
typedef struct   
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a><span data-ttu-id="a87bf-105">Členové</span><span class="sxs-lookup"><span data-stu-id="a87bf-105">Members</span></span>  
  
|<span data-ttu-id="a87bf-106">Člen</span><span class="sxs-lookup"><span data-stu-id="a87bf-106">Member</span></span>|<span data-ttu-id="a87bf-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a87bf-107">Description</span></span>|  
|------------|-----------------|  
|`m_linkType`|<span data-ttu-id="a87bf-108">Typ, který má být propojena v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="a87bf-108">The type to be linked in native code.</span></span> <span data-ttu-id="a87bf-109">Tato hodnota je jedním z [CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a87bf-109">This value is one of the [CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) values.</span></span>|  
|`m_flags`|<span data-ttu-id="a87bf-110">Příznaky linkeru používá při propojování nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="a87bf-110">Flags used by the linker when linking native code.</span></span> <span data-ttu-id="a87bf-111">Tato hodnota je jedním z [CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a87bf-111">This value is one of the [CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) values.</span></span>|  
|`m_entryPoint`|<span data-ttu-id="a87bf-112">Token MemberRef metadata, která představuje vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="a87bf-112">The MemberRef metadata token that represents the entry point.</span></span> <span data-ttu-id="a87bf-113">Formát je `lib:entrypoint`.</span><span class="sxs-lookup"><span data-stu-id="a87bf-113">The format is `lib:entrypoint`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a87bf-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a87bf-114">Requirements</span></span>  
 <span data-ttu-id="a87bf-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a87bf-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a87bf-116">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a87bf-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a87bf-117">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a87bf-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a87bf-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a87bf-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a87bf-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="a87bf-119">See Also</span></span>  
 [<span data-ttu-id="a87bf-120">Struktury metadat</span><span class="sxs-lookup"><span data-stu-id="a87bf-120">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [<span data-ttu-id="a87bf-121">CorNativeLinkType – výčet</span><span class="sxs-lookup"><span data-stu-id="a87bf-121">CorNativeLinkType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)  
 [<span data-ttu-id="a87bf-122">CorNativeLinkFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="a87bf-122">CorNativeLinkFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)
