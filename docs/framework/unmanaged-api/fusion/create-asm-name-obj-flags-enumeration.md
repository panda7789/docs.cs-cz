---
title: "CREATE_ASM_NAME_OBJ_FLAGS – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CREATE_ASM_NAME_OBJ_FLAGS
api_location: fusion.dll
api_type: COM
f1_keywords: CREATE_ASM_NAME_OBJ_FLAGS
helpviewer_keywords: CREATE_ASM_NAME_OBJ_FLAGS enumeration [.NET Framework fusion]
ms.assetid: a5ed2fd0-c7d2-4603-aaca-5d0caad92675
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4982b33643d855be4b8cace59f1c5cac4201d5ac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="createasmnameobjflags-enumeration"></a><span data-ttu-id="4e56f-102">CREATE_ASM_NAME_OBJ_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="4e56f-102">CREATE_ASM_NAME_OBJ_FLAGS Enumeration</span></span>
<span data-ttu-id="4e56f-103">Určuje atributy [iassemblyname – rozhraní](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) objektu, když je vytvořený pomocí [createassemblynameobject –](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="4e56f-103">Specifies the attributes of an [IAssemblyName Interface](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object when it is constructed by the [CreateAssemblyNameObject](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e56f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e56f-104">Syntax</span></span>  
  
```  
typedef enum {  
  
    CANOF_PARSE_DISPLAY_NAME            = 0x1,  
    CANOF_SET_DEFAULT_VALUES            = 0x2,  
    CANOF_VERIFY_FRIEND_ASSEMBLYNAME    = 0x4,  
    CANOF_PARSE_FRIEND_DISPLAY_NAME     =   
        CANOF_PARSE_DISPLAY_NAME | CANOF_VERIFY_FRIEND_ASSEMBLYNAME  
  
} CREATE_ASM_NAME_OBJ_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="4e56f-105">Členové</span><span class="sxs-lookup"><span data-stu-id="4e56f-105">Members</span></span>  
  
|<span data-ttu-id="4e56f-106">Člen</span><span class="sxs-lookup"><span data-stu-id="4e56f-106">Member</span></span>|<span data-ttu-id="4e56f-107">Popis</span><span class="sxs-lookup"><span data-stu-id="4e56f-107">Description</span></span>|  
|------------|-----------------|  
|`CANOF_PARSE_DISPLAY_NAME`|<span data-ttu-id="4e56f-108">Označuje, že je parametr předaný textovou identity.</span><span class="sxs-lookup"><span data-stu-id="4e56f-108">Indicates that the parameter passed is a textual identity.</span></span>|  
|`CANOF_SET_DEFAULT_VALUES`|<span data-ttu-id="4e56f-109">Nastaví několik výchozích hodnot.</span><span class="sxs-lookup"><span data-stu-id="4e56f-109">Sets a few default values.</span></span>|  
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|<span data-ttu-id="4e56f-110">Ověřuje, přítele pravidlo sestavení (pouze název a veřejný klíč).</span><span class="sxs-lookup"><span data-stu-id="4e56f-110">Verifies the friend assembly rule (only name and public key).</span></span> <span data-ttu-id="4e56f-111">Tento člen je jen pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="4e56f-111">This member is for internal use only.</span></span>|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|<span data-ttu-id="4e56f-112">Kombinace `CANOF_PARSE_DISPLAY_NAME` a `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` příznaky.</span><span class="sxs-lookup"><span data-stu-id="4e56f-112">A combination of the `CANOF_PARSE_DISPLAY_NAME` and `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` flags.</span></span> <span data-ttu-id="4e56f-113">Tento člen je jen pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="4e56f-113">This member is for internal use only.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4e56f-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4e56f-114">Requirements</span></span>  
 <span data-ttu-id="4e56f-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e56f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e56f-116">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="4e56f-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="4e56f-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e56f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e56f-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="4e56f-118">See Also</span></span>  
 [<span data-ttu-id="4e56f-119">Iassemblyname – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4e56f-119">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="4e56f-120">Createassemblynameobject – funkce</span><span class="sxs-lookup"><span data-stu-id="4e56f-120">CreateAssemblyNameObject Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)  
 [<span data-ttu-id="4e56f-121">Výčty fúzí</span><span class="sxs-lookup"><span data-stu-id="4e56f-121">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
