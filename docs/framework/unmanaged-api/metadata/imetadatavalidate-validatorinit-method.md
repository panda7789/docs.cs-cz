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
ms.openlocfilehash: 165a57d8029fe03b9de3754fcf7c4db757292cec
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443600"
---
# <a name="imetadatavalidatevalidatorinit-method"></a><span data-ttu-id="ef036-102">IMetaDataValidate::ValidatorInit – metoda</span><span class="sxs-lookup"><span data-stu-id="ef036-102">IMetaDataValidate::ValidatorInit Method</span></span>
<span data-ttu-id="ef036-103">Nastaví příznak, který určuje typ modulu v aktuálním oboru metadat a registruje zadanou metodu zpětného volání pro chyby ověření.</span><span class="sxs-lookup"><span data-stu-id="ef036-103">Sets a flag that specifies the type of the module in the current metadata scope, and registers the specified callback method for validation errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef036-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef036-104">Syntax</span></span>  
  
```cpp  
HRESULT ValidatorInit (  
   [in] DWORD       dwModuleType,  
   [in] IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef036-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ef036-105">Parameters</span></span>  
 `dwModule`  
 <span data-ttu-id="ef036-106">pro Hodnota výčtu [CorValidatorModuleType –](../../../../docs/framework/unmanaged-api/metadata/corvalidatormoduletype-enumeration.md) , která určuje typ modulu v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="ef036-106">[in] A value of the [CorValidatorModuleType](../../../../docs/framework/unmanaged-api/metadata/corvalidatormoduletype-enumeration.md) enumeration that specifies the type of the module in the current metadata scope.</span></span>  
  
 `pUnk`  
 <span data-ttu-id="ef036-107">pro Ukazatel na instanci [IUnknown](/cpp/atl/iunknown) , který slouží jako zpětné volání funkce pro chyby ověřování.</span><span class="sxs-lookup"><span data-stu-id="ef036-107">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) instance that serves as a function callback for validation errors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef036-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ef036-108">Requirements</span></span>  
 <span data-ttu-id="ef036-109">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef036-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef036-110">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ef036-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ef036-111">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="ef036-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ef036-112">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef036-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef036-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ef036-113">See also</span></span>

- [<span data-ttu-id="ef036-114">IMetaDataValidate – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ef036-114">IMetaDataValidate Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatavalidate-interface.md)
