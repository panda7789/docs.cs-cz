---
title: "IMetaDataValidate::ValidatorInit – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataValidate.ValidatorInit
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataValidate::ValidatorInit
helpviewer_keywords:
- IMetaDataValidate::ValidatorInit method [.NET Framework metadata]
- ValidatorInit method [.NET Framework metadata]
ms.assetid: 6bafd75a-e2d0-4aea-aed1-074374d5dff6
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e2a9b265b4fcc75406f5d5f1dbddb8bd74b5832d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="imetadatavalidatevalidatorinit-method"></a><span data-ttu-id="af03f-102">IMetaDataValidate::ValidatorInit – metoda</span><span class="sxs-lookup"><span data-stu-id="af03f-102">IMetaDataValidate::ValidatorInit Method</span></span>
<span data-ttu-id="af03f-103">Nastaví příznak, který určuje typ modulu v aktuálním oboru metadat a zaregistruje metodě zadaného zpětného volání pro chyby ověření.</span><span class="sxs-lookup"><span data-stu-id="af03f-103">Sets a flag that specifies the type of the module in the current metadata scope, and registers the specified callback method for validation errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af03f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af03f-104">Syntax</span></span>  
  
```  
HRESULT ValidatorInit (  
   [in] DWORD       dwModuleType,  
   [in] IUnknown    *pUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="af03f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="af03f-105">Parameters</span></span>  
 `dwModule`  
 <span data-ttu-id="af03f-106">[v] Hodnota [CorValidatorModuleType](../../../../docs/framework/unmanaged-api/metadata/corvalidatormoduletype-enumeration.md) výčet, který určuje typ modulu v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="af03f-106">[in] A value of the [CorValidatorModuleType](../../../../docs/framework/unmanaged-api/metadata/corvalidatormoduletype-enumeration.md) enumeration that specifies the type of the module in the current metadata scope.</span></span>  
  
 `pUnk`  
 <span data-ttu-id="af03f-107">[v] Ukazatel na <<!--zzxref:IUnknown --> `IUnknown`> instance, která slouží jako funkce zpětného volání pro chyby ověření.</span><span class="sxs-lookup"><span data-stu-id="af03f-107">[in] A pointer to an <<!--zzxref:IUnknown --> `IUnknown`> instance that serves as a function callback for validation errors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af03f-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="af03f-108">Requirements</span></span>  
 <span data-ttu-id="af03f-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af03f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af03f-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="af03f-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="af03f-111">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="af03f-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="af03f-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af03f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af03f-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="af03f-113">See Also</span></span>  
 [<span data-ttu-id="af03f-114">Imetadatavalidate – rozhraní</span><span class="sxs-lookup"><span data-stu-id="af03f-114">IMetaDataValidate Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatavalidate-interface.md)
