---
title: Funkce SpawnDerivedClass (Nespravovaný odkaz na rozhraní API)
description: Funkce SpawnDerivedClass vytvoří nový objekt, který je odvozen od objektu.
ms.date: 11/06/2017
api_name:
- SpawnDerivedClass
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnDerivedClass
helpviewer_keywords:
- SpawnDerivedClass function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: e9784f8a024c788823dc702794b2b86eea1827bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174846"
---
# <a name="spawnderivedclass-function"></a><span data-ttu-id="07dd2-103">SpawnDerivedClass</span><span class="sxs-lookup"><span data-stu-id="07dd2-103">SpawnDerivedClass function</span></span>
<span data-ttu-id="07dd2-104">Vytvoří nově odvozený objekt třídy z určeného objektu.</span><span class="sxs-lookup"><span data-stu-id="07dd2-104">Creates a newly derived class object from a specified object.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="07dd2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="07dd2-105">Syntax</span></span>  
  
```cpp  
HRESULT SpawnDerivedClass (
   [in] int                  vFunc,
   [in] IWbemClassObject*    ptr,
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewClass);
```  

## <a name="parameters"></a><span data-ttu-id="07dd2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="07dd2-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="07dd2-107">[v] Tento parametr není použit.</span><span class="sxs-lookup"><span data-stu-id="07dd2-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="07dd2-108">[v] Ukazatel na instanci [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="07dd2-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="07dd2-109">[v] Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="07dd2-109">[in] Reserved.</span></span> <span data-ttu-id="07dd2-110">Tento parametr musí být 0.</span><span class="sxs-lookup"><span data-stu-id="07dd2-110">This parameter must be 0.</span></span>

`ppNewClass`  
<span data-ttu-id="07dd2-111">[out] Obdrží ukazatel na nový objekt definice třídy.</span><span class="sxs-lookup"><span data-stu-id="07dd2-111">[out] Receives the pointer to the new class definition object.</span></span> <span data-ttu-id="07dd2-112">Pokud dojde k chybě, nový objekt není `ppNewClass` vrácena a je ponechána beze změny.</span><span class="sxs-lookup"><span data-stu-id="07dd2-112">If an error occurs, a new object is not returned, and `ppNewClass` is left unmodified.</span></span> <span data-ttu-id="07dd2-113">Jeho hodnota `null`nemůže být .</span><span class="sxs-lookup"><span data-stu-id="07dd2-113">Its value cannot be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="07dd2-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="07dd2-114">Return value</span></span>

<span data-ttu-id="07dd2-115">Následující hodnoty vrácené touto funkcí jsou definovány v souboru *hlavičky WbemCli.h,* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="07dd2-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="07dd2-116">Trvalé</span><span class="sxs-lookup"><span data-stu-id="07dd2-116">Constant</span></span>  |<span data-ttu-id="07dd2-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="07dd2-117">Value</span></span>  |<span data-ttu-id="07dd2-118">Popis</span><span class="sxs-lookup"><span data-stu-id="07dd2-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="07dd2-119">0x80041001</span><span class="sxs-lookup"><span data-stu-id="07dd2-119">0x80041001</span></span> | <span data-ttu-id="07dd2-120">Došlo k obecnému selhání.</span><span class="sxs-lookup"><span data-stu-id="07dd2-120">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_OPERATION` | <span data-ttu-id="07dd2-121">0x80041016</span><span class="sxs-lookup"><span data-stu-id="07dd2-121">0x80041016</span></span> | <span data-ttu-id="07dd2-122">Byla požadována neplatná operace, například vytvoření třídy z instance.</span><span class="sxs-lookup"><span data-stu-id="07dd2-122">An invalid operation, such as spawning a class from an instance, was requested.</span></span> |
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="07dd2-123">Source třída nebyla zcela definována nebo registrována pomocí správy systému Windows, takže nová odvozená třída není povolena.</span><span class="sxs-lookup"><span data-stu-id="07dd2-123">The source class was not completely defined or registered with Windows Management, so a new derived class is not permitted.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="07dd2-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="07dd2-124">0x80041006</span></span> | <span data-ttu-id="07dd2-125">K dokončení operace není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="07dd2-125">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="07dd2-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="07dd2-126">0x80041008</span></span> | <span data-ttu-id="07dd2-127">`ppNewClass` je `null`.</span><span class="sxs-lookup"><span data-stu-id="07dd2-127">`ppNewClass` is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="07dd2-128">0</span><span class="sxs-lookup"><span data-stu-id="07dd2-128">0</span></span> | <span data-ttu-id="07dd2-129">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="07dd2-129">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="07dd2-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="07dd2-130">Remarks</span></span>

<span data-ttu-id="07dd2-131">Tato funkce zabalí volání [metody IWbemClassObject::SpawnDerivedClass.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone)</span><span class="sxs-lookup"><span data-stu-id="07dd2-131">This function wraps a call to the [IWbemClassObject::SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) method.</span></span>

<span data-ttu-id="07dd2-132">`ptr`musí být definice třídy, která se stane nadřazenou třídou objektu spawned.</span><span class="sxs-lookup"><span data-stu-id="07dd2-132">`ptr` must be a class definition that becomes the parent class of the spawned object.</span></span> <span data-ttu-id="07dd2-133">Vrácený objekt se stane podtřídou aktuálního objektu.</span><span class="sxs-lookup"><span data-stu-id="07dd2-133">The returned object becomes a subclass of the current object.</span></span>

<span data-ttu-id="07dd2-134">Nový objekt vrácený automaticky `ppNewClass` se stane podtřídou aktuálního objektu.</span><span class="sxs-lookup"><span data-stu-id="07dd2-134">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="07dd2-135">Toto chování nelze přepsat.</span><span class="sxs-lookup"><span data-stu-id="07dd2-135">This behavior cannot be overridden.</span></span> <span data-ttu-id="07dd2-136">Neexistuje žádná jiná metoda, kterou lze vytvořit podtřídy (odvozené třídy).</span><span class="sxs-lookup"><span data-stu-id="07dd2-136">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="07dd2-137">Požadavky</span><span class="sxs-lookup"><span data-stu-id="07dd2-137">Requirements</span></span>  
 <span data-ttu-id="07dd2-138">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07dd2-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07dd2-139">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="07dd2-139">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="07dd2-140">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="07dd2-140">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07dd2-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="07dd2-141">See also</span></span>

- [<span data-ttu-id="07dd2-142">Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="07dd2-142">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
