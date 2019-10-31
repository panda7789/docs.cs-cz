---
title: WritePropertyValue – funkce (Reference nespravovaného rozhraní API)
description: Funkce WritePropertyValue zapisuje bajty na vlastnost.
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
ms.openlocfilehash: f02fb3877d55e9f47384b281573202712c29c606
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107292"
---
# <a name="writepropertyvalue-function"></a><span data-ttu-id="dd12d-103">WritePropertyValue – funkce</span><span class="sxs-lookup"><span data-stu-id="dd12d-103">WritePropertyValue function</span></span>
<span data-ttu-id="dd12d-104">Zapíše zadaný počet bajtů na vlastnost identifikovanou popisovačem vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="dd12d-104">Writes a specified number of bytes to a property identified by a property handle.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="dd12d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dd12d-105">Syntax</span></span>  
  
```cpp  
HRESULT WritePropertyValue (
   [in] int                  vFunc, 
   [in] IWbemObjectAccess*   ptr, 
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
); 
```  

## <a name="parameters"></a><span data-ttu-id="dd12d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="dd12d-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="dd12d-107">pro Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="dd12d-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="dd12d-108">pro Ukazatel na instanci [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) .</span><span class="sxs-lookup"><span data-stu-id="dd12d-108">[in] A pointer to an [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.</span></span>

`lHandle`  
<span data-ttu-id="dd12d-109">pro Celé číslo obsahující popisovač, který identifikuje tuto vlastnost.</span><span class="sxs-lookup"><span data-stu-id="dd12d-109">[in] An integer that contains the handle that identifies this property.</span></span> <span data-ttu-id="dd12d-110">Popisovač lze načíst voláním funkce [GetPropertyHandle](getpropertyhandle.md) .</span><span class="sxs-lookup"><span data-stu-id="dd12d-110">The handle can be retrieved by calling the [GetPropertyHandle](getpropertyhandle.md) function.</span></span>   

`lNumBytes`  
<span data-ttu-id="dd12d-111">pro Počet bajtů zapsaných do vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="dd12d-111">[in] The number of bytes being written to the property.</span></span> <span data-ttu-id="dd12d-112">Další informace najdete v části [poznámky](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="dd12d-112">See the [Remarks](#remarks) section for more information.</span></span>

`pHandle`   
<span data-ttu-id="dd12d-113">mimo Ukazatel na pole bajtů, které obsahuje data.</span><span class="sxs-lookup"><span data-stu-id="dd12d-113">[out] A pointer to the byte array that contains the data.</span></span>

## <a name="return-value"></a><span data-ttu-id="dd12d-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="dd12d-114">Return value</span></span>

<span data-ttu-id="dd12d-115">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="dd12d-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="dd12d-116">Konstanta</span><span class="sxs-lookup"><span data-stu-id="dd12d-116">Constant</span></span>  |<span data-ttu-id="dd12d-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="dd12d-117">Value</span></span>  |<span data-ttu-id="dd12d-118">Popis</span><span class="sxs-lookup"><span data-stu-id="dd12d-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="dd12d-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="dd12d-119">0x80041008</span></span> | <span data-ttu-id="dd12d-120">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="dd12d-120">A parameter is not valid.</span></span> |
|`WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="dd12d-121">0x80041005</span><span class="sxs-lookup"><span data-stu-id="dd12d-121">0x80041005</span></span> | <span data-ttu-id="dd12d-122">Došlo k neshodě typů.</span><span class="sxs-lookup"><span data-stu-id="dd12d-122">A type mismatch occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="dd12d-123">0,8</span><span class="sxs-lookup"><span data-stu-id="dd12d-123">0</span></span> | <span data-ttu-id="dd12d-124">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="dd12d-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="dd12d-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dd12d-125">Remarks</span></span>

<span data-ttu-id="dd12d-126">Tato funkce zalomí volání metody [IWbemclassObject:: WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) .</span><span class="sxs-lookup"><span data-stu-id="dd12d-126">This function wraps a call to the [IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) method.</span></span>

<span data-ttu-id="dd12d-127">Pomocí této funkce lze nastavit řetězec a všechna ostatní data, která nejsou`DWORD` nebo nejsou`QWORD`.</span><span class="sxs-lookup"><span data-stu-id="dd12d-127">Use this function to set string and all other non-`DWORD` or non-`QWORD` data.</span></span>

<span data-ttu-id="dd12d-128">Pro neřetězcové hodnoty vlastností musí být `lNumBytes` správná velikost dat zadaného typu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="dd12d-128">For nonstring property values, `lNumBytes` must be the correct data size of the property type specified.</span></span> <span data-ttu-id="dd12d-129">U hodnot řetězcových vlastností musí být `lNumBytes` délka zadaného řetězce v bajtech a samotný řetězec musí mít stejnou délku v bajtech a musí následovat po znaku pro ukončení hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="dd12d-129">For string property values, `lNumBytes` must be the length of the specified string in bytes, and the string itself must be of an even length in bytes and be followed with a null-termination character.</span></span>

## <a name="requirements"></a><span data-ttu-id="dd12d-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dd12d-130">Requirements</span></span>  
<span data-ttu-id="dd12d-131">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd12d-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd12d-132">**Hlavička:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="dd12d-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="dd12d-133">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="dd12d-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd12d-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dd12d-134">See also</span></span>

- [<span data-ttu-id="dd12d-135">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="dd12d-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
