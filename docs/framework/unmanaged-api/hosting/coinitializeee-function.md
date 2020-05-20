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
ms.openlocfilehash: 57508a2df3a49c39d25347f2a3038442c37278da
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616759"
---
# <a name="coinitializeee-function"></a><span data-ttu-id="9d008-102">CoInitializeEE – funkce</span><span class="sxs-lookup"><span data-stu-id="9d008-102">CoInitializeEE Function</span></span>
<span data-ttu-id="9d008-103">Zajišťuje, aby byl spouštěcí modul společného jazykového modulu runtime načten do procesu.</span><span class="sxs-lookup"><span data-stu-id="9d008-103">Ensures that the common language runtime execution engine is loaded into a process.</span></span> <span data-ttu-id="9d008-104">Tato funkce je zastaralá v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9d008-104">This function is deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="9d008-105">Místo toho použijte metodu [ICLRRuntimeHost:: Start](iclrruntimehost-start-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9d008-105">Use the [ICLRRuntimeHost::Start](iclrruntimehost-start-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d008-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d008-106">Syntax</span></span>  
  
```cpp  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d008-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d008-107">Parameters</span></span>  
 `fFlags`  
 <span data-ttu-id="9d008-108">pro Jedna z konstant výčtu [COINITIEE –](../metadata/coinitiee-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="9d008-108">[in] One of the [COINITIEE](../metadata/coinitiee-enumeration.md) enumeration constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d008-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9d008-109">Return Value</span></span>  
 <span data-ttu-id="9d008-110">Tato metoda vrátí standardní kódy chyb modelu COM definované v WinError. h a hodnoty v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="9d008-110">This method returns standard COM error codes as defined in Winerror.h, and the values in the following table.</span></span>  
  
|<span data-ttu-id="9d008-111">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="9d008-111">Return code</span></span>|<span data-ttu-id="9d008-112">Popis</span><span class="sxs-lookup"><span data-stu-id="9d008-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="9d008-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="9d008-113">S_OK</span></span>|<span data-ttu-id="9d008-114">Spouštěcí modul byl úspěšně načten.</span><span class="sxs-lookup"><span data-stu-id="9d008-114">The execution engine was loaded successfully.</span></span>|  
|<span data-ttu-id="9d008-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="9d008-115">S_FALSE</span></span>|<span data-ttu-id="9d008-116">Spouštěcí modul je již načten.</span><span class="sxs-lookup"><span data-stu-id="9d008-116">The execution engine is already loaded.</span></span>|  
|<span data-ttu-id="9d008-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9d008-117">E_FAIL</span></span>|<span data-ttu-id="9d008-118">Spouštěcí modul nelze načíst.</span><span class="sxs-lookup"><span data-stu-id="9d008-118">The execution engine could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d008-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9d008-119">Remarks</span></span>  
 <span data-ttu-id="9d008-120">Tato metoda načte prováděcí modul, pokud nebyl dříve načten.</span><span class="sxs-lookup"><span data-stu-id="9d008-120">This method loads the execution engine if it has not been previously loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d008-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9d008-121">Requirements</span></span>  
 <span data-ttu-id="9d008-122">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d008-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d008-123">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9d008-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9d008-124">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9d008-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9d008-125">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d008-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d008-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="9d008-126">See also</span></span>

- [<span data-ttu-id="9d008-127">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="9d008-127">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
