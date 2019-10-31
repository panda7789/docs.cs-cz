---
title: CoInitializeEE – funkce
ms.date: 03/30/2017
api_name:
- CoInitializeEE
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoInitializeEE
helpviewer_keywords:
- CoInitializeEE function [.NET Framework hosting]
ms.assetid: 7e42a928-5068-4ba6-b8c3-806551a01fa8
topic_type:
- apiref
ms.openlocfilehash: 9e90772ae8c3e6be5744fcccc9901123df871831
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131944"
---
# <a name="coinitializeee-function"></a><span data-ttu-id="d2998-102">CoInitializeEE – funkce</span><span class="sxs-lookup"><span data-stu-id="d2998-102">CoInitializeEE Function</span></span>
<span data-ttu-id="d2998-103">Zajišťuje, aby byl spouštěcí modul společného jazykového modulu runtime načten do procesu.</span><span class="sxs-lookup"><span data-stu-id="d2998-103">Ensures that the common language runtime execution engine is loaded into a process.</span></span> <span data-ttu-id="d2998-104">Tato funkce je zastaralá v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d2998-104">This function is deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="d2998-105">Místo toho použijte metodu [ICLRRuntimeHost:: Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d2998-105">Use the [ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2998-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d2998-106">Syntax</span></span>  
  
```cpp  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2998-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="d2998-107">Parameters</span></span>  
 `fFlags`  
 <span data-ttu-id="d2998-108">pro Jedna z konstant výčtu [COINITIEE –](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="d2998-108">[in] One of the [COINITIEE](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md) enumeration constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d2998-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d2998-109">Return Value</span></span>  
 <span data-ttu-id="d2998-110">Tato metoda vrátí standardní kódy chyb modelu COM definované v WinError. h a hodnoty v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="d2998-110">This method returns standard COM error codes as defined in Winerror.h, and the values in the following table.</span></span>  
  
|<span data-ttu-id="d2998-111">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="d2998-111">Return code</span></span>|<span data-ttu-id="d2998-112">Popis</span><span class="sxs-lookup"><span data-stu-id="d2998-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="d2998-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="d2998-113">S_OK</span></span>|<span data-ttu-id="d2998-114">Spouštěcí modul byl úspěšně načten.</span><span class="sxs-lookup"><span data-stu-id="d2998-114">The execution engine was loaded successfully.</span></span>|  
|<span data-ttu-id="d2998-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="d2998-115">S_FALSE</span></span>|<span data-ttu-id="d2998-116">Spouštěcí modul je již načten.</span><span class="sxs-lookup"><span data-stu-id="d2998-116">The execution engine is already loaded.</span></span>|  
|<span data-ttu-id="d2998-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d2998-117">E_FAIL</span></span>|<span data-ttu-id="d2998-118">Spouštěcí modul nelze načíst.</span><span class="sxs-lookup"><span data-stu-id="d2998-118">The execution engine could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2998-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d2998-119">Remarks</span></span>  
 <span data-ttu-id="d2998-120">Tato metoda načte prováděcí modul, pokud nebyl dříve načten.</span><span class="sxs-lookup"><span data-stu-id="d2998-120">This method loads the execution engine if it has not been previously loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2998-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d2998-121">Requirements</span></span>  
 <span data-ttu-id="d2998-122">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2998-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2998-123">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d2998-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d2998-124">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d2998-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d2998-125">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2998-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2998-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d2998-126">See also</span></span>

- [<span data-ttu-id="d2998-127">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="d2998-127">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
