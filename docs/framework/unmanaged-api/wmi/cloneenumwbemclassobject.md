---
title: CloneEnumWbemClassObject – funkce (Reference nespravovaného rozhraní API)
description: Funkce CloneEnumWbemClassObject vytvoří logickou kopii enumerátoru.
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
ms.openlocfilehash: 9d2442161aaa83693a33f9efc230c09b8c4426e2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128724"
---
# <a name="cloneenumwbemclassobject-function"></a><span data-ttu-id="93dd4-103">Funkce CloneEnumWbemClassObject</span><span class="sxs-lookup"><span data-stu-id="93dd4-103">CloneEnumWbemClassObject function</span></span>
<span data-ttu-id="93dd4-104">Vytvoří logickou kopii enumerátoru a uchová jeho aktuální pozici ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="93dd4-104">Makes a logical copy of an enumerator, retaining its current position in an enumeration.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="93dd4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93dd4-105">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="93dd4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="93dd4-106">Parameters</span></span>

`ppEnum`\
<span data-ttu-id="93dd4-107">mimo Přijme ukazatel na nový [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject).</span><span class="sxs-lookup"><span data-stu-id="93dd4-107">[out] Receives a pointer to a new [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject).</span></span>

`authLevel`\
<span data-ttu-id="93dd4-108">pro Úroveň autorizace.</span><span class="sxs-lookup"><span data-stu-id="93dd4-108">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="93dd4-109">pro Úroveň zosobnění.</span><span class="sxs-lookup"><span data-stu-id="93dd4-109">[in] The impersonation level.</span></span>

`pCurrentEnumWbemClassObject`\
<span data-ttu-id="93dd4-110">mimo Ukazatel na instanci [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) , která se má klonovat</span><span class="sxs-lookup"><span data-stu-id="93dd4-110">[out] A pointer to the [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) instance to be cloned.</span></span>

`strUser`\
<span data-ttu-id="93dd4-111">pro Uživatelské jméno</span><span class="sxs-lookup"><span data-stu-id="93dd4-111">[in] The user name.</span></span> <span data-ttu-id="93dd4-112">Další informace najdete v tématu funkce [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="93dd4-112">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="93dd4-113">pro Heslo.</span><span class="sxs-lookup"><span data-stu-id="93dd4-113">[in] The password.</span></span> <span data-ttu-id="93dd4-114">Další informace najdete v tématu funkce [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="93dd4-114">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

<span data-ttu-id="93dd4-115">`strAuthority`\ [in] název domény uživatele.</span><span class="sxs-lookup"><span data-stu-id="93dd4-115">`strAuthority`\ [in] The domain name of the user.</span></span> <span data-ttu-id="93dd4-116">Další informace najdete v tématu funkce [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="93dd4-116">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="93dd4-117">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="93dd4-117">Return value</span></span>

<span data-ttu-id="93dd4-118">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="93dd4-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="93dd4-119">Konstanta</span><span class="sxs-lookup"><span data-stu-id="93dd4-119">Constant</span></span>  |<span data-ttu-id="93dd4-120">Hodnota</span><span class="sxs-lookup"><span data-stu-id="93dd4-120">Value</span></span>  |<span data-ttu-id="93dd4-121">Popis</span><span class="sxs-lookup"><span data-stu-id="93dd4-121">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="93dd4-122">0x80041001</span><span class="sxs-lookup"><span data-stu-id="93dd4-122">0x80041001</span></span> | <span data-ttu-id="93dd4-123">Došlo k obecné chybě.</span><span class="sxs-lookup"><span data-stu-id="93dd4-123">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="93dd4-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="93dd4-124">0x80041008</span></span> | <span data-ttu-id="93dd4-125">Parametr je neplatný.</span><span class="sxs-lookup"><span data-stu-id="93dd4-125">A parameter is invalid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="93dd4-126">0x80041006</span><span class="sxs-lookup"><span data-stu-id="93dd4-126">0x80041006</span></span> | <span data-ttu-id="93dd4-127">K dokončení operace není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="93dd4-127">Not enough memory is available complete the operation.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="93dd4-128">0x80041015</span><span class="sxs-lookup"><span data-stu-id="93dd4-128">0x80041015</span></span> | <span data-ttu-id="93dd4-129">Propojení vzdáleného volání procedur (RPC) mezi aktuálním procesem a rozhraním WMI se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="93dd4-129">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="93dd4-130">0,8</span><span class="sxs-lookup"><span data-stu-id="93dd4-130">0</span></span> | <span data-ttu-id="93dd4-131">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="93dd4-131">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="93dd4-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="93dd4-132">Remarks</span></span>

<span data-ttu-id="93dd4-133">Tato funkce zalomí volání metody [IEnumWbemClassObject:: Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) .</span><span class="sxs-lookup"><span data-stu-id="93dd4-133">This function wraps a call to the [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) method.</span></span>

<span data-ttu-id="93dd4-134">Tato metoda vytvoří pouze "nejlepší úsilí".</span><span class="sxs-lookup"><span data-stu-id="93dd4-134">This method makes only a "best effort" copy.</span></span> <span data-ttu-id="93dd4-135">Vzhledem k dynamické povaze mnoha objektů CIM je možné, že nový enumerátor nevytvoří výčet stejné sady objektů jako zdrojový enumerátor.</span><span class="sxs-lookup"><span data-stu-id="93dd4-135">Due to the dynamic nature of many CIM objects, it is possible that the new enumerator does not enumerate the same set of objects as the source enumerator.</span></span>

<span data-ttu-id="93dd4-136">Pokud volání funkce neproběhne úspěšně, můžete získat další informace o chybě voláním funkce [GetErrorInfo](geterrorinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="93dd4-136">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="example"></a><span data-ttu-id="93dd4-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="93dd4-137">Example</span></span>

<span data-ttu-id="93dd4-138">Příklad naleznete v tématu metoda [IEnumWbemClassObject:: Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) .</span><span class="sxs-lookup"><span data-stu-id="93dd4-138">For an example, see the [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="93dd4-139">Požadavky</span><span class="sxs-lookup"><span data-stu-id="93dd4-139">Requirements</span></span>
 <span data-ttu-id="93dd4-140">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93dd4-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="93dd4-141">**Hlavička:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="93dd4-141">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="93dd4-142">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="93dd4-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="93dd4-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="93dd4-143">See also</span></span>

- [<span data-ttu-id="93dd4-144">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="93dd4-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
