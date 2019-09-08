---
title: SpawnDerivedClass – funkce (Reference nespravovaného rozhraní API)
description: Funkce SpawnDerivedClass vytvoří nový objekt, který je odvozen z objektu.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c213f311f1af1e56d0ce24eba3b76f33be541323
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798226"
---
# <a name="spawnderivedclass-function"></a><span data-ttu-id="08cb9-103">SpawnDerivedClass – funkce</span><span class="sxs-lookup"><span data-stu-id="08cb9-103">SpawnDerivedClass function</span></span>
<span data-ttu-id="08cb9-104">Vytvoří nově odvozený objekt třídy ze zadaného objektu.</span><span class="sxs-lookup"><span data-stu-id="08cb9-104">Creates a newly derived class object from a specified object.</span></span>    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="08cb9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08cb9-105">Syntax</span></span>  
  
```cpp  
HRESULT SpawnDerivedClass (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewClass); 
```  

## <a name="parameters"></a><span data-ttu-id="08cb9-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="08cb9-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="08cb9-107">pro Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="08cb9-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="08cb9-108">pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="08cb9-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="08cb9-109">pro Rezervovaný.</span><span class="sxs-lookup"><span data-stu-id="08cb9-109">[in] Reserved.</span></span> <span data-ttu-id="08cb9-110">Tento parametr musí mít hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="08cb9-110">This parameter must be 0.</span></span>

`ppNewClass`  
<span data-ttu-id="08cb9-111">mimo Přijme ukazatel na nový objekt definice třídy.</span><span class="sxs-lookup"><span data-stu-id="08cb9-111">[out] Receives the pointer to the new class definition object.</span></span> <span data-ttu-id="08cb9-112">Pokud dojde k chybě, nový objekt se nevrátí a `ppNewClass` zůstane beze změny.</span><span class="sxs-lookup"><span data-stu-id="08cb9-112">If an error occurs, a new object is not returned, and `ppNewClass` is left unmodified.</span></span> <span data-ttu-id="08cb9-113">Jeho hodnota nemůže být `null`.</span><span class="sxs-lookup"><span data-stu-id="08cb9-113">Its value cannot be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="08cb9-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="08cb9-114">Return value</span></span>

<span data-ttu-id="08cb9-115">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="08cb9-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="08cb9-116">Konstanta</span><span class="sxs-lookup"><span data-stu-id="08cb9-116">Constant</span></span>  |<span data-ttu-id="08cb9-117">Value</span><span class="sxs-lookup"><span data-stu-id="08cb9-117">Value</span></span>  |<span data-ttu-id="08cb9-118">Popis</span><span class="sxs-lookup"><span data-stu-id="08cb9-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="08cb9-119">0x80041001</span><span class="sxs-lookup"><span data-stu-id="08cb9-119">0x80041001</span></span> | <span data-ttu-id="08cb9-120">Došlo k obecné chybě.</span><span class="sxs-lookup"><span data-stu-id="08cb9-120">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_OPERATION` | <span data-ttu-id="08cb9-121">0x80041016</span><span class="sxs-lookup"><span data-stu-id="08cb9-121">0x80041016</span></span> | <span data-ttu-id="08cb9-122">Byla požadována neplatná operace, například vytvoření třídy z instance.</span><span class="sxs-lookup"><span data-stu-id="08cb9-122">An invalid operation, such as spawning a class from an instance, was requested.</span></span> |
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="08cb9-123">Třída Source nebyla zcela definována ani registrována se správou systému Windows, takže nová odvozená třída není povolena.</span><span class="sxs-lookup"><span data-stu-id="08cb9-123">The source class was not completely defined or registered with Windows Management, so a new derived class is not permitted.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="08cb9-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="08cb9-124">0x80041006</span></span> | <span data-ttu-id="08cb9-125">K dokončení této operace není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="08cb9-125">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="08cb9-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="08cb9-126">0x80041008</span></span> | <span data-ttu-id="08cb9-127">`ppNewClass`je `null`.</span><span class="sxs-lookup"><span data-stu-id="08cb9-127">`ppNewClass` is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="08cb9-128">0</span><span class="sxs-lookup"><span data-stu-id="08cb9-128">0</span></span> | <span data-ttu-id="08cb9-129">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="08cb9-129">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="08cb9-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="08cb9-130">Remarks</span></span>

<span data-ttu-id="08cb9-131">Tato funkce zalomí volání metody [IWbemclassObject:: SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) .</span><span class="sxs-lookup"><span data-stu-id="08cb9-131">This function wraps a call to the [IWbemClassObject::SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) method.</span></span>

<span data-ttu-id="08cb9-132">`ptr`musí se jednat o definici třídy, která se stala nadřazenou třídou vytvořeného objektu.</span><span class="sxs-lookup"><span data-stu-id="08cb9-132">`ptr` must be a class definition that becomes the parent class of the spawned object.</span></span> <span data-ttu-id="08cb9-133">Vrácený objekt se bude podtřídou aktuálního objektu.</span><span class="sxs-lookup"><span data-stu-id="08cb9-133">The returned object becomes a subclass of the current object.</span></span>

<span data-ttu-id="08cb9-134">Nový objekt vrácený `ppNewClass` automaticky se stal podtřídou aktuálního objektu.</span><span class="sxs-lookup"><span data-stu-id="08cb9-134">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="08cb9-135">Toto chování nelze přepsat.</span><span class="sxs-lookup"><span data-stu-id="08cb9-135">This behavior cannot be overridden.</span></span> <span data-ttu-id="08cb9-136">Neexistuje žádná jiná metoda, pomocí které by bylo možné vytvořit podtřídy (odvozené třídy).</span><span class="sxs-lookup"><span data-stu-id="08cb9-136">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="08cb9-137">Požadavky</span><span class="sxs-lookup"><span data-stu-id="08cb9-137">Requirements</span></span>  
 <span data-ttu-id="08cb9-138">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08cb9-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08cb9-139">**Hlaviček** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="08cb9-139">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="08cb9-140">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="08cb9-140">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08cb9-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="08cb9-141">See also</span></span>

- [<span data-ttu-id="08cb9-142">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="08cb9-142">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
