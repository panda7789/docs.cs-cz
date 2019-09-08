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
ms.openlocfilehash: ff64be47802a46979818ab54cc3efb4112dd05e0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798624"
---
# <a name="getcurrentapartmenttype-function"></a><span data-ttu-id="8facc-103">GetCurrentApartmentType function</span><span class="sxs-lookup"><span data-stu-id="8facc-103">GetCurrentApartmentType function</span></span>
<span data-ttu-id="8facc-104">Načte typ objektu apartment, ve kterém je volající spuštěn.</span><span class="sxs-lookup"><span data-stu-id="8facc-104">Retrieves the type of apartment in which the caller is executing.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="8facc-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8facc-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc, 
   [in] IComThreadingInfo*    ptr, 
   [out] APTTYPE*             aptType
); 
```  

## <a name="parameters"></a><span data-ttu-id="8facc-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8facc-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="8facc-107">pro Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="8facc-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="8facc-108">pro Ukazatel na instanci [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) .</span><span class="sxs-lookup"><span data-stu-id="8facc-108">[in] A pointer to an [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) instance.</span></span>

`aptType`  
<span data-ttu-id="8facc-109">mimo Ukazatel na hodnotu výčtu [APTTYPE](/windows/win32/api/objidlbase/ne-objidlbase-apttype) , která označuje objekt Apartment volajícího.</span><span class="sxs-lookup"><span data-stu-id="8facc-109">[out] A pointer to an [APTTYPE](/windows/win32/api/objidlbase/ne-objidlbase-apttype) enumeration value that indicates the caller's apartment.</span></span>

## <a name="return-value"></a><span data-ttu-id="8facc-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8facc-110">Return value</span></span>

|<span data-ttu-id="8facc-111">Konstanta</span><span class="sxs-lookup"><span data-stu-id="8facc-111">Constant</span></span>  |<span data-ttu-id="8facc-112">Value</span><span class="sxs-lookup"><span data-stu-id="8facc-112">Value</span></span>  |<span data-ttu-id="8facc-113">Popis</span><span class="sxs-lookup"><span data-stu-id="8facc-113">Description</span></span>  |
|---------|---------|---------|
| `S_OK` | <span data-ttu-id="8facc-114">0</span><span class="sxs-lookup"><span data-stu-id="8facc-114">0</span></span> | <span data-ttu-id="8facc-115">Funkce byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="8facc-115">The function completed successfully.</span></span> |
| `E_FAIL` | <span data-ttu-id="8facc-116">0x80000008</span><span class="sxs-lookup"><span data-stu-id="8facc-116">0x80000008</span></span> | <span data-ttu-id="8facc-117">Volající není spuštěn v objektu apartment.</span><span class="sxs-lookup"><span data-stu-id="8facc-117">The caller is not executing in an apartment.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="8facc-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8facc-118">Remarks</span></span>

<span data-ttu-id="8facc-119">Tato funkce zalomí volání metody [IComThreadingInfo:: GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) .</span><span class="sxs-lookup"><span data-stu-id="8facc-119">This function wraps a call to the [IComThreadingInfo::GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="8facc-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8facc-120">Requirements</span></span>  
 <span data-ttu-id="8facc-121">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8facc-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8facc-122">**Hlaviček** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="8facc-122">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="8facc-123">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8facc-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8facc-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8facc-124">See also</span></span>

- [<span data-ttu-id="8facc-125">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="8facc-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
