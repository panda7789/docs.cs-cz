---
title: CorValidatorModuleType – výčet
ms.date: 03/30/2017
api_name:
- CorValidatorModuleType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorValidatorModuleType
helpviewer_keywords:
- CorValidatorModuleType enumeration [.NET Framework metadata]
ms.assetid: 748f1ab2-fbcb-4f55-89ec-8d23d81ebc80
topic_type:
- apiref
ms.openlocfilehash: a8dc09ee9f0f0fd79060bb86c599ab40a285153b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448757"
---
# <a name="corvalidatormoduletype-enumeration"></a><span data-ttu-id="60482-102">CorValidatorModuleType – výčet</span><span class="sxs-lookup"><span data-stu-id="60482-102">CorValidatorModuleType Enumeration</span></span>
<span data-ttu-id="60482-103">Určuje typ modulu.</span><span class="sxs-lookup"><span data-stu-id="60482-103">Specifies the type of a module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60482-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60482-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{  
    ValidatorModuleTypeInvalid  = 0x0,  
    ValidatorModuleTypeMin      = 0x00000001,  
    ValidatorModuleTypePE       = 0x00000001,  
    ValidatorModuleTypeObj      = 0x00000002,  
    ValidatorModuleTypeEnc      = 0x00000003,  
    ValidatorModuleTypeIncr     = 0x00000004,  
    ValidatorModuleTypeMax      = 0x00000004  
} CorValidatorModuleType;  
```  
  
## <a name="members"></a><span data-ttu-id="60482-105">Members</span><span class="sxs-lookup"><span data-stu-id="60482-105">Members</span></span>  
  
|<span data-ttu-id="60482-106">Člen</span><span class="sxs-lookup"><span data-stu-id="60482-106">Member</span></span>|<span data-ttu-id="60482-107">Popis</span><span class="sxs-lookup"><span data-stu-id="60482-107">Description</span></span>|  
|------------|-----------------|  
|`ValidatorModuleTypeInvalid`|<span data-ttu-id="60482-108">Modul je neplatného typu.</span><span class="sxs-lookup"><span data-stu-id="60482-108">The module is an invalid type.</span></span>|  
|`ValidatorModuleTypeMin`|<span data-ttu-id="60482-109">Minimální hodnota výčtu `CorValidatorModuleType`.</span><span class="sxs-lookup"><span data-stu-id="60482-109">The minimum value of the `CorValidatorModuleType` enum.</span></span>|  
|`ValidatorModuleTypePE`|<span data-ttu-id="60482-110">Modul je přenosný spustitelný soubor (PE).</span><span class="sxs-lookup"><span data-stu-id="60482-110">The module is a portable executable (PE) file.</span></span>|  
|`ValidatorModuleTypeObj`|<span data-ttu-id="60482-111">Modul je soubor. obj.</span><span class="sxs-lookup"><span data-stu-id="60482-111">The module is a .obj file.</span></span>|  
|`ValidatorModuleTypeEnc`|<span data-ttu-id="60482-112">Modul je relace ladicího programu pro úpravy a pokračování.</span><span class="sxs-lookup"><span data-stu-id="60482-112">The module is an edit-and-continue debugger session.</span></span>|  
|`ValidatorModuleTypeIncr`|<span data-ttu-id="60482-113">Modul je ten, který se postupně sestavil.</span><span class="sxs-lookup"><span data-stu-id="60482-113">The module is one that has been incrementally built.</span></span>|  
|`ValidatorModuleTypeMax`|<span data-ttu-id="60482-114">Maximální hodnota výčtu `CorValidatorModuleType`.</span><span class="sxs-lookup"><span data-stu-id="60482-114">The maximum value of the `CorValidatorModuleType` enum.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="60482-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="60482-115">Requirements</span></span>  
 <span data-ttu-id="60482-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60482-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60482-117">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="60482-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="60482-118">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="60482-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="60482-119">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60482-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60482-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="60482-120">See also</span></span>

- [<span data-ttu-id="60482-121">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="60482-121">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
