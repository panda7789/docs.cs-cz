---
title: "Funkce SpawnDerivedClass (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce SpawnDerivedClass vytvoří nový objekt, který je odvozen z objektu."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: SpawnDerivedClass
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: SpawnDerivedClass
helpviewer_keywords: SpawnDerivedClass function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 16f9a762c87e1e181202739b70cd978a80864f04
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2017
---
# <a name="spawnderivedclass-function"></a><span data-ttu-id="fb3b5-103">SpawnDerivedClass – funkce</span><span class="sxs-lookup"><span data-stu-id="fb3b5-103">SpawnDerivedClass function</span></span>
<span data-ttu-id="fb3b5-104">Vytvoří objekt nově odvozených tříd ze zadaného objektu.</span><span class="sxs-lookup"><span data-stu-id="fb3b5-104">Creates a newly derived class object from a specified object.</span></span>    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="fb3b5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb3b5-105">Syntax</span></span>  
  
```  
HRESULT SpawnDerivedClass (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewClass); 
```  

## <a name="parameters"></a><span data-ttu-id="fb3b5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="fb3b5-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="fb3b5-107">[v] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="fb3b5-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="fb3b5-108">[v] Ukazatel na [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="fb3b5-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`lFlags`  
<span data-ttu-id="fb3b5-109">[v] Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="fb3b5-109">[in] Reserved.</span></span> <span data-ttu-id="fb3b5-110">Tento parametr musí být 0.</span><span class="sxs-lookup"><span data-stu-id="fb3b5-110">This parameter must be 0.</span></span>

`ppNewClass`  
<span data-ttu-id="fb3b5-111">[out] Obdrží má ukazatel na nový objekt – třída definice.</span><span class="sxs-lookup"><span data-stu-id="fb3b5-111">[out] Receives the pointer to the new class definition object.</span></span> <span data-ttu-id="fb3b5-112">Pokud dojde k chybě, nový objekt, který se vrátí, a `ppNewClass` je ponechat beze změny doleva.</span><span class="sxs-lookup"><span data-stu-id="fb3b5-112">If an error occurs, a new object is not returned, and `ppNewClass` is left unmodified.</span></span> <span data-ttu-id="fb3b5-113">Jeho hodnota nemůže být `null`.</span><span class="sxs-lookup"><span data-stu-id="fb3b5-113">Its value cannot be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="fb3b5-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fb3b5-114">Return value</span></span>

<span data-ttu-id="fb3b5-115">Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="fb3b5-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="fb3b5-116">Konstanta</span><span class="sxs-lookup"><span data-stu-id="fb3b5-116">Constant</span></span>  |<span data-ttu-id="fb3b5-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="fb3b5-117">Value</span></span>  |<span data-ttu-id="fb3b5-118">Popis</span><span class="sxs-lookup"><span data-stu-id="fb3b5-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="fb3b5-119">0x80041001</span><span class="sxs-lookup"><span data-stu-id="fb3b5-119">0x80041001</span></span> | <span data-ttu-id="fb3b5-120">Došlo k obecné chybě.</span><span class="sxs-lookup"><span data-stu-id="fb3b5-120">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_OPERATION` | <span data-ttu-id="fb3b5-121">0x80041016</span><span class="sxs-lookup"><span data-stu-id="fb3b5-121">0x80041016</span></span> | <span data-ttu-id="fb3b5-122">Neplatná operace, jako například vytvoření třídy z instance, byl požadován.</span><span class="sxs-lookup"><span data-stu-id="fb3b5-122">An invalid operation, such as spawning a class from an instance, was requested.</span></span> |
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="fb3b5-123">Třída zdroje byla plně definována nebo zaregistrována Správa systému Windows, tak nové odvozené třídy není povoleno.</span><span class="sxs-lookup"><span data-stu-id="fb3b5-123">The source class was not completely defined or registered with Windows Management, so a new derived class is not permitted.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="fb3b5-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="fb3b5-124">0x80041006</span></span> | <span data-ttu-id="fb3b5-125">Je k dispozici k dokončení operace není dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="fb3b5-125">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="fb3b5-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="fb3b5-126">0x80041008</span></span> | <span data-ttu-id="fb3b5-127">`ppNewClass`je `null`.</span><span class="sxs-lookup"><span data-stu-id="fb3b5-127">`ppNewClass` is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="fb3b5-128">0</span><span class="sxs-lookup"><span data-stu-id="fb3b5-128">0</span></span> | <span data-ttu-id="fb3b5-129">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="fb3b5-129">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="fb3b5-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fb3b5-130">Remarks</span></span>

<span data-ttu-id="fb3b5-131">Tato funkce zabalí volání [IWbemClassObject::SpawnDerivedClass](https://msdn.microsoft.com/library/aa391436(v=vs.85).aspx) metoda.</span><span class="sxs-lookup"><span data-stu-id="fb3b5-131">This function wraps a call to the [IWbemClassObject::SpawnDerivedClass](https://msdn.microsoft.com/library/aa391436(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="fb3b5-132">`ptr`musí být definice třídy, který se stane nadřazené třídy objektu vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="fb3b5-132">`ptr` must be a class definition that becomes the parent class of the spawned object.</span></span> <span data-ttu-id="fb3b5-133">Vráceného objektu se změní na podtřídy aktuálního objektu.</span><span class="sxs-lookup"><span data-stu-id="fb3b5-133">The returned object becomes a subclass of the current object.</span></span>

<span data-ttu-id="fb3b5-134">Nový objekt vrácený v `ppNewClass` automaticky stane podtřídy aktuálního objektu.</span><span class="sxs-lookup"><span data-stu-id="fb3b5-134">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="fb3b5-135">Toto chování nelze přepsat.</span><span class="sxs-lookup"><span data-stu-id="fb3b5-135">This behavior cannot be overridden.</span></span> <span data-ttu-id="fb3b5-136">Není k dispozici žádnou jinou metodu, pomocí kterého lze vytvořit podtřídy (odvozené třídy).</span><span class="sxs-lookup"><span data-stu-id="fb3b5-136">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="fb3b5-137">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fb3b5-137">Requirements</span></span>  
 <span data-ttu-id="fb3b5-138">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb3b5-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb3b5-139">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="fb3b5-139">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="fb3b5-140">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="fb3b5-140">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb3b5-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="fb3b5-141">See also</span></span>  
[<span data-ttu-id="fb3b5-142">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="fb3b5-142">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
