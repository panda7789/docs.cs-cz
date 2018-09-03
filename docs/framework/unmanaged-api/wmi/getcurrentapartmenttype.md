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
ms.openlocfilehash: 4de85eb310de70dc8fd61f7c06abca95ec267f87
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43463088"
---
# <a name="getcurrentapartmenttype-function"></a><span data-ttu-id="f9935-103">GetCurrentApartmentType – funkce</span><span class="sxs-lookup"><span data-stu-id="f9935-103">GetCurrentApartmentType function</span></span>
<span data-ttu-id="f9935-104">Získá typ objektu apartment, ve kterém je spuštěn volající.</span><span class="sxs-lookup"><span data-stu-id="f9935-104">Retrieves the type of apartment in which the caller is executing.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="f9935-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9935-105">Syntax</span></span>  
  
```  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc, 
   [in] IComThreadingInfo*    ptr, 
   [out] APTTYPE*             aptType
); 
```  

## <a name="parameters"></a><span data-ttu-id="f9935-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9935-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="f9935-107">[in] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="f9935-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="f9935-108">[in] Ukazatel [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) instance.</span><span class="sxs-lookup"><span data-stu-id="f9935-108">[in] A pointer to an [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) instance.</span></span>

`aptType`  
<span data-ttu-id="f9935-109">[out] Ukazatel [APTTYPE](/windows/desktop/api/objidlbase/ne-objidlbase-_apttype) hodnotu výčtu, která určuje volajícího objektu apartment.</span><span class="sxs-lookup"><span data-stu-id="f9935-109">[out] A pointer to an [APTTYPE](/windows/desktop/api/objidlbase/ne-objidlbase-_apttype) enumeration value that indicates the caller's apartment.</span></span>

## <a name="return-value"></a><span data-ttu-id="f9935-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f9935-110">Return value</span></span>


|<span data-ttu-id="f9935-111">Konstanta</span><span class="sxs-lookup"><span data-stu-id="f9935-111">Constant</span></span>  |<span data-ttu-id="f9935-112">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f9935-112">Value</span></span>  |<span data-ttu-id="f9935-113">Popis</span><span class="sxs-lookup"><span data-stu-id="f9935-113">Description</span></span>  |
|---------|---------|---------|
| `S_OK` | <span data-ttu-id="f9935-114">0</span><span class="sxs-lookup"><span data-stu-id="f9935-114">0</span></span> | <span data-ttu-id="f9935-115">Funkce, která byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="f9935-115">The function completed successfully.</span></span> |
| `E_FAIL` | <span data-ttu-id="f9935-116">0x80000008</span><span class="sxs-lookup"><span data-stu-id="f9935-116">0x80000008</span></span> | <span data-ttu-id="f9935-117">Volající není prováděna v komplexu.</span><span class="sxs-lookup"><span data-stu-id="f9935-117">The caller is not executing in an apartment.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="f9935-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f9935-118">Remarks</span></span>

<span data-ttu-id="f9935-119">Tato funkce zalamuje volání na [IComThreadingInfo::GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) metody.</span><span class="sxs-lookup"><span data-stu-id="f9935-119">This function wraps a call to the [IComThreadingInfo::GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f9935-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f9935-120">Requirements</span></span>  
 <span data-ttu-id="f9935-121">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9935-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9935-122">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="f9935-122">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="f9935-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f9935-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9935-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f9935-124">See also</span></span>  
[<span data-ttu-id="f9935-125">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="f9935-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
