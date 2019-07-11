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
ms.openlocfilehash: 871ad81cd83c40d7299f39ede404e274b95b2ac0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778455"
---
# <a name="createasmnameobjflags-enumeration"></a><span data-ttu-id="16b6c-102">CREATE_ASM_NAME_OBJ_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="16b6c-102">CREATE_ASM_NAME_OBJ_FLAGS Enumeration</span></span>
<span data-ttu-id="16b6c-103">Určuje atributy [iassemblyname – rozhraní](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) objektu při jejím vytváření pomocí [createassemblynameobject –](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="16b6c-103">Specifies the attributes of an [IAssemblyName Interface](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object when it is constructed by the [CreateAssemblyNameObject](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16b6c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="16b6c-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
  
    CANOF_PARSE_DISPLAY_NAME            = 0x1,  
    CANOF_SET_DEFAULT_VALUES            = 0x2,  
    CANOF_VERIFY_FRIEND_ASSEMBLYNAME    = 0x4,  
    CANOF_PARSE_FRIEND_DISPLAY_NAME     =   
        CANOF_PARSE_DISPLAY_NAME | CANOF_VERIFY_FRIEND_ASSEMBLYNAME  
  
} CREATE_ASM_NAME_OBJ_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="16b6c-105">Členové</span><span class="sxs-lookup"><span data-stu-id="16b6c-105">Members</span></span>  
  
|<span data-ttu-id="16b6c-106">Člen</span><span class="sxs-lookup"><span data-stu-id="16b6c-106">Member</span></span>|<span data-ttu-id="16b6c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="16b6c-107">Description</span></span>|  
|------------|-----------------|  
|`CANOF_PARSE_DISPLAY_NAME`|<span data-ttu-id="16b6c-108">Označuje, že je parametr předaný textovou identitu.</span><span class="sxs-lookup"><span data-stu-id="16b6c-108">Indicates that the parameter passed is a textual identity.</span></span>|  
|`CANOF_SET_DEFAULT_VALUES`|<span data-ttu-id="16b6c-109">Nastaví několik výchozích hodnot.</span><span class="sxs-lookup"><span data-stu-id="16b6c-109">Sets a few default values.</span></span>|  
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|<span data-ttu-id="16b6c-110">Ověří pravidla sestavení typu friend (pouze název a veřejný klíč).</span><span class="sxs-lookup"><span data-stu-id="16b6c-110">Verifies the friend assembly rule (only name and public key).</span></span> <span data-ttu-id="16b6c-111">Tento člen je jen pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="16b6c-111">This member is for internal use only.</span></span>|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|<span data-ttu-id="16b6c-112">Kombinace `CANOF_PARSE_DISPLAY_NAME` a `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` příznaky.</span><span class="sxs-lookup"><span data-stu-id="16b6c-112">A combination of the `CANOF_PARSE_DISPLAY_NAME` and `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` flags.</span></span> <span data-ttu-id="16b6c-113">Tento člen je jen pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="16b6c-113">This member is for internal use only.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="16b6c-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="16b6c-114">Requirements</span></span>  
 <span data-ttu-id="16b6c-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16b6c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16b6c-116">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="16b6c-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="16b6c-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16b6c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16b6c-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="16b6c-118">See also</span></span>

- [<span data-ttu-id="16b6c-119">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="16b6c-119">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="16b6c-120">CreateAssemblyNameObject – funkce</span><span class="sxs-lookup"><span data-stu-id="16b6c-120">CreateAssemblyNameObject Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)
- [<span data-ttu-id="16b6c-121">Výčty pro fúze</span><span class="sxs-lookup"><span data-stu-id="16b6c-121">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
