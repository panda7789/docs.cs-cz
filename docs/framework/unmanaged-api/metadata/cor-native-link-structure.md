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
ms.openlocfilehash: a11b7d5939c4c20504b1ff3dfb4613f85bca0db4
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007972"
---
# <a name="cor_native_link-structure"></a><span data-ttu-id="e178f-102">COR_NATIVE_LINK – struktura</span><span class="sxs-lookup"><span data-stu-id="e178f-102">COR_NATIVE_LINK Structure</span></span>
<span data-ttu-id="e178f-103">Obsahuje informace, které se používají k propojení nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="e178f-103">Contains information that is used to link native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e178f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e178f-104">Syntax</span></span>  
  
```cpp  
typedef struct
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a><span data-ttu-id="e178f-105">Členové</span><span class="sxs-lookup"><span data-stu-id="e178f-105">Members</span></span>  
  
|<span data-ttu-id="e178f-106">Člen</span><span class="sxs-lookup"><span data-stu-id="e178f-106">Member</span></span>|<span data-ttu-id="e178f-107">Description</span><span class="sxs-lookup"><span data-stu-id="e178f-107">Description</span></span>|  
|------------|-----------------|  
|`m_linkType`|<span data-ttu-id="e178f-108">Typ, který se má propojit v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="e178f-108">The type to be linked in native code.</span></span> <span data-ttu-id="e178f-109">Tato hodnota je jednou z hodnot [CorNativeLinkType –](cornativelinktype-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="e178f-109">This value is one of the [CorNativeLinkType](cornativelinktype-enumeration.md) values.</span></span>|  
|`m_flags`|<span data-ttu-id="e178f-110">Příznaky používané linkerem při propojování nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="e178f-110">Flags used by the linker when linking native code.</span></span> <span data-ttu-id="e178f-111">Tato hodnota je jednou z hodnot [CorNativeLinkFlags –](cornativelinkflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="e178f-111">This value is one of the [CorNativeLinkFlags](cornativelinkflags-enumeration.md) values.</span></span>|  
|`m_entryPoint`|<span data-ttu-id="e178f-112">Token metadat MemberRef, který představuje vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="e178f-112">The MemberRef metadata token that represents the entry point.</span></span> <span data-ttu-id="e178f-113">Formát je `lib:entrypoint`.</span><span class="sxs-lookup"><span data-stu-id="e178f-113">The format is `lib:entrypoint`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e178f-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e178f-114">Requirements</span></span>  
 <span data-ttu-id="e178f-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e178f-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e178f-116">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e178f-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e178f-117">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="e178f-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e178f-118">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e178f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e178f-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="e178f-119">See also</span></span>

- [<span data-ttu-id="e178f-120">Struktury pro metadata</span><span class="sxs-lookup"><span data-stu-id="e178f-120">Metadata Structures</span></span>](metadata-structures.md)
- [<span data-ttu-id="e178f-121">CorNativeLinkType – výčet</span><span class="sxs-lookup"><span data-stu-id="e178f-121">CorNativeLinkType Enumeration</span></span>](cornativelinktype-enumeration.md)
- [<span data-ttu-id="e178f-122">CorNativeLinkFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="e178f-122">CorNativeLinkFlags Enumeration</span></span>](cornativelinkflags-enumeration.md)
