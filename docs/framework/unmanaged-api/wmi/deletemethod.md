---
title: DeleteMethod function (Unmanaged API Reference)
description: Funkce DeleteMethod odstraní zadanou metodu z definice třídy CIM.
ms.date: 11/06/2017
api_name:
- DeleteMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- DeleteMethod
helpviewer_keywords:
- DeleteMethod function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 4059555d74c0b0f151332ddcf9faedecf238e795
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174989"
---
# <a name="deletemethod-function"></a><span data-ttu-id="ea6e3-103">Funkce DeleteMethod</span><span class="sxs-lookup"><span data-stu-id="ea6e3-103">DeleteMethod function</span></span>
<span data-ttu-id="ea6e3-104">Odstraní zadanou metodu z definice třídy CIM.</span><span class="sxs-lookup"><span data-stu-id="ea6e3-104">Deletes the specified method from a CIM class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="ea6e3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea6e3-105">Syntax</span></span>  
  
```cpp  
HRESULT Delete (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName
);
```  

## <a name="parameters"></a><span data-ttu-id="ea6e3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ea6e3-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="ea6e3-107">[v] Tento parametr není použit.</span><span class="sxs-lookup"><span data-stu-id="ea6e3-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="ea6e3-108">[v] Ukazatel na instanci [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="ea6e3-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="ea6e3-109">[v] Název metody odebrat z tabulky třídy.</span><span class="sxs-lookup"><span data-stu-id="ea6e3-109">[in] The name of the method to remove from the class table.</span></span> <span data-ttu-id="ea6e3-110">`wszName`musí být ukazatel na `LPCWSTR`platný .</span><span class="sxs-lookup"><span data-stu-id="ea6e3-110">`wszName` must be a pointer to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="ea6e3-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ea6e3-111">Return value</span></span>

<span data-ttu-id="ea6e3-112">Následující hodnoty vrácené touto funkcí jsou definovány v souboru *hlavičky WbemCli.h,* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="ea6e3-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="ea6e3-113">Trvalé</span><span class="sxs-lookup"><span data-stu-id="ea6e3-113">Constant</span></span>  |<span data-ttu-id="ea6e3-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ea6e3-114">Value</span></span>  |<span data-ttu-id="ea6e3-115">Popis</span><span class="sxs-lookup"><span data-stu-id="ea6e3-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="ea6e3-116">0x80041002</span><span class="sxs-lookup"><span data-stu-id="ea6e3-116">0x80041002</span></span> | <span data-ttu-id="ea6e3-117">Zadaná metoda neexistuje.</span><span class="sxs-lookup"><span data-stu-id="ea6e3-117">The specified method does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="ea6e3-118">0x80041006</span><span class="sxs-lookup"><span data-stu-id="ea6e3-118">0x80041006</span></span> | <span data-ttu-id="ea6e3-119">K dokončení operace není dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="ea6e3-119">There is not enough memory to complete the operation.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="ea6e3-120">0</span><span class="sxs-lookup"><span data-stu-id="ea6e3-120">0</span></span> | <span data-ttu-id="ea6e3-121">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="ea6e3-121">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="ea6e3-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ea6e3-122">Remarks</span></span>

<span data-ttu-id="ea6e3-123">Tato funkce zabalí volání metody [IWbemClassObject::DeleteMethod.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-deletemethod)</span><span class="sxs-lookup"><span data-stu-id="ea6e3-123">This function wraps a call to the [IWbemClassObject::DeleteMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-deletemethod) method.</span></span>

<span data-ttu-id="ea6e3-124">Odstranění metody není podporováno pro ukazatele [IWbemClassObject,](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) které odkazují na instance CIM.</span><span class="sxs-lookup"><span data-stu-id="ea6e3-124">Method deletion is not supported for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

## <a name="requirements"></a><span data-ttu-id="ea6e3-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ea6e3-125">Requirements</span></span>  
 <span data-ttu-id="ea6e3-126">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea6e3-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea6e3-127">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="ea6e3-127">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="ea6e3-128">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ea6e3-128">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea6e3-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="ea6e3-129">See also</span></span>

- [<span data-ttu-id="ea6e3-130">Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="ea6e3-130">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
