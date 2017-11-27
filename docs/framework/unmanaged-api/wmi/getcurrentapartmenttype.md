---
title: "Funkce GetCurrentApartmentType (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce GetCurrentApartmentType načte typu apartment, ve kterém je prováděna volající."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetCurrentApartmentType
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetCurrentApartmentType
helpviewer_keywords: GetCurrentApartmentType function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b250913b55ba59261a666760cc15466b6f9d096e
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2017
---
# <a name="getcurrentapartmenttype-function"></a><span data-ttu-id="a583d-103">GetCurrentApartmentType – funkce</span><span class="sxs-lookup"><span data-stu-id="a583d-103">GetCurrentApartmentType function</span></span>
<span data-ttu-id="a583d-104">Načte typu apartment, ve kterém je prováděna volající.</span><span class="sxs-lookup"><span data-stu-id="a583d-104">Retrieves the type of apartment in which the caller is executing.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="a583d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a583d-105">Syntax</span></span>  
  
```  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc, 
   [in] IComThreadingInfo*    ptr, 
   [out] APTTYPE*             aptType
); 
```  

## <a name="parameters"></a><span data-ttu-id="a583d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a583d-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="a583d-107">[v] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="a583d-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="a583d-108">[v] Ukazatel na [IComThreadingInfo](https://msdn.microsoft.com/library/windows/desktop/ms694502(v=vs.85).aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="a583d-108">[in] A pointer to an [IComThreadingInfo](https://msdn.microsoft.com/library/windows/desktop/ms694502(v=vs.85).aspx) instance.</span></span>

`aptType`  
<span data-ttu-id="a583d-109">[out] Ukazatel na [APTTYPE](https://msdn.microsoft.com/library/windows/desktop/ms693793(v=vs.85).aspx) hodnotu výčtu, která určuje apartment volajícího.</span><span class="sxs-lookup"><span data-stu-id="a583d-109">[out] A pointer to an [APTTYPE](https://msdn.microsoft.com/library/windows/desktop/ms693793(v=vs.85).aspx) enumeration value that indicates the caller's apartment.</span></span>

## <a name="return-value"></a><span data-ttu-id="a583d-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a583d-110">Return value</span></span>


|<span data-ttu-id="a583d-111">Konstanta</span><span class="sxs-lookup"><span data-stu-id="a583d-111">Constant</span></span>  |<span data-ttu-id="a583d-112">Hodnota</span><span class="sxs-lookup"><span data-stu-id="a583d-112">Value</span></span>  |<span data-ttu-id="a583d-113">Popis</span><span class="sxs-lookup"><span data-stu-id="a583d-113">Description</span></span>  |
|---------|---------|---------|
| `S_OK` | <span data-ttu-id="a583d-114">0</span><span class="sxs-lookup"><span data-stu-id="a583d-114">0</span></span> | <span data-ttu-id="a583d-115">Funkce byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="a583d-115">The function completed successfully.</span></span> |
| `E_FAIL` | <span data-ttu-id="a583d-116">0x80000008</span><span class="sxs-lookup"><span data-stu-id="a583d-116">0x80000008</span></span> | <span data-ttu-id="a583d-117">Volající není spuštěno v typu apartment.</span><span class="sxs-lookup"><span data-stu-id="a583d-117">The caller is not executing in an apartment.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="a583d-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a583d-118">Remarks</span></span>

<span data-ttu-id="a583d-119">Tato funkce zabalí volání [IComThreadingInfo::GetCurrentApartmentType](https://msdn.microsoft.com/library/windows/desktop/ms683752(v=vs.85).aspx) metoda.</span><span class="sxs-lookup"><span data-stu-id="a583d-119">This function wraps a call to the [IComThreadingInfo::GetCurrentApartmentType](https://msdn.microsoft.com/library/windows/desktop/ms683752(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a583d-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a583d-120">Requirements</span></span>  
 <span data-ttu-id="a583d-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a583d-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a583d-122">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="a583d-122">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="a583d-123">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a583d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a583d-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="a583d-124">See also</span></span>  
[<span data-ttu-id="a583d-125">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="a583d-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
