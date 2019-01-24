---
title: Funkce SpawnInstance (referenční dokumentace nespravovaného rozhraní API)
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
ms.openlocfilehash: 74eb098ee68f57477c8b9115db2bce60919f0b12
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580210"
---
# <a name="spawninstance-function"></a><span data-ttu-id="12c74-103">SpawnInstance – funkce</span><span class="sxs-lookup"><span data-stu-id="12c74-103">SpawnInstance function</span></span>
<span data-ttu-id="12c74-104">Vytvoří novou instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="12c74-104">Creates a new instance of a class.</span></span>    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="12c74-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12c74-105">Syntax</span></span>  
  
```  
HRESULT SpawnInstance (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewInstance); 
```  

## <a name="parameters"></a><span data-ttu-id="12c74-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="12c74-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="12c74-107">[in] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="12c74-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="12c74-108">[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span><span class="sxs-lookup"><span data-stu-id="12c74-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="12c74-109">[in] Vyhrazená.</span><span class="sxs-lookup"><span data-stu-id="12c74-109">[in] Reserved.</span></span> <span data-ttu-id="12c74-110">Tento parametr musí být 0.</span><span class="sxs-lookup"><span data-stu-id="12c74-110">This parameter must be 0.</span></span>

`ppNewInstance`  
<span data-ttu-id="12c74-111">[out] Přijímá ukazatel na novou instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="12c74-111">[out] Receives the pointer to the new instance of the class.</span></span> <span data-ttu-id="12c74-112">Pokud dojde k chybě, není objekt vrácen, a `ppNewInstance` je bez jakýchkoli úprav vlevo.</span><span class="sxs-lookup"><span data-stu-id="12c74-112">If an error occurs, a new object is not returned, and `ppNewInstance` is left unmodified.</span></span>

## <a name="return-value"></a><span data-ttu-id="12c74-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="12c74-113">Return value</span></span>

<span data-ttu-id="12c74-114">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="12c74-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="12c74-115">Konstanta</span><span class="sxs-lookup"><span data-stu-id="12c74-115">Constant</span></span>  |<span data-ttu-id="12c74-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="12c74-116">Value</span></span>  |<span data-ttu-id="12c74-117">Popis</span><span class="sxs-lookup"><span data-stu-id="12c74-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="12c74-118">0x80041020</span><span class="sxs-lookup"><span data-stu-id="12c74-118">0x80041020</span></span> | <span data-ttu-id="12c74-119">`ptr` není platnou definicí třídy a nelze vytvořit podřízený nové instance.</span><span class="sxs-lookup"><span data-stu-id="12c74-119">`ptr` is not a valid class definition and cannot spawn new instances.</span></span> <span data-ttu-id="12c74-120">Je neúplný nebo nebyl zaregistrován pomocí Windows Management voláním [PutClassWmi](putclasswmi.md).</span><span class="sxs-lookup"><span data-stu-id="12c74-120">Either it is incomplete or it has not been registered with Windows Management by calling [PutClassWmi](putclasswmi.md).</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="12c74-121">0x80041006</span><span class="sxs-lookup"><span data-stu-id="12c74-121">0x80041006</span></span> | <span data-ttu-id="12c74-122">Nedostatek paměti je k dispozici k dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="12c74-122">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="12c74-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="12c74-123">0x80041008</span></span> | <span data-ttu-id="12c74-124">`ppNewClass` je `null`.</span><span class="sxs-lookup"><span data-stu-id="12c74-124">`ppNewClass` is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="12c74-125">0</span><span class="sxs-lookup"><span data-stu-id="12c74-125">0</span></span> | <span data-ttu-id="12c74-126">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="12c74-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="12c74-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="12c74-127">Remarks</span></span>

<span data-ttu-id="12c74-128">Tato funkce zalamuje volání na [IWbemClassObject::SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance) metody.</span><span class="sxs-lookup"><span data-stu-id="12c74-128">This function wraps a call to the [IWbemClassObject::SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance) method.</span></span>

<span data-ttu-id="12c74-129">`ptr` musí být definice třídy získat ze správy Windows.</span><span class="sxs-lookup"><span data-stu-id="12c74-129">`ptr` must be a class definition obtained from Windows Management.</span></span> <span data-ttu-id="12c74-130">(Všimněte si, že vytváření podřízeného procesu instanci z instance je podporováno, ale vrácená instance je prázdný). Pak použijete této definici třídy k vytvoření nové instance.</span><span class="sxs-lookup"><span data-stu-id="12c74-130">(Note that spawning an instance from an instance is supported but the returned instance is empty.) You then use this class definition to create new instances.</span></span> <span data-ttu-id="12c74-131">Volání [PutInstanceWmi](putinstancewmi.md) funkce je nutný, pokud máte v úmyslu instance zápisu ke správě Windows.</span><span class="sxs-lookup"><span data-stu-id="12c74-131">A call to the [PutInstanceWmi](putinstancewmi.md) function is required if you intend to write the instance to Windows Management.</span></span>




<span data-ttu-id="12c74-132">Nový objekt vrácený v `ppNewClass` automaticky stane podtřídu aktuálního objektu.</span><span class="sxs-lookup"><span data-stu-id="12c74-132">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="12c74-133">Toto chování nelze přepsat.</span><span class="sxs-lookup"><span data-stu-id="12c74-133">This behavior cannot be overridden.</span></span> <span data-ttu-id="12c74-134">Neexistuje žádná další metoda, podle kterého je možné vytvořit podtřídy (odvozené třídy).</span><span class="sxs-lookup"><span data-stu-id="12c74-134">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="12c74-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="12c74-135">Requirements</span></span>  
 <span data-ttu-id="12c74-136">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12c74-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12c74-137">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="12c74-137">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="12c74-138">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="12c74-138">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12c74-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="12c74-139">See also</span></span>
- [<span data-ttu-id="12c74-140">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="12c74-140">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
