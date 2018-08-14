---
title: IMetaDataValidate::ValidatorInit – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataValidate.ValidatorInit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataValidate::ValidatorInit
helpviewer_keywords:
- IMetaDataValidate::ValidatorInit method [.NET Framework metadata]
- ValidatorInit method [.NET Framework metadata]
ms.assetid: 6bafd75a-e2d0-4aea-aed1-074374d5dff6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 053c94bc540b130510f155506b6fad32f032a475
ms.sourcegitcommit: a474397fd4de822f0d878d86d907e49763872b0b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "33449543"
---
# <a name="imetadatavalidatevalidatorinit-method"></a><span data-ttu-id="c557f-102">IMetaDataValidate::ValidatorInit – metoda</span><span class="sxs-lookup"><span data-stu-id="c557f-102">IMetaDataValidate::ValidatorInit Method</span></span>
<span data-ttu-id="c557f-103">Nastaví příznak, který určuje typ modulu v aktuálním oboru metadata a zaregistruje zadaná metoda zpětného volání pro chyby ověření.</span><span class="sxs-lookup"><span data-stu-id="c557f-103">Sets a flag that specifies the type of the module in the current metadata scope, and registers the specified callback method for validation errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c557f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c557f-104">Syntax</span></span>  
  
```  
HRESULT ValidatorInit (  
   [in] DWORD       dwModuleType,  
   [in] IUnknown    *pUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c557f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c557f-105">Parameters</span></span>  
 `dwModule`  
 <span data-ttu-id="c557f-106">[in] Hodnota [corvalidatormoduletype –](../../../../docs/framework/unmanaged-api/metadata/corvalidatormoduletype-enumeration.md) výčet, který určuje typ modulu v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="c557f-106">[in] A value of the [CorValidatorModuleType](../../../../docs/framework/unmanaged-api/metadata/corvalidatormoduletype-enumeration.md) enumeration that specifies the type of the module in the current metadata scope.</span></span>  
  
 `pUnk`  
 <span data-ttu-id="c557f-107">[in] Ukazatel [IUnknown](/cpp/atl/iunknown) instanci, která slouží jako funkce zpětného volání pro chyby ověření.</span><span class="sxs-lookup"><span data-stu-id="c557f-107">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) instance that serves as a function callback for validation errors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c557f-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c557f-108">Requirements</span></span>  
 <span data-ttu-id="c557f-109">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c557f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c557f-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c557f-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c557f-111">**Knihovna:** použit jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c557f-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c557f-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c557f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c557f-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="c557f-113">See Also</span></span>  
 [<span data-ttu-id="c557f-114">IMetaDataValidate – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c557f-114">IMetaDataValidate Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatavalidate-interface.md)
