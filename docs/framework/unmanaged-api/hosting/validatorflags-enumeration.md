---
title: "ValidatorFlags – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 952944e9ae9a8186a182796deb587b6fa6a0d6a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="validatorflags-enumeration"></a><span data-ttu-id="be13a-102">ValidatorFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="be13a-102">ValidatorFlags Enumeration</span></span>
<span data-ttu-id="be13a-103">Obsahuje hodnoty, které označují typ ověření, která má být provedena ve volání [iclrvalidator::Validate –](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="be13a-103">Contains values that indicate the type of validation that should be performed in a call to the [ICLRValidator::Validate](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be13a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be13a-104">Syntax</span></span>  
  
```  
enum ValidatorFlags {  
    VALIDATOR_EXTRA_VERBOSE =       0x00000001,  
    VALIDATOR_SHOW_SOURCE_LINES =   0x00000002,  
    VALIDATOR_CHECK_ILONLY =        0x00000004,  
    VALIDATOR_CHECK_PEFORMAT_ONLY = 0x00000008,  
    VALIDATOR_NOCHECK_PEFORMAT =    0x00000010,  
};  
```  
  
## <a name="members"></a><span data-ttu-id="be13a-105">Členové</span><span class="sxs-lookup"><span data-stu-id="be13a-105">Members</span></span>  
  
|<span data-ttu-id="be13a-106">Člen</span><span class="sxs-lookup"><span data-stu-id="be13a-106">Member</span></span>|<span data-ttu-id="be13a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="be13a-107">Description</span></span>|  
|------------|-----------------|  
|`VALIDATOR_CHECK_ILONLY`|<span data-ttu-id="be13a-108">Určuje, zda má být ověřen pouze Microsoft (MSIL intermediate language) ve spustitelném souboru.</span><span class="sxs-lookup"><span data-stu-id="be13a-108">Specifies that only the Microsoft intermediate language (MSIL) in the executable file should be validated.</span></span>|  
|`VALIDATOR_CHECK_PEFORMAT_ONLY`|<span data-ttu-id="be13a-109">Určuje, zda má být ověřen pouze formát spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="be13a-109">Specifies that only the format of the executable file should be validated.</span></span>|  
|`VALIDATOR_EXTRA_VERBOSE`|<span data-ttu-id="be13a-110">Určuje, že všechny typy ověření, které by měl být provést a ohlášeny.</span><span class="sxs-lookup"><span data-stu-id="be13a-110">Specifies that all types of validation should be performed and reported on.</span></span>|  
|`VALIDATOR_NOCHECK_PEFORMAT`|<span data-ttu-id="be13a-111">Určuje, že formát spustitelného souboru by neměl ověřit.</span><span class="sxs-lookup"><span data-stu-id="be13a-111">Specifies that the format of the executable file should not be validated.</span></span>|  
|`VALIDATOR_SHOW_SOURCE_LINES`|<span data-ttu-id="be13a-112">Určuje, že chybových zpráv ověření by měl obsahovat řádky zdrojového kódu, které vyvolat chyby ověření.</span><span class="sxs-lookup"><span data-stu-id="be13a-112">Specifies that validation error messages should include the lines of source code that raise validation errors.</span></span> <span data-ttu-id="be13a-113">Tato hodnota pole není platný v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="be13a-113">This field value is not valid in the .NET Framework version 2.0.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="be13a-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="be13a-114">Requirements</span></span>  
 <span data-ttu-id="be13a-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be13a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be13a-116">**Záhlaví:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="be13a-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="be13a-117">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="be13a-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="be13a-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be13a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be13a-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="be13a-119">See Also</span></span>  
 [<span data-ttu-id="be13a-120">ICLRErrorReportingManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="be13a-120">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 [<span data-ttu-id="be13a-121">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="be13a-121">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
