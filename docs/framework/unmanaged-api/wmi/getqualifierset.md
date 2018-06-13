---
title: Funkce GetQualifierSet (referenční dokumentace nespravovaného rozhraní API)
description: Funkce GetQualifierSet načte kvalifikátor nastavení pro třídy nebo instance.
ms.date: 11/06/2017
api_name:
- GetQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetQualifierSet
helpviewer_keywords:
- GetQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0b50befa4346e17048598afd3d018dbde2fe8572
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458559"
---
# <a name="getqualifierset-function"></a><span data-ttu-id="d2c62-103">GetQualifierSet – funkce</span><span class="sxs-lookup"><span data-stu-id="d2c62-103">GetQualifierSet function</span></span>
<span data-ttu-id="d2c62-104">Načte kvalifikátor pro instanci třídy nebo definici třídy.</span><span class="sxs-lookup"><span data-stu-id="d2c62-104">Retrieves the qualifier set for a class instance or a class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="d2c62-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d2c62-105">Syntax</span></span>  
  
```  
HRESULT GetQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a><span data-ttu-id="d2c62-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d2c62-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="d2c62-107">[v] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="d2c62-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="d2c62-108">[v] Ukazatel na [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="d2c62-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`ppQualSet`  
<span data-ttu-id="d2c62-109">[out] Ukazatel rozhraní, které umožňuje přístup k kvalifikátory třídy objektu obdrží.</span><span class="sxs-lookup"><span data-stu-id="d2c62-109">[out] Receives the interface pointer that allows access to the qualifiers of the class object.</span></span> <span data-ttu-id="d2c62-110">`ppQualSet` nemůže být `null`.</span><span class="sxs-lookup"><span data-stu-id="d2c62-110">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="d2c62-111">Pokud dojde k chybě, nevrátí nový objekt a ukazatele je ponechán beze změny.</span><span class="sxs-lookup"><span data-stu-id="d2c62-111">If an error occurs, a new object is not returned, and the pointer is left unmodified.</span></span> 

## <a name="return-value"></a><span data-ttu-id="d2c62-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d2c62-112">Return value</span></span>

<span data-ttu-id="d2c62-113">Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="d2c62-113">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="d2c62-114">Konstanta</span><span class="sxs-lookup"><span data-stu-id="d2c62-114">Constant</span></span>  |<span data-ttu-id="d2c62-115">Hodnota</span><span class="sxs-lookup"><span data-stu-id="d2c62-115">Value</span></span>  |<span data-ttu-id="d2c62-116">Popis</span><span class="sxs-lookup"><span data-stu-id="d2c62-116">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="d2c62-117">0x80041001</span><span class="sxs-lookup"><span data-stu-id="d2c62-117">0x80041001</span></span> | <span data-ttu-id="d2c62-118">Došlo k obecné chybě.</span><span class="sxs-lookup"><span data-stu-id="d2c62-118">There has been a general failure.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="d2c62-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="d2c62-119">0x80041002</span></span> | <span data-ttu-id="d2c62-120">Zadaná metoda neexistuje.</span><span class="sxs-lookup"><span data-stu-id="d2c62-120">The specified method does not exist.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="d2c62-121">0x80041006</span><span class="sxs-lookup"><span data-stu-id="d2c62-121">0x80041006</span></span> | <span data-ttu-id="d2c62-122">Je k dispozici k dokončení operace není dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="d2c62-122">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="d2c62-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="d2c62-123">0x80041008</span></span> | <span data-ttu-id="d2c62-124">Parametr je `null`.</span><span class="sxs-lookup"><span data-stu-id="d2c62-124">A parameter is `null`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="d2c62-125">0</span><span class="sxs-lookup"><span data-stu-id="d2c62-125">0</span></span> | <span data-ttu-id="d2c62-126">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="d2c62-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="d2c62-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d2c62-127">Remarks</span></span>

<span data-ttu-id="d2c62-128">Tato funkce zabalí volání [IWbemClassObject::GetQualifierSet](https://msdn.microsoft.com/library/aa391451(v=vs.85).aspx) metoda.</span><span class="sxs-lookup"><span data-stu-id="d2c62-128">This function wraps a call to the [IWbemClassObject::GetQualifierSet](https://msdn.microsoft.com/library/aa391451(v=vs.85).aspx) method.</span></span> 

<span data-ttu-id="d2c62-129">[IWbemQualifierSet ukazatel](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) umožňuje přidat, upravit nebo odstranit tyto kvalifikátory volající.</span><span class="sxs-lookup"><span data-stu-id="d2c62-129">The [IWbemQualifierSet pointer](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) lets the caller add, edit, or delete these qualifiers.</span></span> <span data-ttu-id="d2c62-130">Takové added, upravené nebo odstraněné kvalifikátory se vztahují na celou definice třídy nebo instance.</span><span class="sxs-lookup"><span data-stu-id="d2c62-130">Such added, edited, or deleted qualifiers apply to the entire instance or class definition.</span></span>

## <a name="requirements"></a><span data-ttu-id="d2c62-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d2c62-131">Requirements</span></span>  
<span data-ttu-id="d2c62-132">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2c62-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2c62-133">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="d2c62-133">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="d2c62-134">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d2c62-134">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2c62-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="d2c62-135">See also</span></span>  
[<span data-ttu-id="d2c62-136">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="d2c62-136">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
