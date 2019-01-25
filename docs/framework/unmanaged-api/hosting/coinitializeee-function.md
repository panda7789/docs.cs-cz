---
title: CoInitializeEE – funkce
ms.date: 03/30/2017
api_name:
- CoInitializeEE
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CoInitializeEE
helpviewer_keywords:
- CoInitializeEE function [.NET Framework hosting]
ms.assetid: 7e42a928-5068-4ba6-b8c3-806551a01fa8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36a603bf1badebd2454601780179a8435f33bc70
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54525180"
---
# <a name="coinitializeee-function"></a><span data-ttu-id="6eda5-102">CoInitializeEE – funkce</span><span class="sxs-lookup"><span data-stu-id="6eda5-102">CoInitializeEE Function</span></span>
<span data-ttu-id="6eda5-103">Zajišťuje, že common language runtime prováděcí modul je načten do procesu.</span><span class="sxs-lookup"><span data-stu-id="6eda5-103">Ensures that the common language runtime execution engine is loaded into a process.</span></span> <span data-ttu-id="6eda5-104">Tato funkce je zastaralá ve [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6eda5-104">This function is deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="6eda5-105">Použití [ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="6eda5-105">Use the [ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6eda5-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6eda5-106">Syntax</span></span>  
  
```  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6eda5-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="6eda5-107">Parameters</span></span>  
 `fFlags`  
 <span data-ttu-id="6eda5-108">[in] Jeden z [coinitiee –](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md) výčtu konstant.</span><span class="sxs-lookup"><span data-stu-id="6eda5-108">[in] One of the [COINITIEE](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md) enumeration constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6eda5-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6eda5-109">Return Value</span></span>  
 <span data-ttu-id="6eda5-110">Tato metoda vrátí standardní kódy chyb modelu COM, jak je definováno ve Winerror.h a hodnoty v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="6eda5-110">This method returns standard COM error codes as defined in Winerror.h, and the values in the following table.</span></span>  
  
|<span data-ttu-id="6eda5-111">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="6eda5-111">Return code</span></span>|<span data-ttu-id="6eda5-112">Popis</span><span class="sxs-lookup"><span data-stu-id="6eda5-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="6eda5-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="6eda5-113">S_OK</span></span>|<span data-ttu-id="6eda5-114">Prováděcí modul byl úspěšně načten.</span><span class="sxs-lookup"><span data-stu-id="6eda5-114">The execution engine was loaded successfully.</span></span>|  
|<span data-ttu-id="6eda5-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="6eda5-115">S_FALSE</span></span>|<span data-ttu-id="6eda5-116">Prováděcí modul je již načtena.</span><span class="sxs-lookup"><span data-stu-id="6eda5-116">The execution engine is already loaded.</span></span>|  
|<span data-ttu-id="6eda5-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6eda5-117">E_FAIL</span></span>|<span data-ttu-id="6eda5-118">Prováděcí modul nelze načíst.</span><span class="sxs-lookup"><span data-stu-id="6eda5-118">The execution engine could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6eda5-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6eda5-119">Remarks</span></span>  
 <span data-ttu-id="6eda5-120">Tato metoda načte prováděcího modulu, pokud nebyla dříve načtena.</span><span class="sxs-lookup"><span data-stu-id="6eda5-120">This method loads the execution engine if it has not been previously loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6eda5-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6eda5-121">Requirements</span></span>  
 <span data-ttu-id="6eda5-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6eda5-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6eda5-123">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6eda5-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6eda5-124">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6eda5-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6eda5-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6eda5-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6eda5-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6eda5-126">See also</span></span>
- [<span data-ttu-id="6eda5-127">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="6eda5-127">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
