---
title: Funkce WritePropertyValue (referenční dokumentace nespravovaného rozhraní API)
description: Funkce WritePropertyValue zapíše bajty do vlastnosti.
ms.date: 11/06/2017
api_name:
- WritePropertyValue
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- WritePropertyValue
helpviewer_keywords:
- WritePropertyValue function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 47120ff9de9e6e4802c5aea990841b235cd6c74c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783057"
---
# <a name="writepropertyvalue-function"></a><span data-ttu-id="50fb3-103">WritePropertyValue – funkce</span><span class="sxs-lookup"><span data-stu-id="50fb3-103">WritePropertyValue function</span></span>
<span data-ttu-id="50fb3-104">Zapíše zadaný počet bajtů na vlastnost identifikovaný popisovač vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="50fb3-104">Writes a specified number of bytes to a property identified by a property handle.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="50fb3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="50fb3-105">Syntax</span></span>  
  
```cpp  
HRESULT WritePropertyValue (
   [in] int                  vFunc, 
   [in] IWbemObjectAccess*   ptr, 
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
); 
```  

## <a name="parameters"></a><span data-ttu-id="50fb3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="50fb3-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="50fb3-107">[in] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="50fb3-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="50fb3-108">[in] Ukazatel [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.</span><span class="sxs-lookup"><span data-stu-id="50fb3-108">[in] A pointer to an [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.</span></span>

`lHandle`  
<span data-ttu-id="50fb3-109">[in] Celé číslo, které obsahuje popisovač identifikující tuto vlastnost.</span><span class="sxs-lookup"><span data-stu-id="50fb3-109">[in] An integer that contains the handle that identifies this property.</span></span> <span data-ttu-id="50fb3-110">Popisovač může být načten voláním [GetPropertyHandle](getpropertyhandle.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="50fb3-110">The handle can be retrieved by calling the [GetPropertyHandle](getpropertyhandle.md) function.</span></span>   

`lNumBytes`  
<span data-ttu-id="50fb3-111">[in] Počet bajtů, které probíhá zápis do vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="50fb3-111">[in] The number of bytes being written to the property.</span></span> <span data-ttu-id="50fb3-112">Zobrazit [poznámky](#remarks) části Další informace.</span><span class="sxs-lookup"><span data-stu-id="50fb3-112">See the [Remarks](#remarks) section for more information.</span></span>

`pHandle`   
<span data-ttu-id="50fb3-113">[out] Ukazatel na pole bajtů obsahující data.</span><span class="sxs-lookup"><span data-stu-id="50fb3-113">[out] A pointer to the byte array that contains the data.</span></span>

## <a name="return-value"></a><span data-ttu-id="50fb3-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="50fb3-114">Return value</span></span>

<span data-ttu-id="50fb3-115">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="50fb3-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="50fb3-116">Konstanta</span><span class="sxs-lookup"><span data-stu-id="50fb3-116">Constant</span></span>  |<span data-ttu-id="50fb3-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="50fb3-117">Value</span></span>  |<span data-ttu-id="50fb3-118">Popis</span><span class="sxs-lookup"><span data-stu-id="50fb3-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="50fb3-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="50fb3-119">0x80041008</span></span> | <span data-ttu-id="50fb3-120">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="50fb3-120">A parameter is not valid.</span></span> |
|`WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="50fb3-121">0x80041005</span><span class="sxs-lookup"><span data-stu-id="50fb3-121">0x80041005</span></span> | <span data-ttu-id="50fb3-122">Došlo k neshodě typů.</span><span class="sxs-lookup"><span data-stu-id="50fb3-122">A type mismatch occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="50fb3-123">0</span><span class="sxs-lookup"><span data-stu-id="50fb3-123">0</span></span> | <span data-ttu-id="50fb3-124">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="50fb3-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="50fb3-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="50fb3-125">Remarks</span></span>

<span data-ttu-id="50fb3-126">Tato funkce zalamuje volání na [IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) metody.</span><span class="sxs-lookup"><span data-stu-id="50fb3-126">This function wraps a call to the [IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) method.</span></span>

<span data-ttu-id="50fb3-127">Pomocí této funkce můžete nastavit řetězec a všechny ostatní jinou hodnotu než`DWORD` nebo jiných-`QWORD` data.</span><span class="sxs-lookup"><span data-stu-id="50fb3-127">Use this function to set string and all other non-`DWORD` or non-`QWORD` data.</span></span>

<span data-ttu-id="50fb3-128">Neřetězcový hodnoty vlastností `lNumBytes` musí mít velikost správného datového typu vlastnosti zadané.</span><span class="sxs-lookup"><span data-stu-id="50fb3-128">For nonstring property values, `lNumBytes` must be the correct data size of the property type specified.</span></span> <span data-ttu-id="50fb3-129">Pro řetězce hodnoty vlastnosti `lNumBytes` musí mít délku zadaného řetězce v bajtech a řetězce samostatně musí být i délka v bajtech a být následován znakem ukončení hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="50fb3-129">For string property values, `lNumBytes` must be the length of the specified string in bytes, and the string itself must be of an even length in bytes and be followed with a null-termination character.</span></span>

## <a name="requirements"></a><span data-ttu-id="50fb3-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="50fb3-130">Requirements</span></span>  
<span data-ttu-id="50fb3-131">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50fb3-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50fb3-132">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="50fb3-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="50fb3-133">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="50fb3-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50fb3-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="50fb3-134">See also</span></span>

- [<span data-ttu-id="50fb3-135">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="50fb3-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
