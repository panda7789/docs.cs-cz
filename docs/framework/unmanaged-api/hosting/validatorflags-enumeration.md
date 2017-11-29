---
title: "ValidatorFlags – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ValidatorFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: ValidatorFlags
helpviewer_keywords: ValidatorFlags enumeration [.NET Framework hosting]
ms.assetid: a3f5c266-3fcc-4ad1-aaf5-4cdbe26304ad
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f283beb79ec47454185800bd772904c3c696c7c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="validatorflags-enumeration"></a><span data-ttu-id="f94cf-102">ValidatorFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="f94cf-102">ValidatorFlags Enumeration</span></span>
<span data-ttu-id="f94cf-103">Obsahuje hodnoty, které označují typ ověření, která má být provedena ve volání [iclrvalidator::Validate –](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="f94cf-103">Contains values that indicate the type of validation that should be performed in a call to the [ICLRValidator::Validate](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f94cf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f94cf-104">Syntax</span></span>  
  
```  
enum ValidatorFlags {  
    VALIDATOR_EXTRA_VERBOSE =       0x00000001,  
    VALIDATOR_SHOW_SOURCE_LINES =   0x00000002,  
    VALIDATOR_CHECK_ILONLY =        0x00000004,  
    VALIDATOR_CHECK_PEFORMAT_ONLY = 0x00000008,  
    VALIDATOR_NOCHECK_PEFORMAT =    0x00000010,  
};  
```  
  
## <a name="members"></a><span data-ttu-id="f94cf-105">Členové</span><span class="sxs-lookup"><span data-stu-id="f94cf-105">Members</span></span>  
  
|<span data-ttu-id="f94cf-106">Člen</span><span class="sxs-lookup"><span data-stu-id="f94cf-106">Member</span></span>|<span data-ttu-id="f94cf-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f94cf-107">Description</span></span>|  
|------------|-----------------|  
|`VALIDATOR_CHECK_ILONLY`|<span data-ttu-id="f94cf-108">Určuje, zda má být ověřen pouze Microsoft (MSIL intermediate language) ve spustitelném souboru.</span><span class="sxs-lookup"><span data-stu-id="f94cf-108">Specifies that only the Microsoft intermediate language (MSIL) in the executable file should be validated.</span></span>|  
|`VALIDATOR_CHECK_PEFORMAT_ONLY`|<span data-ttu-id="f94cf-109">Určuje, zda má být ověřen pouze formát spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="f94cf-109">Specifies that only the format of the executable file should be validated.</span></span>|  
|`VALIDATOR_EXTRA_VERBOSE`|<span data-ttu-id="f94cf-110">Určuje, že všechny typy ověření, které by měl být provést a ohlášeny.</span><span class="sxs-lookup"><span data-stu-id="f94cf-110">Specifies that all types of validation should be performed and reported on.</span></span>|  
|`VALIDATOR_NOCHECK_PEFORMAT`|<span data-ttu-id="f94cf-111">Určuje, že formát spustitelného souboru by neměl ověřit.</span><span class="sxs-lookup"><span data-stu-id="f94cf-111">Specifies that the format of the executable file should not be validated.</span></span>|  
|`VALIDATOR_SHOW_SOURCE_LINES`|<span data-ttu-id="f94cf-112">Určuje, že chybových zpráv ověření by měl obsahovat řádky zdrojového kódu, které vyvolat chyby ověření.</span><span class="sxs-lookup"><span data-stu-id="f94cf-112">Specifies that validation error messages should include the lines of source code that raise validation errors.</span></span> <span data-ttu-id="f94cf-113">Tato hodnota pole není platný v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="f94cf-113">This field value is not valid in the .NET Framework version 2.0.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f94cf-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f94cf-114">Requirements</span></span>  
 <span data-ttu-id="f94cf-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f94cf-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f94cf-116">**Záhlaví:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="f94cf-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="f94cf-117">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f94cf-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f94cf-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f94cf-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f94cf-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="f94cf-119">See Also</span></span>  
 [<span data-ttu-id="f94cf-120">Iclrerrorreportingmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f94cf-120">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 [<span data-ttu-id="f94cf-121">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="f94cf-121">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
