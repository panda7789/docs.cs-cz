---
title: SpawnInstance – funkce (Reference nespravovaného rozhraní API)
description: Funkce SpawnInstance vytvoří novou instanci třídy.
ms.date: 11/06/2017
api_name:
- SpawnInstance
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnInstance
helpviewer_keywords:
- SpawnInstance function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 529905bd9286520a8e09479bfc95ef0b614f53e9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798216"
---
# <a name="spawninstance-function"></a><span data-ttu-id="45612-103">SpawnInstance – funkce</span><span class="sxs-lookup"><span data-stu-id="45612-103">SpawnInstance function</span></span>
<span data-ttu-id="45612-104">Vytvoří novou instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="45612-104">Creates a new instance of a class.</span></span>    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="45612-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45612-105">Syntax</span></span>  
  
```cpp  
HRESULT SpawnInstance (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewInstance); 
```  

## <a name="parameters"></a><span data-ttu-id="45612-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="45612-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="45612-107">pro Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="45612-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="45612-108">pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="45612-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="45612-109">pro Rezervovaný.</span><span class="sxs-lookup"><span data-stu-id="45612-109">[in] Reserved.</span></span> <span data-ttu-id="45612-110">Tento parametr musí mít hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="45612-110">This parameter must be 0.</span></span>

`ppNewInstance`  
<span data-ttu-id="45612-111">mimo Přijme ukazatel na novou instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="45612-111">[out] Receives the pointer to the new instance of the class.</span></span> <span data-ttu-id="45612-112">Pokud dojde k chybě, nový objekt se nevrátí a `ppNewInstance` zůstane beze změny.</span><span class="sxs-lookup"><span data-stu-id="45612-112">If an error occurs, a new object is not returned, and `ppNewInstance` is left unmodified.</span></span>

## <a name="return-value"></a><span data-ttu-id="45612-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="45612-113">Return value</span></span>

<span data-ttu-id="45612-114">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="45612-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="45612-115">Konstanta</span><span class="sxs-lookup"><span data-stu-id="45612-115">Constant</span></span>  |<span data-ttu-id="45612-116">Value</span><span class="sxs-lookup"><span data-stu-id="45612-116">Value</span></span>  |<span data-ttu-id="45612-117">Popis</span><span class="sxs-lookup"><span data-stu-id="45612-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="45612-118">0x80041020</span><span class="sxs-lookup"><span data-stu-id="45612-118">0x80041020</span></span> | <span data-ttu-id="45612-119">`ptr`není platnou definicí třídy a nemůže vytvořit nové instance.</span><span class="sxs-lookup"><span data-stu-id="45612-119">`ptr` is not a valid class definition and cannot spawn new instances.</span></span> <span data-ttu-id="45612-120">Buď je neúplný, nebo nebyl zaregistrován u správy systému Windows voláním [PutClassWmi](putclasswmi.md).</span><span class="sxs-lookup"><span data-stu-id="45612-120">Either it is incomplete or it has not been registered with Windows Management by calling [PutClassWmi](putclasswmi.md).</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="45612-121">0x80041006</span><span class="sxs-lookup"><span data-stu-id="45612-121">0x80041006</span></span> | <span data-ttu-id="45612-122">K dokončení této operace není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="45612-122">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="45612-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="45612-123">0x80041008</span></span> | <span data-ttu-id="45612-124">`ppNewClass`je `null`.</span><span class="sxs-lookup"><span data-stu-id="45612-124">`ppNewClass` is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="45612-125">0</span><span class="sxs-lookup"><span data-stu-id="45612-125">0</span></span> | <span data-ttu-id="45612-126">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="45612-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="45612-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="45612-127">Remarks</span></span>

<span data-ttu-id="45612-128">Tato funkce zalomí volání metody [IWbemclassObject:: SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance) .</span><span class="sxs-lookup"><span data-stu-id="45612-128">This function wraps a call to the [IWbemClassObject::SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance) method.</span></span>

<span data-ttu-id="45612-129">`ptr`musí se jednat o definici třídy získanou ze správy systému Windows.</span><span class="sxs-lookup"><span data-stu-id="45612-129">`ptr` must be a class definition obtained from Windows Management.</span></span> <span data-ttu-id="45612-130">(Všimněte si, že vytvoření instance z instance je podporováno, ale vrácená instance je prázdná.) Tuto definici třídy pak můžete použít k vytvoření nových instancí.</span><span class="sxs-lookup"><span data-stu-id="45612-130">(Note that spawning an instance from an instance is supported but the returned instance is empty.) You then use this class definition to create new instances.</span></span> <span data-ttu-id="45612-131">Pokud máte v úmyslu zapsat instanci do správy systému Windows, je třeba zadat volání funkce [PutInstanceWmi](putinstancewmi.md) .</span><span class="sxs-lookup"><span data-stu-id="45612-131">A call to the [PutInstanceWmi](putinstancewmi.md) function is required if you intend to write the instance to Windows Management.</span></span>

<span data-ttu-id="45612-132">Nový objekt vrácený `ppNewClass` automaticky se stal podtřídou aktuálního objektu.</span><span class="sxs-lookup"><span data-stu-id="45612-132">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="45612-133">Toto chování nelze přepsat.</span><span class="sxs-lookup"><span data-stu-id="45612-133">This behavior cannot be overridden.</span></span> <span data-ttu-id="45612-134">Neexistuje žádná jiná metoda, pomocí které by bylo možné vytvořit podtřídy (odvozené třídy).</span><span class="sxs-lookup"><span data-stu-id="45612-134">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="45612-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="45612-135">Requirements</span></span>  
 <span data-ttu-id="45612-136">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45612-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45612-137">**Hlaviček** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="45612-137">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="45612-138">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="45612-138">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45612-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="45612-139">See also</span></span>

- [<span data-ttu-id="45612-140">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="45612-140">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
