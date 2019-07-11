---
title: Funkce GetCurrentApartmentType (referenční dokumentace nespravovaného rozhraní API)
description: Funkce GetCurrentApartmentType načte typ objektu apartment, ve kterém je spuštěn volající.
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
ms.openlocfilehash: 76c852ac81126895ea3a2e1b40473722c8445201
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746554"
---
# <a name="getcurrentapartmenttype-function"></a><span data-ttu-id="7081b-103">GetCurrentApartmentType function</span><span class="sxs-lookup"><span data-stu-id="7081b-103">GetCurrentApartmentType function</span></span>
<span data-ttu-id="7081b-104">Získá typ objektu apartment, ve kterém je spuštěn volající.</span><span class="sxs-lookup"><span data-stu-id="7081b-104">Retrieves the type of apartment in which the caller is executing.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="7081b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7081b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc, 
   [in] IComThreadingInfo*    ptr, 
   [out] APTTYPE*             aptType
); 
```  

## <a name="parameters"></a><span data-ttu-id="7081b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7081b-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="7081b-107">[in] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="7081b-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="7081b-108">[in] Ukazatel [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) instance.</span><span class="sxs-lookup"><span data-stu-id="7081b-108">[in] A pointer to an [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) instance.</span></span>

`aptType`  
<span data-ttu-id="7081b-109">[out] Ukazatel [APTTYPE](/windows/desktop/api/objidlbase/ne-objidlbase-_apttype) hodnotu výčtu, která určuje volajícího objektu apartment.</span><span class="sxs-lookup"><span data-stu-id="7081b-109">[out] A pointer to an [APTTYPE](/windows/desktop/api/objidlbase/ne-objidlbase-_apttype) enumeration value that indicates the caller's apartment.</span></span>

## <a name="return-value"></a><span data-ttu-id="7081b-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7081b-110">Return value</span></span>

|<span data-ttu-id="7081b-111">Konstanta</span><span class="sxs-lookup"><span data-stu-id="7081b-111">Constant</span></span>  |<span data-ttu-id="7081b-112">Value</span><span class="sxs-lookup"><span data-stu-id="7081b-112">Value</span></span>  |<span data-ttu-id="7081b-113">Popis</span><span class="sxs-lookup"><span data-stu-id="7081b-113">Description</span></span>  |
|---------|---------|---------|
| `S_OK` | <span data-ttu-id="7081b-114">0</span><span class="sxs-lookup"><span data-stu-id="7081b-114">0</span></span> | <span data-ttu-id="7081b-115">Funkce, která byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="7081b-115">The function completed successfully.</span></span> |
| `E_FAIL` | <span data-ttu-id="7081b-116">0x80000008</span><span class="sxs-lookup"><span data-stu-id="7081b-116">0x80000008</span></span> | <span data-ttu-id="7081b-117">Volající není prováděna v komplexu.</span><span class="sxs-lookup"><span data-stu-id="7081b-117">The caller is not executing in an apartment.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="7081b-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7081b-118">Remarks</span></span>

<span data-ttu-id="7081b-119">Tato funkce zalamuje volání na [IComThreadingInfo::GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) metody.</span><span class="sxs-lookup"><span data-stu-id="7081b-119">This function wraps a call to the [IComThreadingInfo::GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7081b-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7081b-120">Requirements</span></span>  
 <span data-ttu-id="7081b-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7081b-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7081b-122">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="7081b-122">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="7081b-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7081b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7081b-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7081b-124">See also</span></span>

- [<span data-ttu-id="7081b-125">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="7081b-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
