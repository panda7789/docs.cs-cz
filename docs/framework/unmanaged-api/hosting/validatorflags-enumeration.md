---
title: ValidatorFlags – výčet
ms.date: 03/30/2017
api_name:
- ValidatorFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ValidatorFlags
helpviewer_keywords:
- ValidatorFlags enumeration [.NET Framework hosting]
ms.assetid: a3f5c266-3fcc-4ad1-aaf5-4cdbe26304ad
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e982fa7f6354f341ff4718440f345e282a1d20d3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492219"
---
# <a name="validatorflags-enumeration"></a><span data-ttu-id="e53b5-102">ValidatorFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="e53b5-102">ValidatorFlags Enumeration</span></span>
<span data-ttu-id="e53b5-103">Obsahuje hodnoty, které označují typ ověřování, která má být provedena ve volání [iclrvalidator::Validate –](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="e53b5-103">Contains values that indicate the type of validation that should be performed in a call to the [ICLRValidator::Validate](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e53b5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e53b5-104">Syntax</span></span>  
  
```  
enum ValidatorFlags {  
    VALIDATOR_EXTRA_VERBOSE =       0x00000001,  
    VALIDATOR_SHOW_SOURCE_LINES =   0x00000002,  
    VALIDATOR_CHECK_ILONLY =        0x00000004,  
    VALIDATOR_CHECK_PEFORMAT_ONLY = 0x00000008,  
    VALIDATOR_NOCHECK_PEFORMAT =    0x00000010,  
};  
```  
  
## <a name="members"></a><span data-ttu-id="e53b5-105">Členové</span><span class="sxs-lookup"><span data-stu-id="e53b5-105">Members</span></span>  
  
|<span data-ttu-id="e53b5-106">Člen</span><span class="sxs-lookup"><span data-stu-id="e53b5-106">Member</span></span>|<span data-ttu-id="e53b5-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e53b5-107">Description</span></span>|  
|------------|-----------------|  
|`VALIDATOR_CHECK_ILONLY`|<span data-ttu-id="e53b5-108">Určuje, zda by měl být ověřen pouze Microsoft intermediate language (MSIL) ve spustitelném souboru.</span><span class="sxs-lookup"><span data-stu-id="e53b5-108">Specifies that only the Microsoft intermediate language (MSIL) in the executable file should be validated.</span></span>|  
|`VALIDATOR_CHECK_PEFORMAT_ONLY`|<span data-ttu-id="e53b5-109">Určuje, zda by měl být ověřen pouze formát spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="e53b5-109">Specifies that only the format of the executable file should be validated.</span></span>|  
|`VALIDATOR_EXTRA_VERBOSE`|<span data-ttu-id="e53b5-110">Určuje, že všechny typy ověření, které provádí a reportovány.</span><span class="sxs-lookup"><span data-stu-id="e53b5-110">Specifies that all types of validation should be performed and reported on.</span></span>|  
|`VALIDATOR_NOCHECK_PEFORMAT`|<span data-ttu-id="e53b5-111">Určuje, že by neměla ověří Formát spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="e53b5-111">Specifies that the format of the executable file should not be validated.</span></span>|  
|`VALIDATOR_SHOW_SOURCE_LINES`|<span data-ttu-id="e53b5-112">Určuje, že chybových zpráv ověření by měl obsahovat řádky zdrojového kódu, které vyvolávají chyby ověření.</span><span class="sxs-lookup"><span data-stu-id="e53b5-112">Specifies that validation error messages should include the lines of source code that raise validation errors.</span></span> <span data-ttu-id="e53b5-113">Tato hodnota pole není platný v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="e53b5-113">This field value is not valid in the .NET Framework version 2.0.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e53b5-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e53b5-114">Requirements</span></span>  
 <span data-ttu-id="e53b5-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e53b5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e53b5-116">**Záhlaví:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="e53b5-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="e53b5-117">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e53b5-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e53b5-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e53b5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e53b5-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e53b5-119">See also</span></span>
- [<span data-ttu-id="e53b5-120">ICLRErrorReportingManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e53b5-120">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="e53b5-121">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="e53b5-121">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
