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
ms.openlocfilehash: 687f33c364f9730a554a41ade1ca2b78e33ffdc5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84489675"
---
# <a name="imetadatavalidatevalidatorinit-method"></a><span data-ttu-id="f692c-102">IMetaDataValidate::ValidatorInit – metoda</span><span class="sxs-lookup"><span data-stu-id="f692c-102">IMetaDataValidate::ValidatorInit Method</span></span>
<span data-ttu-id="f692c-103">Nastaví příznak, který určuje typ modulu v aktuálním oboru metadat a registruje zadanou metodu zpětného volání pro chyby ověření.</span><span class="sxs-lookup"><span data-stu-id="f692c-103">Sets a flag that specifies the type of the module in the current metadata scope, and registers the specified callback method for validation errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f692c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f692c-104">Syntax</span></span>  
  
```cpp  
HRESULT ValidatorInit (  
   [in] DWORD       dwModuleType,  
   [in] IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f692c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f692c-105">Parameters</span></span>  
 `dwModule`  
 <span data-ttu-id="f692c-106">pro Hodnota výčtu [CorValidatorModuleType –](corvalidatormoduletype-enumeration.md) , která určuje typ modulu v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="f692c-106">[in] A value of the [CorValidatorModuleType](corvalidatormoduletype-enumeration.md) enumeration that specifies the type of the module in the current metadata scope.</span></span>  
  
 `pUnk`  
 <span data-ttu-id="f692c-107">pro Ukazatel na instanci [IUnknown](/cpp/atl/iunknown) , který slouží jako zpětné volání funkce pro chyby ověřování.</span><span class="sxs-lookup"><span data-stu-id="f692c-107">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) instance that serves as a function callback for validation errors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f692c-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f692c-108">Requirements</span></span>  
 <span data-ttu-id="f692c-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f692c-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f692c-110">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f692c-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f692c-111">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="f692c-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f692c-112">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f692c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f692c-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f692c-113">See also</span></span>

- [<span data-ttu-id="f692c-114">IMetaDataValidate – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f692c-114">IMetaDataValidate Interface</span></span>](imetadatavalidate-interface.md)
