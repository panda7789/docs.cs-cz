---
title: Funkce CloneEnumWbemClassObject (referenční dokumentace nespravovaného rozhraní API)
description: Funkce CloneEnumWbemClassObject vytvoří kopii logické enumerátor.
ms.date: 11/06/2017
api_name:
- CloneEnumWbemClassObject
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CloneEnumWbemClassObject
helpviewer_keywords:
- CloneEnumWbemClassObject function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 52edc72e3714ceaf8cc92f272da6a374eb324dad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54661643"
---
# <a name="cloneenumwbemclassobject-function"></a><span data-ttu-id="401b7-103">Funkce CloneEnumWbemClassObject</span><span class="sxs-lookup"><span data-stu-id="401b7-103">CloneEnumWbemClassObject function</span></span>
<span data-ttu-id="401b7-104">Vytvoří kopii logické tohoto čítače, zachovat své aktuální pozici ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="401b7-104">Makes a logical copy of an enumerator, retaining its current position in an enumeration.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="401b7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="401b7-105">Syntax</span></span>  
  
```  
HRESULT CloneEnumWbemClassObject (
   [out] IEnumWbemClassObject**  ppEnum, 
   [in] DWORD                    authLevel,
   [in] DWORD                    impLevel,
   [in] IEnumWbemClassObject*    pCurrentEnumWbemClassObject, 
   [in] BSTR                     strUser,
   [in] BSTR                     strPassword,
   [in BSTR]                     strAuthority 
); 
```  

## <a name="parameters"></a><span data-ttu-id="401b7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="401b7-106">Parameters</span></span>

`ppEnum`  
<span data-ttu-id="401b7-107">[out] Přijímá ukazatel na novou [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject).</span><span class="sxs-lookup"><span data-stu-id="401b7-107">[out] Receives a pointer to a new [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject).</span></span>

`authLevel`  
<span data-ttu-id="401b7-108">[in] Úroveň autorizace.</span><span class="sxs-lookup"><span data-stu-id="401b7-108">[in] The authorization level.</span></span>

<span data-ttu-id="401b7-109">`impLevel` [in] Úroveň zosobnění.</span><span class="sxs-lookup"><span data-stu-id="401b7-109">`impLevel` [in] The impersonation level.</span></span>

`pCurrentEnumWbemClassObject`  
<span data-ttu-id="401b7-110">[out] Ukazatel [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) instance ke klonování.</span><span class="sxs-lookup"><span data-stu-id="401b7-110">[out] A pointer to the [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) instance to be cloned.</span></span>

`strUser`   
<span data-ttu-id="401b7-111">[in] Uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="401b7-111">[in] The user name.</span></span> <span data-ttu-id="401b7-112">Zobrazit [ConnectServerWmi](connectserverwmi.md) funkce pro další informace.</span><span class="sxs-lookup"><span data-stu-id="401b7-112">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`   
<span data-ttu-id="401b7-113">[in] Heslo.</span><span class="sxs-lookup"><span data-stu-id="401b7-113">[in] The password.</span></span> <span data-ttu-id="401b7-114">Zobrazit [ConnectServerWmi](connectserverwmi.md) funkce pro další informace.</span><span class="sxs-lookup"><span data-stu-id="401b7-114">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`   
<span data-ttu-id="401b7-115">[in] Název domény uživatele.</span><span class="sxs-lookup"><span data-stu-id="401b7-115">[in] The domain name of the user.</span></span> <span data-ttu-id="401b7-116">Zobrazit [ConnectServerWmi](connectserverwmi.md) funkce pro další informace.</span><span class="sxs-lookup"><span data-stu-id="401b7-116">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="401b7-117">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="401b7-117">Return value</span></span>

<span data-ttu-id="401b7-118">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="401b7-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="401b7-119">Konstanta</span><span class="sxs-lookup"><span data-stu-id="401b7-119">Constant</span></span>  |<span data-ttu-id="401b7-120">Hodnota</span><span class="sxs-lookup"><span data-stu-id="401b7-120">Value</span></span>  |<span data-ttu-id="401b7-121">Popis</span><span class="sxs-lookup"><span data-stu-id="401b7-121">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="401b7-122">0x80041001</span><span class="sxs-lookup"><span data-stu-id="401b7-122">0x80041001</span></span> | <span data-ttu-id="401b7-123">Obecné selhání došlo.</span><span class="sxs-lookup"><span data-stu-id="401b7-123">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="401b7-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="401b7-124">0x80041008</span></span> | <span data-ttu-id="401b7-125">Parametr je neplatný.</span><span class="sxs-lookup"><span data-stu-id="401b7-125">A parameter is invalid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="401b7-126">0x80041006</span><span class="sxs-lookup"><span data-stu-id="401b7-126">0x80041006</span></span> | <span data-ttu-id="401b7-127">Není k dispozici není dostatek paměti dokončit operaci.</span><span class="sxs-lookup"><span data-stu-id="401b7-127">Not enough memory is available complete the operation.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="401b7-128">0x80041015</span><span class="sxs-lookup"><span data-stu-id="401b7-128">0x80041015</span></span> | <span data-ttu-id="401b7-129">Odkaz vzdálené volání (procedur RPC) mezi aktuálním procesem a službou WMI se nezdařil.</span><span class="sxs-lookup"><span data-stu-id="401b7-129">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="401b7-130">0</span><span class="sxs-lookup"><span data-stu-id="401b7-130">0</span></span> | <span data-ttu-id="401b7-131">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="401b7-131">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="401b7-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="401b7-132">Remarks</span></span>

<span data-ttu-id="401b7-133">Tato funkce zalamuje volání na [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) metody.</span><span class="sxs-lookup"><span data-stu-id="401b7-133">This function wraps a call to the [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) method.</span></span>

<span data-ttu-id="401b7-134">Tato metoda provádí pouze kopie "co možná nejlepší".</span><span class="sxs-lookup"><span data-stu-id="401b7-134">This method makes only a "best effort" copy.</span></span> <span data-ttu-id="401b7-135">Vzhledem k dynamické povaze velký počet objektů CIM je možné, že nový čítač není výčet stejnou sadu objektů jako enumerátoru zdroje.</span><span class="sxs-lookup"><span data-stu-id="401b7-135">Due to the dynamic nature of many CIM objects, it is possible that the new enumerator does not enumerate the same set of objects as the source enumerator.</span></span>  

<span data-ttu-id="401b7-136">Pokud selže volání funkce, můžete získat další informace o chybě při volání [GetErrorInfo –](geterrorinfo.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="401b7-136">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="example"></a><span data-ttu-id="401b7-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="401b7-137">Example</span></span>

<span data-ttu-id="401b7-138">Příklad najdete v tématu [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) metody.</span><span class="sxs-lookup"><span data-stu-id="401b7-138">For an example, see the [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="401b7-139">Požadavky</span><span class="sxs-lookup"><span data-stu-id="401b7-139">Requirements</span></span>  
 <span data-ttu-id="401b7-140">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="401b7-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="401b7-141">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="401b7-141">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="401b7-142">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="401b7-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="401b7-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="401b7-143">See also</span></span>
- [<span data-ttu-id="401b7-144">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="401b7-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
