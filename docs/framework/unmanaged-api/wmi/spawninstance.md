---
title: Funkce SpawnInstance (Nespravovaný odkaz na rozhraní API)
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
ms.openlocfilehash: a15eb8123c1ee807444bdb4c6fe71cdccc08f434
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176718"
---
# <a name="spawninstance-function"></a><span data-ttu-id="5e7e8-103">SpawnInstance</span><span class="sxs-lookup"><span data-stu-id="5e7e8-103">SpawnInstance function</span></span>
<span data-ttu-id="5e7e8-104">Vytvoří novou instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="5e7e8-104">Creates a new instance of a class.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="5e7e8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5e7e8-105">Syntax</span></span>  
  
```cpp  
HRESULT SpawnInstance (
   [in] int                  vFunc,
   [in] IWbemClassObject*    ptr,
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewInstance);
```  

## <a name="parameters"></a><span data-ttu-id="5e7e8-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5e7e8-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="5e7e8-107">[v] Tento parametr není použit.</span><span class="sxs-lookup"><span data-stu-id="5e7e8-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="5e7e8-108">[v] Ukazatel na instanci [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="5e7e8-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="5e7e8-109">[v] Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="5e7e8-109">[in] Reserved.</span></span> <span data-ttu-id="5e7e8-110">Tento parametr musí být 0.</span><span class="sxs-lookup"><span data-stu-id="5e7e8-110">This parameter must be 0.</span></span>

`ppNewInstance`  
<span data-ttu-id="5e7e8-111">[out] Obdrží ukazatel na novou instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="5e7e8-111">[out] Receives the pointer to the new instance of the class.</span></span> <span data-ttu-id="5e7e8-112">Pokud dojde k chybě, nový objekt není `ppNewInstance` vrácena a je ponechána beze změny.</span><span class="sxs-lookup"><span data-stu-id="5e7e8-112">If an error occurs, a new object is not returned, and `ppNewInstance` is left unmodified.</span></span>

## <a name="return-value"></a><span data-ttu-id="5e7e8-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5e7e8-113">Return value</span></span>

<span data-ttu-id="5e7e8-114">Následující hodnoty vrácené touto funkcí jsou definovány v souboru *hlavičky WbemCli.h,* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="5e7e8-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="5e7e8-115">Trvalé</span><span class="sxs-lookup"><span data-stu-id="5e7e8-115">Constant</span></span>  |<span data-ttu-id="5e7e8-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5e7e8-116">Value</span></span>  |<span data-ttu-id="5e7e8-117">Popis</span><span class="sxs-lookup"><span data-stu-id="5e7e8-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="5e7e8-118">0x80041020</span><span class="sxs-lookup"><span data-stu-id="5e7e8-118">0x80041020</span></span> | <span data-ttu-id="5e7e8-119">`ptr`není platnou definicí třídy a nemůže vytvořit nové instance.</span><span class="sxs-lookup"><span data-stu-id="5e7e8-119">`ptr` is not a valid class definition and cannot spawn new instances.</span></span> <span data-ttu-id="5e7e8-120">Buď je neúplný, nebo nebyl aregistrován pomocí správy systému Windows voláním [PutClassWmi](putclasswmi.md).</span><span class="sxs-lookup"><span data-stu-id="5e7e8-120">Either it is incomplete or it has not been registered with Windows Management by calling [PutClassWmi](putclasswmi.md).</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="5e7e8-121">0x80041006</span><span class="sxs-lookup"><span data-stu-id="5e7e8-121">0x80041006</span></span> | <span data-ttu-id="5e7e8-122">K dokončení operace není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="5e7e8-122">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="5e7e8-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="5e7e8-123">0x80041008</span></span> | <span data-ttu-id="5e7e8-124">`ppNewClass` je `null`.</span><span class="sxs-lookup"><span data-stu-id="5e7e8-124">`ppNewClass` is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="5e7e8-125">0</span><span class="sxs-lookup"><span data-stu-id="5e7e8-125">0</span></span> | <span data-ttu-id="5e7e8-126">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="5e7e8-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="5e7e8-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5e7e8-127">Remarks</span></span>

<span data-ttu-id="5e7e8-128">Tato funkce zabalí volání metody [IWbemClassObject::SpawnInstance.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance)</span><span class="sxs-lookup"><span data-stu-id="5e7e8-128">This function wraps a call to the [IWbemClassObject::SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance) method.</span></span>

<span data-ttu-id="5e7e8-129">`ptr`musí být definice třídy získaná ze správy systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5e7e8-129">`ptr` must be a class definition obtained from Windows Management.</span></span> <span data-ttu-id="5e7e8-130">(Všimněte si, že tření instance z instance je podporována, ale vrácená instance je prázdná.) Potom použijete tuto definici třídy k vytvoření nových instancí.</span><span class="sxs-lookup"><span data-stu-id="5e7e8-130">(Note that spawning an instance from an instance is supported but the returned instance is empty.) You then use this class definition to create new instances.</span></span> <span data-ttu-id="5e7e8-131">Volání funkce [PutInstanceWmi](putinstancewmi.md) je vyžadováno, pokud máte v úmyslu zapsat instanci do správy systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5e7e8-131">A call to the [PutInstanceWmi](putinstancewmi.md) function is required if you intend to write the instance to Windows Management.</span></span>

<span data-ttu-id="5e7e8-132">Nový objekt vrácený automaticky `ppNewClass` se stane podtřídou aktuálního objektu.</span><span class="sxs-lookup"><span data-stu-id="5e7e8-132">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="5e7e8-133">Toto chování nelze přepsat.</span><span class="sxs-lookup"><span data-stu-id="5e7e8-133">This behavior cannot be overridden.</span></span> <span data-ttu-id="5e7e8-134">Neexistuje žádná jiná metoda, kterou lze vytvořit podtřídy (odvozené třídy).</span><span class="sxs-lookup"><span data-stu-id="5e7e8-134">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="5e7e8-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5e7e8-135">Requirements</span></span>  
 <span data-ttu-id="5e7e8-136">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e7e8-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e7e8-137">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="5e7e8-137">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="5e7e8-138">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5e7e8-138">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e7e8-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="5e7e8-139">See also</span></span>

- [<span data-ttu-id="5e7e8-140">Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="5e7e8-140">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
