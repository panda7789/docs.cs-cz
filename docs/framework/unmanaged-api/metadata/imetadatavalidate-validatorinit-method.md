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
ms.openlocfilehash: 31ff2c62810061cd8b774e934167a5ee3acf040c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59195888"
---
# <a name="imetadatavalidatevalidatorinit-method"></a><span data-ttu-id="44094-102">IMetaDataValidate::ValidatorInit – metoda</span><span class="sxs-lookup"><span data-stu-id="44094-102">IMetaDataValidate::ValidatorInit Method</span></span>
<span data-ttu-id="44094-103">Nastaví příznak, který určuje typ modulu v aktuálním oboru metadata a zaregistruje zadaná metoda zpětného volání pro chyby ověření.</span><span class="sxs-lookup"><span data-stu-id="44094-103">Sets a flag that specifies the type of the module in the current metadata scope, and registers the specified callback method for validation errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44094-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44094-104">Syntax</span></span>  
  
```  
HRESULT ValidatorInit (  
   [in] DWORD       dwModuleType,  
   [in] IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44094-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="44094-105">Parameters</span></span>  
 `dwModule`  
 <span data-ttu-id="44094-106">[in] Hodnota [corvalidatormoduletype –](../../../../docs/framework/unmanaged-api/metadata/corvalidatormoduletype-enumeration.md) výčet, který určuje typ modulu v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="44094-106">[in] A value of the [CorValidatorModuleType](../../../../docs/framework/unmanaged-api/metadata/corvalidatormoduletype-enumeration.md) enumeration that specifies the type of the module in the current metadata scope.</span></span>  
  
 `pUnk`  
 <span data-ttu-id="44094-107">[in] Ukazatel [IUnknown](/cpp/atl/iunknown) instanci, která slouží jako funkce zpětného volání pro chyby ověření.</span><span class="sxs-lookup"><span data-stu-id="44094-107">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) instance that serves as a function callback for validation errors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44094-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="44094-108">Requirements</span></span>  
 <span data-ttu-id="44094-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44094-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44094-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="44094-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="44094-111">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="44094-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="44094-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44094-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44094-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="44094-113">See also</span></span>

- [<span data-ttu-id="44094-114">IMetaDataValidate – rozhraní</span><span class="sxs-lookup"><span data-stu-id="44094-114">IMetaDataValidate Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatavalidate-interface.md)
