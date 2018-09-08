---
title: Funkce GetQualifierSet (referenční dokumentace nespravovaného rozhraní API)
description: Funkce GetQualifierSet načte kvalifikátor nastavení pro třídu nebo instanci.
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
ms.openlocfilehash: 635dc7605af00f2662a9f9553adefafcd25f9452
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44201241"
---
# <a name="getqualifierset-function"></a><span data-ttu-id="cebc9-103">GetQualifierSet – funkce</span><span class="sxs-lookup"><span data-stu-id="cebc9-103">GetQualifierSet function</span></span>
<span data-ttu-id="cebc9-104">Načte kvalifikátor, nastavte pro instanci třídy nebo definice třídy.</span><span class="sxs-lookup"><span data-stu-id="cebc9-104">Retrieves the qualifier set for a class instance or a class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="cebc9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cebc9-105">Syntax</span></span>  
  
```  
HRESULT GetQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a><span data-ttu-id="cebc9-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="cebc9-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="cebc9-107">[in] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="cebc9-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="cebc9-108">[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span><span class="sxs-lookup"><span data-stu-id="cebc9-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`ppQualSet`  
<span data-ttu-id="cebc9-109">[out] Přijímá ukazatel rozhraní, která umožňuje přístup k kvalifikátory třídy objektu.</span><span class="sxs-lookup"><span data-stu-id="cebc9-109">[out] Receives the interface pointer that allows access to the qualifiers of the class object.</span></span> <span data-ttu-id="cebc9-110">`ppQualSet` nemůže být `null`.</span><span class="sxs-lookup"><span data-stu-id="cebc9-110">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="cebc9-111">Pokud dojde k chybě, není vrátí nový objekt a ukazatel myši zůstane bez úprav.</span><span class="sxs-lookup"><span data-stu-id="cebc9-111">If an error occurs, a new object is not returned, and the pointer is left unmodified.</span></span> 

## <a name="return-value"></a><span data-ttu-id="cebc9-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="cebc9-112">Return value</span></span>

<span data-ttu-id="cebc9-113">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="cebc9-113">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="cebc9-114">Konstanta</span><span class="sxs-lookup"><span data-stu-id="cebc9-114">Constant</span></span>  |<span data-ttu-id="cebc9-115">Hodnota</span><span class="sxs-lookup"><span data-stu-id="cebc9-115">Value</span></span>  |<span data-ttu-id="cebc9-116">Popis</span><span class="sxs-lookup"><span data-stu-id="cebc9-116">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="cebc9-117">0x80041001</span><span class="sxs-lookup"><span data-stu-id="cebc9-117">0x80041001</span></span> | <span data-ttu-id="cebc9-118">Obecné selhání došlo.</span><span class="sxs-lookup"><span data-stu-id="cebc9-118">There has been a general failure.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="cebc9-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="cebc9-119">0x80041002</span></span> | <span data-ttu-id="cebc9-120">Zadaná metoda neexistuje.</span><span class="sxs-lookup"><span data-stu-id="cebc9-120">The specified method does not exist.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="cebc9-121">0x80041006</span><span class="sxs-lookup"><span data-stu-id="cebc9-121">0x80041006</span></span> | <span data-ttu-id="cebc9-122">Nedostatek paměti je k dispozici k dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="cebc9-122">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="cebc9-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="cebc9-123">0x80041008</span></span> | <span data-ttu-id="cebc9-124">Parametr je `null`.</span><span class="sxs-lookup"><span data-stu-id="cebc9-124">A parameter is `null`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="cebc9-125">0</span><span class="sxs-lookup"><span data-stu-id="cebc9-125">0</span></span> | <span data-ttu-id="cebc9-126">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="cebc9-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="cebc9-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cebc9-127">Remarks</span></span>

<span data-ttu-id="cebc9-128">Tato funkce zalamuje volání na [IWbemClassObject::GetQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getqualifierset) metody.</span><span class="sxs-lookup"><span data-stu-id="cebc9-128">This function wraps a call to the [IWbemClassObject::GetQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getqualifierset) method.</span></span> 

<span data-ttu-id="cebc9-129">[IWbemQualifierSet ukazatel](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) umožňuje volajícímu přidat, upravit nebo odstranit kvalifikátory.</span><span class="sxs-lookup"><span data-stu-id="cebc9-129">The [IWbemQualifierSet pointer](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) lets the caller add, edit, or delete these qualifiers.</span></span> <span data-ttu-id="cebc9-130">Tyto přidané, upravené nebo odstraněné kvalifikátory platí pro celou definici třídy nebo instance.</span><span class="sxs-lookup"><span data-stu-id="cebc9-130">Such added, edited, or deleted qualifiers apply to the entire instance or class definition.</span></span>

## <a name="requirements"></a><span data-ttu-id="cebc9-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cebc9-131">Requirements</span></span>  
<span data-ttu-id="cebc9-132">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cebc9-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cebc9-133">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="cebc9-133">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="cebc9-134">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="cebc9-134">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cebc9-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cebc9-135">See also</span></span>  
[<span data-ttu-id="cebc9-136">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="cebc9-136">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
