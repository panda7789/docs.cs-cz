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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7024140ed9b870b5db38dba7e9b13321dd37386a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62046160"
---
# <a name="cornativelink-structure"></a><span data-ttu-id="3aa3b-102">COR_NATIVE_LINK – struktura</span><span class="sxs-lookup"><span data-stu-id="3aa3b-102">COR_NATIVE_LINK Structure</span></span>
<span data-ttu-id="3aa3b-103">Obsahuje informace, které slouží k propojení nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="3aa3b-103">Contains information that is used to link native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3aa3b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3aa3b-104">Syntax</span></span>  
  
```  
typedef struct   
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a><span data-ttu-id="3aa3b-105">Členové</span><span class="sxs-lookup"><span data-stu-id="3aa3b-105">Members</span></span>  
  
|<span data-ttu-id="3aa3b-106">Člen</span><span class="sxs-lookup"><span data-stu-id="3aa3b-106">Member</span></span>|<span data-ttu-id="3aa3b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="3aa3b-107">Description</span></span>|  
|------------|-----------------|  
|`m_linkType`|<span data-ttu-id="3aa3b-108">Typ propojení v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="3aa3b-108">The type to be linked in native code.</span></span> <span data-ttu-id="3aa3b-109">Tato hodnota je jedním z [cornativelinktype –](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) hodnoty.</span><span class="sxs-lookup"><span data-stu-id="3aa3b-109">This value is one of the [CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) values.</span></span>|  
|`m_flags`|<span data-ttu-id="3aa3b-110">Příznaky použité linkerem při propojování nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="3aa3b-110">Flags used by the linker when linking native code.</span></span> <span data-ttu-id="3aa3b-111">Tato hodnota je jedním z [cornativelinkflags –](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) hodnoty.</span><span class="sxs-lookup"><span data-stu-id="3aa3b-111">This value is one of the [CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) values.</span></span>|  
|`m_entryPoint`|<span data-ttu-id="3aa3b-112">Token MemberRef metadata, která představuje vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="3aa3b-112">The MemberRef metadata token that represents the entry point.</span></span> <span data-ttu-id="3aa3b-113">Formát je `lib:entrypoint`.</span><span class="sxs-lookup"><span data-stu-id="3aa3b-113">The format is `lib:entrypoint`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3aa3b-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3aa3b-114">Requirements</span></span>  
 <span data-ttu-id="3aa3b-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3aa3b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3aa3b-116">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3aa3b-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3aa3b-117">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3aa3b-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3aa3b-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3aa3b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3aa3b-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3aa3b-119">See also</span></span>

- [<span data-ttu-id="3aa3b-120">Struktury pro metadata</span><span class="sxs-lookup"><span data-stu-id="3aa3b-120">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="3aa3b-121">CorNativeLinkType – výčet</span><span class="sxs-lookup"><span data-stu-id="3aa3b-121">CorNativeLinkType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)
- [<span data-ttu-id="3aa3b-122">CorNativeLinkFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="3aa3b-122">CorNativeLinkFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)
