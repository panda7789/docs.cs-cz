---
title: WritePropertyValue function (Unmanaged API Reference)
description: Funkce WritePropertyValue zapisuje bajty do vlastnosti.
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
ms.openlocfilehash: 4a950beef2e9bf8c0230d6a38008d75f89373410
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174833"
---
# <a name="writepropertyvalue-function"></a><span data-ttu-id="3ecb6-103">WritePropertyValue</span><span class="sxs-lookup"><span data-stu-id="3ecb6-103">WritePropertyValue function</span></span>
<span data-ttu-id="3ecb6-104">Zapíše zadaný počet bajtů do vlastnosti identifikované popisovačem vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3ecb6-104">Writes a specified number of bytes to a property identified by a property handle.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="3ecb6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ecb6-105">Syntax</span></span>  
  
```cpp  
HRESULT WritePropertyValue (
   [in] int                  vFunc,
   [in] IWbemObjectAccess*   ptr,
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
);
```  

## <a name="parameters"></a><span data-ttu-id="3ecb6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3ecb6-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="3ecb6-107">[v] Tento parametr není použit.</span><span class="sxs-lookup"><span data-stu-id="3ecb6-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="3ecb6-108">[v] Ukazatel na instanci [IWbemObjectAccess.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess)</span><span class="sxs-lookup"><span data-stu-id="3ecb6-108">[in] A pointer to an [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.</span></span>

`lHandle`  
<span data-ttu-id="3ecb6-109">[v] Celé číslo, které obsahuje popisovač, který identifikuje tuto vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3ecb6-109">[in] An integer that contains the handle that identifies this property.</span></span> <span data-ttu-id="3ecb6-110">Popisovač lze načíst voláním funkce [GetPropertyHandle.](getpropertyhandle.md)</span><span class="sxs-lookup"><span data-stu-id="3ecb6-110">The handle can be retrieved by calling the [GetPropertyHandle](getpropertyhandle.md) function.</span></span>

`lNumBytes`  
<span data-ttu-id="3ecb6-111">[v] Počet bajtů zapisováno do vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3ecb6-111">[in] The number of bytes being written to the property.</span></span> <span data-ttu-id="3ecb6-112">Další informace naleznete v části [Poznámky.](#remarks)</span><span class="sxs-lookup"><span data-stu-id="3ecb6-112">See the [Remarks](#remarks) section for more information.</span></span>

<span data-ttu-id="3ecb6-113">`pHandle`[out] Ukazatel na bajtové pole, které obsahuje data.</span><span class="sxs-lookup"><span data-stu-id="3ecb6-113">`pHandle` [out] A pointer to the byte array that contains the data.</span></span>

## <a name="return-value"></a><span data-ttu-id="3ecb6-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3ecb6-114">Return value</span></span>

<span data-ttu-id="3ecb6-115">Následující hodnoty vrácené touto funkcí jsou definovány v souboru *hlavičky WbemCli.h,* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="3ecb6-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="3ecb6-116">Trvalé</span><span class="sxs-lookup"><span data-stu-id="3ecb6-116">Constant</span></span>  |<span data-ttu-id="3ecb6-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="3ecb6-117">Value</span></span>  |<span data-ttu-id="3ecb6-118">Popis</span><span class="sxs-lookup"><span data-stu-id="3ecb6-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="3ecb6-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="3ecb6-119">0x80041008</span></span> | <span data-ttu-id="3ecb6-120">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="3ecb6-120">A parameter is not valid.</span></span> |
|`WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="3ecb6-121">0x80041005</span><span class="sxs-lookup"><span data-stu-id="3ecb6-121">0x80041005</span></span> | <span data-ttu-id="3ecb6-122">Došlo k neshodě typů.</span><span class="sxs-lookup"><span data-stu-id="3ecb6-122">A type mismatch occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="3ecb6-123">0</span><span class="sxs-lookup"><span data-stu-id="3ecb6-123">0</span></span> | <span data-ttu-id="3ecb6-124">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="3ecb6-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="3ecb6-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3ecb6-125">Remarks</span></span>

<span data-ttu-id="3ecb6-126">Tato funkce zabalí volání metody [IWbemClassObject::WritePropertyValue.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue)</span><span class="sxs-lookup"><span data-stu-id="3ecb6-126">This function wraps a call to the [IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) method.</span></span>

<span data-ttu-id="3ecb6-127">Tato funkce slouží k nastavení řetězce`DWORD` a`QWORD` všech ostatních nedat.</span><span class="sxs-lookup"><span data-stu-id="3ecb6-127">Use this function to set string and all other non-`DWORD` or non-`QWORD` data.</span></span>

<span data-ttu-id="3ecb6-128">Pro hodnoty vlastností `lNumBytes` nonstring musí být správná velikost dat zadaného typu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3ecb6-128">For nonstring property values, `lNumBytes` must be the correct data size of the property type specified.</span></span> <span data-ttu-id="3ecb6-129">Pro hodnoty vlastností řetězce `lNumBytes` musí být délka zadaného řetězce v bajtů a samotný řetězec musí mít rovnou délku v bajtů a musí být následován znakem null-termination.</span><span class="sxs-lookup"><span data-stu-id="3ecb6-129">For string property values, `lNumBytes` must be the length of the specified string in bytes, and the string itself must be of an even length in bytes and be followed with a null-termination character.</span></span>

## <a name="requirements"></a><span data-ttu-id="3ecb6-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3ecb6-130">Requirements</span></span>  
<span data-ttu-id="3ecb6-131">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ecb6-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ecb6-132">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="3ecb6-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="3ecb6-133">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3ecb6-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ecb6-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="3ecb6-134">See also</span></span>

- [<span data-ttu-id="3ecb6-135">Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="3ecb6-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
