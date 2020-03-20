---
title: Funkce GetQualifierSet (Unmanaged API Reference)
description: Funkce GetQualifierSet načte kvalifikátor pro třídu nebo instanci.
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
ms.openlocfilehash: 368f0a13871bd48780fa30b370d37157d2724bb8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176770"
---
# <a name="getqualifierset-function"></a><span data-ttu-id="59937-103">GetQualifierSet</span><span class="sxs-lookup"><span data-stu-id="59937-103">GetQualifierSet function</span></span>
<span data-ttu-id="59937-104">Načte kvalifikátor nastavenou pro instanci třídy nebo definici třídy.</span><span class="sxs-lookup"><span data-stu-id="59937-104">Retrieves the qualifier set for a class instance or a class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="59937-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59937-105">Syntax</span></span>  
  
```cpp  
HRESULT GetQualifierSet (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [out] IWbemQualifierSet  **ppQualSet
);
```  

## <a name="parameters"></a><span data-ttu-id="59937-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="59937-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="59937-107">[v] Tento parametr není použit.</span><span class="sxs-lookup"><span data-stu-id="59937-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="59937-108">[v] Ukazatel na instanci [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="59937-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`ppQualSet`  
<span data-ttu-id="59937-109">[out] Přijímá ukazatel rozhraní, který umožňuje přístup k kvalifikátory objektu třídy.</span><span class="sxs-lookup"><span data-stu-id="59937-109">[out] Receives the interface pointer that allows access to the qualifiers of the class object.</span></span> <span data-ttu-id="59937-110">`ppQualSet`nemůže `null`být .</span><span class="sxs-lookup"><span data-stu-id="59937-110">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="59937-111">Pokud dojde k chybě, nový objekt není vrácena a ukazatel zůstane beze změny.</span><span class="sxs-lookup"><span data-stu-id="59937-111">If an error occurs, a new object is not returned, and the pointer is left unmodified.</span></span>

## <a name="return-value"></a><span data-ttu-id="59937-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="59937-112">Return value</span></span>

<span data-ttu-id="59937-113">Následující hodnoty vrácené touto funkcí jsou definovány v souboru *hlavičky WbemCli.h,* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="59937-113">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="59937-114">Trvalé</span><span class="sxs-lookup"><span data-stu-id="59937-114">Constant</span></span>  |<span data-ttu-id="59937-115">Hodnota</span><span class="sxs-lookup"><span data-stu-id="59937-115">Value</span></span>  |<span data-ttu-id="59937-116">Popis</span><span class="sxs-lookup"><span data-stu-id="59937-116">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="59937-117">0x80041001</span><span class="sxs-lookup"><span data-stu-id="59937-117">0x80041001</span></span> | <span data-ttu-id="59937-118">Došlo k obecnému selhání.</span><span class="sxs-lookup"><span data-stu-id="59937-118">There has been a general failure.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="59937-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="59937-119">0x80041002</span></span> | <span data-ttu-id="59937-120">Zadaná metoda neexistuje.</span><span class="sxs-lookup"><span data-stu-id="59937-120">The specified method does not exist.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="59937-121">0x80041006</span><span class="sxs-lookup"><span data-stu-id="59937-121">0x80041006</span></span> | <span data-ttu-id="59937-122">K dokončení operace není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="59937-122">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="59937-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="59937-123">0x80041008</span></span> | <span data-ttu-id="59937-124">Parametr je `null`.</span><span class="sxs-lookup"><span data-stu-id="59937-124">A parameter is `null`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="59937-125">0</span><span class="sxs-lookup"><span data-stu-id="59937-125">0</span></span> | <span data-ttu-id="59937-126">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="59937-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="59937-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="59937-127">Remarks</span></span>

<span data-ttu-id="59937-128">Tato funkce zabalí volání [metody IWbemClassObject::GetQualifierSet.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getqualifierset)</span><span class="sxs-lookup"><span data-stu-id="59937-128">This function wraps a call to the [IWbemClassObject::GetQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getqualifierset) method.</span></span>

<span data-ttu-id="59937-129">[Ukazatel IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) umožňuje volajícímu přidat, upravit nebo odstranit tyto kvalifikátory.</span><span class="sxs-lookup"><span data-stu-id="59937-129">The [IWbemQualifierSet pointer](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) lets the caller add, edit, or delete these qualifiers.</span></span> <span data-ttu-id="59937-130">Tyto přidané, upravené nebo odstraněné kvalifikátory platí pro celou definici instance nebo třídy.</span><span class="sxs-lookup"><span data-stu-id="59937-130">Such added, edited, or deleted qualifiers apply to the entire instance or class definition.</span></span>

## <a name="requirements"></a><span data-ttu-id="59937-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="59937-131">Requirements</span></span>  
<span data-ttu-id="59937-132">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59937-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59937-133">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="59937-133">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="59937-134">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="59937-134">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59937-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="59937-135">See also</span></span>

- [<span data-ttu-id="59937-136">Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="59937-136">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
