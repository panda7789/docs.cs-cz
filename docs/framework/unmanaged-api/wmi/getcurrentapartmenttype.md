---
title: Funkce GetCurrentApartmentType (referenční dokumentace nespravovaného rozhraní API)
description: Funkce GetCurrentApartmentType načte typu apartment, ve kterém je prováděna volající.
ms.date: 11/06/2017
api_name:
- GetCurrentApartmentType
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetCurrentApartmentType
helpviewer_keywords:
- GetCurrentApartmentType function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca7b5fa5bf6d845d542d3e80c0571e59f3d4c1e0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461721"
---
# <a name="getcurrentapartmenttype-function"></a><span data-ttu-id="db0d6-103">GetCurrentApartmentType – funkce</span><span class="sxs-lookup"><span data-stu-id="db0d6-103">GetCurrentApartmentType function</span></span>
<span data-ttu-id="db0d6-104">Načte typu apartment, ve kterém je prováděna volající.</span><span class="sxs-lookup"><span data-stu-id="db0d6-104">Retrieves the type of apartment in which the caller is executing.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="db0d6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db0d6-105">Syntax</span></span>  
  
```  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc, 
   [in] IComThreadingInfo*    ptr, 
   [out] APTTYPE*             aptType
); 
```  

## <a name="parameters"></a><span data-ttu-id="db0d6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="db0d6-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="db0d6-107">[v] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="db0d6-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="db0d6-108">[v] Ukazatel na [IComThreadingInfo](https://msdn.microsoft.com/library/windows/desktop/ms694502(v=vs.85).aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="db0d6-108">[in] A pointer to an [IComThreadingInfo](https://msdn.microsoft.com/library/windows/desktop/ms694502(v=vs.85).aspx) instance.</span></span>

`aptType`  
<span data-ttu-id="db0d6-109">[out] Ukazatel na [APTTYPE](https://msdn.microsoft.com/library/windows/desktop/ms693793(v=vs.85).aspx) hodnotu výčtu, která určuje apartment volajícího.</span><span class="sxs-lookup"><span data-stu-id="db0d6-109">[out] A pointer to an [APTTYPE](https://msdn.microsoft.com/library/windows/desktop/ms693793(v=vs.85).aspx) enumeration value that indicates the caller's apartment.</span></span>

## <a name="return-value"></a><span data-ttu-id="db0d6-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="db0d6-110">Return value</span></span>


|<span data-ttu-id="db0d6-111">Konstanta</span><span class="sxs-lookup"><span data-stu-id="db0d6-111">Constant</span></span>  |<span data-ttu-id="db0d6-112">Hodnota</span><span class="sxs-lookup"><span data-stu-id="db0d6-112">Value</span></span>  |<span data-ttu-id="db0d6-113">Popis</span><span class="sxs-lookup"><span data-stu-id="db0d6-113">Description</span></span>  |
|---------|---------|---------|
| `S_OK` | <span data-ttu-id="db0d6-114">0</span><span class="sxs-lookup"><span data-stu-id="db0d6-114">0</span></span> | <span data-ttu-id="db0d6-115">Funkce byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="db0d6-115">The function completed successfully.</span></span> |
| `E_FAIL` | <span data-ttu-id="db0d6-116">0x80000008</span><span class="sxs-lookup"><span data-stu-id="db0d6-116">0x80000008</span></span> | <span data-ttu-id="db0d6-117">Volající není spuštěno v typu apartment.</span><span class="sxs-lookup"><span data-stu-id="db0d6-117">The caller is not executing in an apartment.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="db0d6-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="db0d6-118">Remarks</span></span>

<span data-ttu-id="db0d6-119">Tato funkce zabalí volání [IComThreadingInfo::GetCurrentApartmentType](https://msdn.microsoft.com/library/windows/desktop/ms683752(v=vs.85).aspx) metoda.</span><span class="sxs-lookup"><span data-stu-id="db0d6-119">This function wraps a call to the [IComThreadingInfo::GetCurrentApartmentType](https://msdn.microsoft.com/library/windows/desktop/ms683752(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="db0d6-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="db0d6-120">Requirements</span></span>  
 <span data-ttu-id="db0d6-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db0d6-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db0d6-122">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="db0d6-122">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="db0d6-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="db0d6-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db0d6-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="db0d6-124">See also</span></span>  
[<span data-ttu-id="db0d6-125">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="db0d6-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
