---
title: CloneEnumWbemClassObject (Nespravovaný odkaz na rozhraní API)
description: CloneEnumWbemClassObject funkce vytvoří logickou kopii čítače výčtu.
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
ms.openlocfilehash: f2a3a7e848108e50c04f0ec70cf42586755a0a88
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175015"
---
# <a name="cloneenumwbemclassobject-function"></a><span data-ttu-id="402ef-103">Funkce CloneEnumWbemClassObject</span><span class="sxs-lookup"><span data-stu-id="402ef-103">CloneEnumWbemClassObject function</span></span>
<span data-ttu-id="402ef-104">Vytvoří logickou kopii čítače výčtu, zachování jeho aktuální pozici ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="402ef-104">Makes a logical copy of an enumerator, retaining its current position in an enumeration.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="402ef-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="402ef-105">Syntax</span></span>

```cpp
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

## <a name="parameters"></a><span data-ttu-id="402ef-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="402ef-106">Parameters</span></span>

`ppEnum`\
<span data-ttu-id="402ef-107">[out] Obdrží ukazatel na nový [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject).</span><span class="sxs-lookup"><span data-stu-id="402ef-107">[out] Receives a pointer to a new [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject).</span></span>

`authLevel`\
<span data-ttu-id="402ef-108">[v] Úroveň autorizace.</span><span class="sxs-lookup"><span data-stu-id="402ef-108">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="402ef-109">[v] Úroveň zosobnění.</span><span class="sxs-lookup"><span data-stu-id="402ef-109">[in] The impersonation level.</span></span>

`pCurrentEnumWbemClassObject`\
<span data-ttu-id="402ef-110">[out] Ukazatel na instanci [IEnumWbemClassObject,](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) která má být klonována.</span><span class="sxs-lookup"><span data-stu-id="402ef-110">[out] A pointer to the [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) instance to be cloned.</span></span>

`strUser`\
<span data-ttu-id="402ef-111">[v] Uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="402ef-111">[in] The user name.</span></span> <span data-ttu-id="402ef-112">Další informace naleznete ve funkci [ConnectServerWmi.](connectserverwmi.md)</span><span class="sxs-lookup"><span data-stu-id="402ef-112">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="402ef-113">[v] Heslo.</span><span class="sxs-lookup"><span data-stu-id="402ef-113">[in] The password.</span></span> <span data-ttu-id="402ef-114">Další informace naleznete ve funkci [ConnectServerWmi.](connectserverwmi.md)</span><span class="sxs-lookup"><span data-stu-id="402ef-114">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="402ef-115">[v] Název domény uživatele.</span><span class="sxs-lookup"><span data-stu-id="402ef-115">[in] The domain name of the user.</span></span> <span data-ttu-id="402ef-116">Další informace naleznete ve funkci [ConnectServerWmi.](connectserverwmi.md)</span><span class="sxs-lookup"><span data-stu-id="402ef-116">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="402ef-117">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="402ef-117">Return value</span></span>

<span data-ttu-id="402ef-118">Následující hodnoty vrácené touto funkcí jsou definovány v souboru *hlavičky WbemCli.h,* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="402ef-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="402ef-119">Trvalé</span><span class="sxs-lookup"><span data-stu-id="402ef-119">Constant</span></span>  |<span data-ttu-id="402ef-120">Hodnota</span><span class="sxs-lookup"><span data-stu-id="402ef-120">Value</span></span>  |<span data-ttu-id="402ef-121">Popis</span><span class="sxs-lookup"><span data-stu-id="402ef-121">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="402ef-122">0x80041001</span><span class="sxs-lookup"><span data-stu-id="402ef-122">0x80041001</span></span> | <span data-ttu-id="402ef-123">Došlo k obecnému selhání.</span><span class="sxs-lookup"><span data-stu-id="402ef-123">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="402ef-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="402ef-124">0x80041008</span></span> | <span data-ttu-id="402ef-125">Parametr je neplatný.</span><span class="sxs-lookup"><span data-stu-id="402ef-125">A parameter is invalid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="402ef-126">0x80041006</span><span class="sxs-lookup"><span data-stu-id="402ef-126">0x80041006</span></span> | <span data-ttu-id="402ef-127">Operace není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="402ef-127">Not enough memory is available complete the operation.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="402ef-128">0x80041015</span><span class="sxs-lookup"><span data-stu-id="402ef-128">0x80041015</span></span> | <span data-ttu-id="402ef-129">Připojení vzdáleného volání procedur (RPC) mezi aktuálním procesem a službou WMI se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="402ef-129">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="402ef-130">0</span><span class="sxs-lookup"><span data-stu-id="402ef-130">0</span></span> | <span data-ttu-id="402ef-131">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="402ef-131">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="402ef-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="402ef-132">Remarks</span></span>

<span data-ttu-id="402ef-133">Tato funkce zabalí volání [metody IEnumWbemClassObject::Clone.](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone)</span><span class="sxs-lookup"><span data-stu-id="402ef-133">This function wraps a call to the [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) method.</span></span>

<span data-ttu-id="402ef-134">Tato metoda provede pouze "nejlepší úsilí" kopie.</span><span class="sxs-lookup"><span data-stu-id="402ef-134">This method makes only a "best effort" copy.</span></span> <span data-ttu-id="402ef-135">Vzhledem k dynamické povaze mnoho objektů CIM je možné, že nový čítač výčtu není výčet stejnou sadu objektů jako zdroj čítač výčtu.</span><span class="sxs-lookup"><span data-stu-id="402ef-135">Due to the dynamic nature of many CIM objects, it is possible that the new enumerator does not enumerate the same set of objects as the source enumerator.</span></span>

<span data-ttu-id="402ef-136">Pokud volání funkce selže, můžete získat další informace o chybě voláním funkce [GetErrorInfo.](geterrorinfo.md)</span><span class="sxs-lookup"><span data-stu-id="402ef-136">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="example"></a><span data-ttu-id="402ef-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="402ef-137">Example</span></span>

<span data-ttu-id="402ef-138">Příklad naleznete v metodě [IEnumWbemClassObject::Clone.](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone)</span><span class="sxs-lookup"><span data-stu-id="402ef-138">For an example, see the [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="402ef-139">Požadavky</span><span class="sxs-lookup"><span data-stu-id="402ef-139">Requirements</span></span>
 <span data-ttu-id="402ef-140">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="402ef-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="402ef-141">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="402ef-141">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="402ef-142">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="402ef-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="402ef-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="402ef-143">See also</span></span>

- [<span data-ttu-id="402ef-144">Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="402ef-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
