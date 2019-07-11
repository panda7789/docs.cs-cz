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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 04bed418d96658e29328cf2ce6bba445639b437f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750759"
---
# <a name="corvalidatormoduletype-enumeration"></a><span data-ttu-id="13681-102">CorValidatorModuleType – výčet</span><span class="sxs-lookup"><span data-stu-id="13681-102">CorValidatorModuleType Enumeration</span></span>
<span data-ttu-id="13681-103">Určuje typ modulu.</span><span class="sxs-lookup"><span data-stu-id="13681-103">Specifies the type of a module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13681-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13681-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="13681-105">Členové</span><span class="sxs-lookup"><span data-stu-id="13681-105">Members</span></span>  
  
|<span data-ttu-id="13681-106">Člen</span><span class="sxs-lookup"><span data-stu-id="13681-106">Member</span></span>|<span data-ttu-id="13681-107">Popis</span><span class="sxs-lookup"><span data-stu-id="13681-107">Description</span></span>|  
|------------|-----------------|  
|`ValidatorModuleTypeInvalid`|<span data-ttu-id="13681-108">Modul je neplatného typu.</span><span class="sxs-lookup"><span data-stu-id="13681-108">The module is an invalid type.</span></span>|  
|`ValidatorModuleTypeMin`|<span data-ttu-id="13681-109">Minimální hodnota `CorValidatorModuleType` výčtu.</span><span class="sxs-lookup"><span data-stu-id="13681-109">The minimum value of the `CorValidatorModuleType` enum.</span></span>|  
|`ValidatorModuleTypePE`|<span data-ttu-id="13681-110">Modul je soubor (PE portable executable).</span><span class="sxs-lookup"><span data-stu-id="13681-110">The module is a portable executable (PE) file.</span></span>|  
|`ValidatorModuleTypeObj`|<span data-ttu-id="13681-111">Modul je soubor .obj.</span><span class="sxs-lookup"><span data-stu-id="13681-111">The module is a .obj file.</span></span>|  
|`ValidatorModuleTypeEnc`|<span data-ttu-id="13681-112">Modul je relace ladicího programu edit-and-continue.</span><span class="sxs-lookup"><span data-stu-id="13681-112">The module is an edit-and-continue debugger session.</span></span>|  
|`ValidatorModuleTypeIncr`|<span data-ttu-id="13681-113">Modul je postupně sestavena.</span><span class="sxs-lookup"><span data-stu-id="13681-113">The module is one that has been incrementally built.</span></span>|  
|`ValidatorModuleTypeMax`|<span data-ttu-id="13681-114">Maximální hodnota `CorValidatorModuleType` výčtu.</span><span class="sxs-lookup"><span data-stu-id="13681-114">The maximum value of the `CorValidatorModuleType` enum.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="13681-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="13681-115">Requirements</span></span>  
 <span data-ttu-id="13681-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13681-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13681-117">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="13681-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="13681-118">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="13681-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="13681-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13681-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13681-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="13681-120">See also</span></span>

- [<span data-ttu-id="13681-121">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="13681-121">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
