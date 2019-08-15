---
title: GetCurrentApartmentType – funkce (Reference nespravovaného rozhraní API)
description: Funkce GetCurrentApartmentType načte typ objektu apartment, ve kterém je volající spuštěn.
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
ms.openlocfilehash: 68eb4ba653098d847022da45e610cb4fa5496a8c
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69037968"
---
# <a name="getcurrentapartmenttype-function"></a><span data-ttu-id="dddc2-103">GetCurrentApartmentType function</span><span class="sxs-lookup"><span data-stu-id="dddc2-103">GetCurrentApartmentType function</span></span>
<span data-ttu-id="dddc2-104">Načte typ objektu apartment, ve kterém je volající spuštěn.</span><span class="sxs-lookup"><span data-stu-id="dddc2-104">Retrieves the type of apartment in which the caller is executing.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="dddc2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dddc2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc, 
   [in] IComThreadingInfo*    ptr, 
   [out] APTTYPE*             aptType
); 
```  

## <a name="parameters"></a><span data-ttu-id="dddc2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="dddc2-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="dddc2-107">pro Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="dddc2-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="dddc2-108">pro Ukazatel na instanci [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) .</span><span class="sxs-lookup"><span data-stu-id="dddc2-108">[in] A pointer to an [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) instance.</span></span>

`aptType`  
<span data-ttu-id="dddc2-109">mimo Ukazatel na hodnotu výčtu [APTTYPE](/windows/win32/api/objidlbase/ne-objidlbase-apttype) , která označuje objekt Apartment volajícího.</span><span class="sxs-lookup"><span data-stu-id="dddc2-109">[out] A pointer to an [APTTYPE](/windows/win32/api/objidlbase/ne-objidlbase-apttype) enumeration value that indicates the caller's apartment.</span></span>

## <a name="return-value"></a><span data-ttu-id="dddc2-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="dddc2-110">Return value</span></span>

|<span data-ttu-id="dddc2-111">Konstanta</span><span class="sxs-lookup"><span data-stu-id="dddc2-111">Constant</span></span>  |<span data-ttu-id="dddc2-112">Value</span><span class="sxs-lookup"><span data-stu-id="dddc2-112">Value</span></span>  |<span data-ttu-id="dddc2-113">Popis</span><span class="sxs-lookup"><span data-stu-id="dddc2-113">Description</span></span>  |
|---------|---------|---------|
| `S_OK` | <span data-ttu-id="dddc2-114">0</span><span class="sxs-lookup"><span data-stu-id="dddc2-114">0</span></span> | <span data-ttu-id="dddc2-115">Funkce byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="dddc2-115">The function completed successfully.</span></span> |
| `E_FAIL` | <span data-ttu-id="dddc2-116">0x80000008</span><span class="sxs-lookup"><span data-stu-id="dddc2-116">0x80000008</span></span> | <span data-ttu-id="dddc2-117">Volající není spuštěn v objektu apartment.</span><span class="sxs-lookup"><span data-stu-id="dddc2-117">The caller is not executing in an apartment.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="dddc2-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dddc2-118">Remarks</span></span>

<span data-ttu-id="dddc2-119">Tato funkce zalomí volání metody [IComThreadingInfo:: GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) .</span><span class="sxs-lookup"><span data-stu-id="dddc2-119">This function wraps a call to the [IComThreadingInfo::GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="dddc2-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dddc2-120">Requirements</span></span>  
 <span data-ttu-id="dddc2-121">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dddc2-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dddc2-122">**Hlaviček** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="dddc2-122">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="dddc2-123">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="dddc2-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dddc2-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dddc2-124">See also</span></span>

- [<span data-ttu-id="dddc2-125">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="dddc2-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
