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
ms.openlocfilehash: ee1cfe52caa9d727a132d7adc23b03575293db65
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716775"
---
# <a name="corvalidatormoduletype-enumeration"></a><span data-ttu-id="b6c0a-102">CorValidatorModuleType – výčet</span><span class="sxs-lookup"><span data-stu-id="b6c0a-102">CorValidatorModuleType Enumeration</span></span>
<span data-ttu-id="b6c0a-103">Určuje typ modulu.</span><span class="sxs-lookup"><span data-stu-id="b6c0a-103">Specifies the type of a module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6c0a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6c0a-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="b6c0a-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b6c0a-105">Members</span></span>  
  
|<span data-ttu-id="b6c0a-106">Člen</span><span class="sxs-lookup"><span data-stu-id="b6c0a-106">Member</span></span>|<span data-ttu-id="b6c0a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b6c0a-107">Description</span></span>|  
|------------|-----------------|  
|`ValidatorModuleTypeInvalid`|<span data-ttu-id="b6c0a-108">Modul je neplatného typu.</span><span class="sxs-lookup"><span data-stu-id="b6c0a-108">The module is an invalid type.</span></span>|  
|`ValidatorModuleTypeMin`|<span data-ttu-id="b6c0a-109">Minimální hodnota `CorValidatorModuleType` výčtu.</span><span class="sxs-lookup"><span data-stu-id="b6c0a-109">The minimum value of the `CorValidatorModuleType` enum.</span></span>|  
|`ValidatorModuleTypePE`|<span data-ttu-id="b6c0a-110">Modul je soubor (PE portable executable).</span><span class="sxs-lookup"><span data-stu-id="b6c0a-110">The module is a portable executable (PE) file.</span></span>|  
|`ValidatorModuleTypeObj`|<span data-ttu-id="b6c0a-111">Modul je soubor .obj.</span><span class="sxs-lookup"><span data-stu-id="b6c0a-111">The module is a .obj file.</span></span>|  
|`ValidatorModuleTypeEnc`|<span data-ttu-id="b6c0a-112">Modul je relace ladicího programu edit-and-continue.</span><span class="sxs-lookup"><span data-stu-id="b6c0a-112">The module is an edit-and-continue debugger session.</span></span>|  
|`ValidatorModuleTypeIncr`|<span data-ttu-id="b6c0a-113">Modul je postupně sestavena.</span><span class="sxs-lookup"><span data-stu-id="b6c0a-113">The module is one that has been incrementally built.</span></span>|  
|`ValidatorModuleTypeMax`|<span data-ttu-id="b6c0a-114">Maximální hodnota `CorValidatorModuleType` výčtu.</span><span class="sxs-lookup"><span data-stu-id="b6c0a-114">The maximum value of the `CorValidatorModuleType` enum.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b6c0a-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b6c0a-115">Requirements</span></span>  
 <span data-ttu-id="b6c0a-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6c0a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6c0a-117">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b6c0a-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b6c0a-118">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b6c0a-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b6c0a-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6c0a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6c0a-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b6c0a-120">See also</span></span>
- [<span data-ttu-id="b6c0a-121">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="b6c0a-121">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
