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
ms.openlocfilehash: 8bbd25909e70826f8cd29076c1eb62a4da6779cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435398"
---
# <a name="coinitializeee-function"></a><span data-ttu-id="bca0a-102">CoInitializeEE – funkce</span><span class="sxs-lookup"><span data-stu-id="bca0a-102">CoInitializeEE Function</span></span>
<span data-ttu-id="bca0a-103">Zajišťuje, že je běžné spouštěcí modul runtime jazyka načtena do procesu.</span><span class="sxs-lookup"><span data-stu-id="bca0a-103">Ensures that the common language runtime execution engine is loaded into a process.</span></span> <span data-ttu-id="bca0a-104">Tato funkce je ve zastaralá [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bca0a-104">This function is deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="bca0a-105">Použití [iclrruntimehost::Start –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="bca0a-105">Use the [ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bca0a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bca0a-106">Syntax</span></span>  
  
```  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bca0a-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="bca0a-107">Parameters</span></span>  
 `fFlags`  
 <span data-ttu-id="bca0a-108">[v] Jeden z [COINITIEE](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md) konstanty výčtu.</span><span class="sxs-lookup"><span data-stu-id="bca0a-108">[in] One of the [COINITIEE](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md) enumeration constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bca0a-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bca0a-109">Return Value</span></span>  
 <span data-ttu-id="bca0a-110">Tato metoda vrátí standardní kódy chyb COM, jak jsou definovány v Winerror.h a hodnoty v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="bca0a-110">This method returns standard COM error codes as defined in Winerror.h, and the values in the following table.</span></span>  
  
|<span data-ttu-id="bca0a-111">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="bca0a-111">Return code</span></span>|<span data-ttu-id="bca0a-112">Popis</span><span class="sxs-lookup"><span data-stu-id="bca0a-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="bca0a-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="bca0a-113">S_OK</span></span>|<span data-ttu-id="bca0a-114">Spouštěcí modul byl úspěšně načten.</span><span class="sxs-lookup"><span data-stu-id="bca0a-114">The execution engine was loaded successfully.</span></span>|  
|<span data-ttu-id="bca0a-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="bca0a-115">S_FALSE</span></span>|<span data-ttu-id="bca0a-116">Spouštěcí modul je již načten.</span><span class="sxs-lookup"><span data-stu-id="bca0a-116">The execution engine is already loaded.</span></span>|  
|<span data-ttu-id="bca0a-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bca0a-117">E_FAIL</span></span>|<span data-ttu-id="bca0a-118">Spouštěcí modul nelze načíst.</span><span class="sxs-lookup"><span data-stu-id="bca0a-118">The execution engine could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bca0a-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bca0a-119">Remarks</span></span>  
 <span data-ttu-id="bca0a-120">Tato metoda načte modul provádění, pokud nebyla dříve načtena.</span><span class="sxs-lookup"><span data-stu-id="bca0a-120">This method loads the execution engine if it has not been previously loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bca0a-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bca0a-121">Requirements</span></span>  
 <span data-ttu-id="bca0a-122">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bca0a-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bca0a-123">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bca0a-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bca0a-124">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bca0a-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bca0a-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bca0a-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bca0a-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="bca0a-126">See Also</span></span>  
 [<span data-ttu-id="bca0a-127">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="bca0a-127">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
