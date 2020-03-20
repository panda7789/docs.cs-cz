---
title: COR_NATIVE_LINK – struktura
ms.date: 03/30/2017
api_name:
- COR_NATIVE_LINK
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_NATIVE_LINK
helpviewer_keywords:
- COR_NATIVE_LINK structure [.NET Framework metadata]
ms.assetid: 6ef78d3c-1c69-4141-b687-dcb065b7a74d
topic_type:
- apiref
ms.openlocfilehash: 812b70a594b5aa933f52d36f32d96d712267ecf4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177962"
---
# <a name="cor_native_link-structure"></a><span data-ttu-id="e5903-102">COR_NATIVE_LINK – struktura</span><span class="sxs-lookup"><span data-stu-id="e5903-102">COR_NATIVE_LINK Structure</span></span>
<span data-ttu-id="e5903-103">Obsahuje informace, které se používají k propojení nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="e5903-103">Contains information that is used to link native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5903-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5903-104">Syntax</span></span>  
  
```cpp  
typedef struct
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a><span data-ttu-id="e5903-105">Členové</span><span class="sxs-lookup"><span data-stu-id="e5903-105">Members</span></span>  
  
|<span data-ttu-id="e5903-106">Člen</span><span class="sxs-lookup"><span data-stu-id="e5903-106">Member</span></span>|<span data-ttu-id="e5903-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e5903-107">Description</span></span>|  
|------------|-----------------|  
|`m_linkType`|<span data-ttu-id="e5903-108">Typ, který má být propojen v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="e5903-108">The type to be linked in native code.</span></span> <span data-ttu-id="e5903-109">Tato hodnota je jednou z hodnot [CorNativeLinkType.](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="e5903-109">This value is one of the [CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) values.</span></span>|  
|`m_flags`|<span data-ttu-id="e5903-110">Příznaky používané propojovacím programem při propojování nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="e5903-110">Flags used by the linker when linking native code.</span></span> <span data-ttu-id="e5903-111">Tato hodnota je jednou z hodnot [CorNativeLinkFlags.](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="e5903-111">This value is one of the [CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) values.</span></span>|  
|`m_entryPoint`|<span data-ttu-id="e5903-112">Token metadat MemberRef, který představuje vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="e5903-112">The MemberRef metadata token that represents the entry point.</span></span> <span data-ttu-id="e5903-113">Formát je `lib:entrypoint`.</span><span class="sxs-lookup"><span data-stu-id="e5903-113">The format is `lib:entrypoint`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e5903-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e5903-114">Requirements</span></span>  
 <span data-ttu-id="e5903-115">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5903-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5903-116">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="e5903-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e5903-117">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e5903-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e5903-118">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5903-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5903-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="e5903-119">See also</span></span>

- [<span data-ttu-id="e5903-120">Struktury pro metadata</span><span class="sxs-lookup"><span data-stu-id="e5903-120">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="e5903-121">CorNativeLinkType – výčet</span><span class="sxs-lookup"><span data-stu-id="e5903-121">CorNativeLinkType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)
- [<span data-ttu-id="e5903-122">CorNativeLinkFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="e5903-122">CorNativeLinkFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)
