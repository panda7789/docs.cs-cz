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
ms.openlocfilehash: 61aafb8dc99bb908fc603945ff6ea74054f812c4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141416"
---
# <a name="validatorflags-enumeration"></a><span data-ttu-id="51274-102">ValidatorFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="51274-102">ValidatorFlags Enumeration</span></span>
<span data-ttu-id="51274-103">Obsahuje hodnoty, které určují typ ověřování, který by měl být proveden při volání metody [ICLRValidator:: Validate](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md) .</span><span class="sxs-lookup"><span data-stu-id="51274-103">Contains values that indicate the type of validation that should be performed in a call to the [ICLRValidator::Validate](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51274-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51274-104">Syntax</span></span>  
  
```cpp  
enum ValidatorFlags {  
    VALIDATOR_EXTRA_VERBOSE =       0x00000001,  
    VALIDATOR_SHOW_SOURCE_LINES =   0x00000002,  
    VALIDATOR_CHECK_ILONLY =        0x00000004,  
    VALIDATOR_CHECK_PEFORMAT_ONLY = 0x00000008,  
    VALIDATOR_NOCHECK_PEFORMAT =    0x00000010,  
};  
```  
  
## <a name="members"></a><span data-ttu-id="51274-105">Členové</span><span class="sxs-lookup"><span data-stu-id="51274-105">Members</span></span>  
  
|<span data-ttu-id="51274-106">Člen</span><span class="sxs-lookup"><span data-stu-id="51274-106">Member</span></span>|<span data-ttu-id="51274-107">Popis</span><span class="sxs-lookup"><span data-stu-id="51274-107">Description</span></span>|  
|------------|-----------------|  
|`VALIDATOR_CHECK_ILONLY`|<span data-ttu-id="51274-108">Určuje, že by měl být ověřený pouze kód jazyka MSIL (Microsoft Intermediate Language) ve spustitelném souboru.</span><span class="sxs-lookup"><span data-stu-id="51274-108">Specifies that only the Microsoft intermediate language (MSIL) in the executable file should be validated.</span></span>|  
|`VALIDATOR_CHECK_PEFORMAT_ONLY`|<span data-ttu-id="51274-109">Určuje, že by měl být ověřený jenom formát spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="51274-109">Specifies that only the format of the executable file should be validated.</span></span>|  
|`VALIDATOR_EXTRA_VERBOSE`|<span data-ttu-id="51274-110">Určuje, že by měly být provedeny a hlášeny všechny typy ověřování.</span><span class="sxs-lookup"><span data-stu-id="51274-110">Specifies that all types of validation should be performed and reported on.</span></span>|  
|`VALIDATOR_NOCHECK_PEFORMAT`|<span data-ttu-id="51274-111">Určuje, že by se neměl ověřit formát spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="51274-111">Specifies that the format of the executable file should not be validated.</span></span>|  
|`VALIDATOR_SHOW_SOURCE_LINES`|<span data-ttu-id="51274-112">Určuje, že zprávy o chybách ověřování by měly zahrnovat řádky zdrojového kódu, které vyvolávají chyby ověřování.</span><span class="sxs-lookup"><span data-stu-id="51274-112">Specifies that validation error messages should include the lines of source code that raise validation errors.</span></span> <span data-ttu-id="51274-113">Hodnota tohoto pole není platná v .NET Framework verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="51274-113">This field value is not valid in the .NET Framework version 2.0.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="51274-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="51274-114">Requirements</span></span>  
 <span data-ttu-id="51274-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51274-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51274-116">**Hlavička:** IValidator. idl, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="51274-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="51274-117">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="51274-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="51274-118">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51274-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51274-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="51274-119">See also</span></span>

- [<span data-ttu-id="51274-120">ICLRErrorReportingManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="51274-120">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="51274-121">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="51274-121">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
