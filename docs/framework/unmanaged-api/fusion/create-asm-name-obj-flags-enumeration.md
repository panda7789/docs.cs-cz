---
title: CREATE_ASM_NAME_OBJ_FLAGS – výčet
ms.date: 03/30/2017
api_name:
- CREATE_ASM_NAME_OBJ_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- CREATE_ASM_NAME_OBJ_FLAGS
helpviewer_keywords:
- CREATE_ASM_NAME_OBJ_FLAGS enumeration [.NET Framework fusion]
ms.assetid: a5ed2fd0-c7d2-4603-aaca-5d0caad92675
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9897e396424b9076da8f30c61b5a14cfa9539690
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795420"
---
# <a name="create_asm_name_obj_flags-enumeration"></a><span data-ttu-id="2a9bd-102">CREATE_ASM_NAME_OBJ_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="2a9bd-102">CREATE_ASM_NAME_OBJ_FLAGS Enumeration</span></span>
<span data-ttu-id="2a9bd-103">Určuje atributy objektu [rozhraní IAssemblyName](iassemblyname-interface.md) , když je vytvořen funkcí [CreateAssemblyNameObject –](createassemblynameobject-function.md) .</span><span class="sxs-lookup"><span data-stu-id="2a9bd-103">Specifies the attributes of an [IAssemblyName Interface](iassemblyname-interface.md) object when it is constructed by the [CreateAssemblyNameObject](createassemblynameobject-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a9bd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2a9bd-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
  
    CANOF_PARSE_DISPLAY_NAME            = 0x1,  
    CANOF_SET_DEFAULT_VALUES            = 0x2,  
    CANOF_VERIFY_FRIEND_ASSEMBLYNAME    = 0x4,  
    CANOF_PARSE_FRIEND_DISPLAY_NAME     =   
        CANOF_PARSE_DISPLAY_NAME | CANOF_VERIFY_FRIEND_ASSEMBLYNAME  
  
} CREATE_ASM_NAME_OBJ_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="2a9bd-105">Členové</span><span class="sxs-lookup"><span data-stu-id="2a9bd-105">Members</span></span>  
  
|<span data-ttu-id="2a9bd-106">Člen</span><span class="sxs-lookup"><span data-stu-id="2a9bd-106">Member</span></span>|<span data-ttu-id="2a9bd-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2a9bd-107">Description</span></span>|  
|------------|-----------------|  
|`CANOF_PARSE_DISPLAY_NAME`|<span data-ttu-id="2a9bd-108">Označuje, že předaný parametr je textová identita.</span><span class="sxs-lookup"><span data-stu-id="2a9bd-108">Indicates that the parameter passed is a textual identity.</span></span>|  
|`CANOF_SET_DEFAULT_VALUES`|<span data-ttu-id="2a9bd-109">Nastaví několik výchozích hodnot.</span><span class="sxs-lookup"><span data-stu-id="2a9bd-109">Sets a few default values.</span></span>|  
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|<span data-ttu-id="2a9bd-110">Ověří pravidlo sestavení typu Friend (pouze název a veřejný klíč).</span><span class="sxs-lookup"><span data-stu-id="2a9bd-110">Verifies the friend assembly rule (only name and public key).</span></span> <span data-ttu-id="2a9bd-111">Tento člen je určen pouze pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="2a9bd-111">This member is for internal use only.</span></span>|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|<span data-ttu-id="2a9bd-112">Kombinace `CANOF_PARSE_DISPLAY_NAME` příznaků a `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` .</span><span class="sxs-lookup"><span data-stu-id="2a9bd-112">A combination of the `CANOF_PARSE_DISPLAY_NAME` and `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` flags.</span></span> <span data-ttu-id="2a9bd-113">Tento člen je určen pouze pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="2a9bd-113">This member is for internal use only.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2a9bd-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2a9bd-114">Requirements</span></span>  
 <span data-ttu-id="2a9bd-115">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a9bd-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a9bd-116">**Hlaviček** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="2a9bd-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="2a9bd-117">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a9bd-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a9bd-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2a9bd-118">See also</span></span>

- [<span data-ttu-id="2a9bd-119">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2a9bd-119">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="2a9bd-120">CreateAssemblyNameObject – funkce</span><span class="sxs-lookup"><span data-stu-id="2a9bd-120">CreateAssemblyNameObject Function</span></span>](createassemblynameobject-function.md)
- [<span data-ttu-id="2a9bd-121">Výčty pro fúze</span><span class="sxs-lookup"><span data-stu-id="2a9bd-121">Fusion Enumerations</span></span>](fusion-enumerations.md)
