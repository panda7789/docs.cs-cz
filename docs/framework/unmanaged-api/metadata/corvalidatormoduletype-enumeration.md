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
ms.openlocfilehash: 97e9ae5a7c35b4f9b6e2b4ca7e754b5b7480dfa6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444136"
---
# <a name="corvalidatormoduletype-enumeration"></a><span data-ttu-id="a6674-102">CorValidatorModuleType – výčet</span><span class="sxs-lookup"><span data-stu-id="a6674-102">CorValidatorModuleType Enumeration</span></span>
<span data-ttu-id="a6674-103">Určuje typ modulu.</span><span class="sxs-lookup"><span data-stu-id="a6674-103">Specifies the type of a module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6674-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6674-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="a6674-105">Členové</span><span class="sxs-lookup"><span data-stu-id="a6674-105">Members</span></span>  
  
|<span data-ttu-id="a6674-106">Člen</span><span class="sxs-lookup"><span data-stu-id="a6674-106">Member</span></span>|<span data-ttu-id="a6674-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a6674-107">Description</span></span>|  
|------------|-----------------|  
|`ValidatorModuleTypeInvalid`|<span data-ttu-id="a6674-108">Modul je neplatného typu.</span><span class="sxs-lookup"><span data-stu-id="a6674-108">The module is an invalid type.</span></span>|  
|`ValidatorModuleTypeMin`|<span data-ttu-id="a6674-109">Minimální hodnota `CorValidatorModuleType` výčtu.</span><span class="sxs-lookup"><span data-stu-id="a6674-109">The minimum value of the `CorValidatorModuleType` enum.</span></span>|  
|`ValidatorModuleTypePE`|<span data-ttu-id="a6674-110">Modul je soubor přenosné spustitelný soubor (PE).</span><span class="sxs-lookup"><span data-stu-id="a6674-110">The module is a portable executable (PE) file.</span></span>|  
|`ValidatorModuleTypeObj`|<span data-ttu-id="a6674-111">Modul je soubor .obj.</span><span class="sxs-lookup"><span data-stu-id="a6674-111">The module is a .obj file.</span></span>|  
|`ValidatorModuleTypeEnc`|<span data-ttu-id="a6674-112">Modul je relaci upravit a pokračovat ladicí program.</span><span class="sxs-lookup"><span data-stu-id="a6674-112">The module is an edit-and-continue debugger session.</span></span>|  
|`ValidatorModuleTypeIncr`|<span data-ttu-id="a6674-113">Modul je ten, který přírůstkově sestaven.</span><span class="sxs-lookup"><span data-stu-id="a6674-113">The module is one that has been incrementally built.</span></span>|  
|`ValidatorModuleTypeMax`|<span data-ttu-id="a6674-114">Maximální hodnota, která `CorValidatorModuleType` výčtu.</span><span class="sxs-lookup"><span data-stu-id="a6674-114">The maximum value of the `CorValidatorModuleType` enum.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a6674-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a6674-115">Requirements</span></span>  
 <span data-ttu-id="a6674-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6674-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6674-117">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a6674-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a6674-118">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a6674-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a6674-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6674-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6674-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="a6674-120">See Also</span></span>  
 [<span data-ttu-id="a6674-121">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="a6674-121">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
