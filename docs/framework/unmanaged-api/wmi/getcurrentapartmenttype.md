---
title: Funkce GetCurrentApartmentType (Nespravovaný odkaz na rozhraní API)
description: Funkce GetCurrentApartmentType načte typ apartment, ve kterém volající provádí.
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
ms.openlocfilehash: 3fc88f7997ee5a6c25359243e1ee97a041050eb7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176822"
---
# <a name="getcurrentapartmenttype-function"></a><span data-ttu-id="94a15-103">GetCurrentApartmentType</span><span class="sxs-lookup"><span data-stu-id="94a15-103">GetCurrentApartmentType function</span></span>
<span data-ttu-id="94a15-104">Načte typ apartment, ve kterém volající provádí.</span><span class="sxs-lookup"><span data-stu-id="94a15-104">Retrieves the type of apartment in which the caller is executing.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="94a15-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94a15-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc,
   [in] IComThreadingInfo*    ptr,
   [out] APTTYPE*             aptType
);
```  

## <a name="parameters"></a><span data-ttu-id="94a15-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="94a15-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="94a15-107">[v] Tento parametr není použit.</span><span class="sxs-lookup"><span data-stu-id="94a15-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="94a15-108">[v] Ukazatel na instanci [IComThreadingInfo.](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo)</span><span class="sxs-lookup"><span data-stu-id="94a15-108">[in] A pointer to an [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) instance.</span></span>

`aptType`  
<span data-ttu-id="94a15-109">[out] Ukazatel na hodnotu výčtu [APTTYPE,](/windows/win32/api/objidlbase/ne-objidlbase-apttype) která označuje apartment volajícího.</span><span class="sxs-lookup"><span data-stu-id="94a15-109">[out] A pointer to an [APTTYPE](/windows/win32/api/objidlbase/ne-objidlbase-apttype) enumeration value that indicates the caller's apartment.</span></span>

## <a name="return-value"></a><span data-ttu-id="94a15-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="94a15-110">Return value</span></span>

|<span data-ttu-id="94a15-111">Trvalé</span><span class="sxs-lookup"><span data-stu-id="94a15-111">Constant</span></span>  |<span data-ttu-id="94a15-112">Hodnota</span><span class="sxs-lookup"><span data-stu-id="94a15-112">Value</span></span>  |<span data-ttu-id="94a15-113">Popis</span><span class="sxs-lookup"><span data-stu-id="94a15-113">Description</span></span>  |
|---------|---------|---------|
| `S_OK` | <span data-ttu-id="94a15-114">0</span><span class="sxs-lookup"><span data-stu-id="94a15-114">0</span></span> | <span data-ttu-id="94a15-115">Funkce byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="94a15-115">The function completed successfully.</span></span> |
| `E_FAIL` | <span data-ttu-id="94a15-116">0x80000008</span><span class="sxs-lookup"><span data-stu-id="94a15-116">0x80000008</span></span> | <span data-ttu-id="94a15-117">Volající není provádění v bytě.</span><span class="sxs-lookup"><span data-stu-id="94a15-117">The caller is not executing in an apartment.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="94a15-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="94a15-118">Remarks</span></span>

<span data-ttu-id="94a15-119">Tato funkce zabalí volání [metody IComThreadingInfo::GetCurrentApartmentType.](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype)</span><span class="sxs-lookup"><span data-stu-id="94a15-119">This function wraps a call to the [IComThreadingInfo::GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="94a15-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="94a15-120">Requirements</span></span>  
 <span data-ttu-id="94a15-121">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94a15-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94a15-122">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="94a15-122">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="94a15-123">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="94a15-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94a15-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="94a15-124">See also</span></span>

- [<span data-ttu-id="94a15-125">Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="94a15-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
