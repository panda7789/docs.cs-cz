---
title: Funkce BeginMethodEnumeration (referenční dokumentace nespravovaného rozhraní API)
description: Funkce BeginMethodEnumeration začíná výčet metod objektu
ms.date: 11/06/2017
api_name:
- BeginMethodEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BeginMethodEnumeration
helpviewer_keywords:
- BeginMethodEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d6de2a5ff4d2743c7aca2e46b3af848138c15fb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59158779"
---
# <a name="beginenumeration-function"></a><span data-ttu-id="75adb-103">Funkce BeginEnumeration</span><span class="sxs-lookup"><span data-stu-id="75adb-103">BeginEnumeration function</span></span>
<span data-ttu-id="75adb-104">Začíná výčet dostupné metody pro objekt.</span><span class="sxs-lookup"><span data-stu-id="75adb-104">Begins an enumeration of the methods available for the object.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="75adb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="75adb-105">Syntax</span></span>  
  
``` 
HRESULT BeginMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="75adb-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="75adb-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="75adb-107">[in] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="75adb-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="75adb-108">[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span><span class="sxs-lookup"><span data-stu-id="75adb-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lEnumFlags`  
<span data-ttu-id="75adb-109">[in] Nula (0) pro všechny metody nebo příznak, který určuje rozsah výčtu.</span><span class="sxs-lookup"><span data-stu-id="75adb-109">[in] Zero (0) for all methods, or a flag that specifies the scope of the enumeration.</span></span> <span data-ttu-id="75adb-110">Následující příznaky jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="75adb-110">The following flags are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

<span data-ttu-id="75adb-111">Konstanta</span><span class="sxs-lookup"><span data-stu-id="75adb-111">Constant</span></span>  |<span data-ttu-id="75adb-112">Hodnota</span><span class="sxs-lookup"><span data-stu-id="75adb-112">Value</span></span>  |<span data-ttu-id="75adb-113">Popis</span><span class="sxs-lookup"><span data-stu-id="75adb-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="75adb-114">0x10</span><span class="sxs-lookup"><span data-stu-id="75adb-114">0x10</span></span> | <span data-ttu-id="75adb-115">Omezte výčet metodám, které jsou definovány v samotné třídě.</span><span class="sxs-lookup"><span data-stu-id="75adb-115">Limit the enumeration to methods that are defined in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="75adb-116">0x20</span><span class="sxs-lookup"><span data-stu-id="75adb-116">0x20</span></span> | <span data-ttu-id="75adb-117">Omezte výčet vlastností, které se dědí ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="75adb-117">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="return-value"></a><span data-ttu-id="75adb-118">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="75adb-118">Return value</span></span>

<span data-ttu-id="75adb-119">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="75adb-119">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="75adb-120">Konstanta</span><span class="sxs-lookup"><span data-stu-id="75adb-120">Constant</span></span>  |<span data-ttu-id="75adb-121">Value</span><span class="sxs-lookup"><span data-stu-id="75adb-121">Value</span></span>  |<span data-ttu-id="75adb-122">Popis</span><span class="sxs-lookup"><span data-stu-id="75adb-122">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="75adb-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="75adb-123">0x80041008</span></span> | <span data-ttu-id="75adb-124">`lEnnumFlags` je nenulová a není součástí zadané příznaky.</span><span class="sxs-lookup"><span data-stu-id="75adb-124">`lEnnumFlags` is non-zero and is not one of the specified flags.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="75adb-125">0</span><span class="sxs-lookup"><span data-stu-id="75adb-125">0</span></span> | <span data-ttu-id="75adb-126">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="75adb-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="75adb-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="75adb-127">Remarks</span></span>

<span data-ttu-id="75adb-128">Tato funkce zalamuje volání na [IWbemClassObject::BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration) metody.</span><span class="sxs-lookup"><span data-stu-id="75adb-128">This function wraps a call to the [IWbemClassObject::BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration) method.</span></span>

<span data-ttu-id="75adb-129">Volání této metody je podporována pouze, pokud se aktuální objekt definice třídy.</span><span class="sxs-lookup"><span data-stu-id="75adb-129">This method call is only supported if the current object is a class definition.</span></span> <span data-ttu-id="75adb-130">Zpracování metody není k dispozici [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) ukazatele, které odkazují na instance.</span><span class="sxs-lookup"><span data-stu-id="75adb-130">Method manipulation is not available from [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to instances.</span></span> <span data-ttu-id="75adb-131">Pořadí, ve kterém jsou uvedené metody je zaručeno, že bude neutrální pro danou instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject).</span><span class="sxs-lookup"><span data-stu-id="75adb-131">The order in which methods are enumerated is guaranteed to be invariant for a given instance of [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject).</span></span>

## <a name="requirements"></a><span data-ttu-id="75adb-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="75adb-132">Requirements</span></span>  
 <span data-ttu-id="75adb-133">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75adb-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75adb-134">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="75adb-134">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="75adb-135">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="75adb-135">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75adb-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="75adb-136">See also</span></span>

- [<span data-ttu-id="75adb-137">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="75adb-137">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
