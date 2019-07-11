---
title: Funkce DeleteMethod (referenční dokumentace nespravovaného rozhraní API)
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 291d5d0461da8d130d41f9a0eca67ea3be42b4bc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746822"
---
# <a name="deletemethod-function"></a><span data-ttu-id="fccd1-103">Funkce DeleteMethod</span><span class="sxs-lookup"><span data-stu-id="fccd1-103">DeleteMethod function</span></span>
<span data-ttu-id="fccd1-104">Odstraní zadanou metodu z definice třídy CIM.</span><span class="sxs-lookup"><span data-stu-id="fccd1-104">Deletes the specified method from a CIM class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="fccd1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fccd1-105">Syntax</span></span>  
  
```cpp  
HRESULT Delete (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName 
); 
```  

## <a name="parameters"></a><span data-ttu-id="fccd1-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="fccd1-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="fccd1-107">[in] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="fccd1-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="fccd1-108">[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span><span class="sxs-lookup"><span data-stu-id="fccd1-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="fccd1-109">[in] Název metody, která odebere z tabulky třídy.</span><span class="sxs-lookup"><span data-stu-id="fccd1-109">[in] The name of the method to remove from the class table.</span></span> <span data-ttu-id="fccd1-110">`wszName` musí být ukazatel na platný `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="fccd1-110">`wszName` must be a pointer to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="fccd1-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fccd1-111">Return value</span></span>

<span data-ttu-id="fccd1-112">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="fccd1-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="fccd1-113">Konstanta</span><span class="sxs-lookup"><span data-stu-id="fccd1-113">Constant</span></span>  |<span data-ttu-id="fccd1-114">Value</span><span class="sxs-lookup"><span data-stu-id="fccd1-114">Value</span></span>  |<span data-ttu-id="fccd1-115">Popis</span><span class="sxs-lookup"><span data-stu-id="fccd1-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="fccd1-116">0x80041002</span><span class="sxs-lookup"><span data-stu-id="fccd1-116">0x80041002</span></span> | <span data-ttu-id="fccd1-117">Zadaná metoda neexistuje.</span><span class="sxs-lookup"><span data-stu-id="fccd1-117">The specified method does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="fccd1-118">0x80041006</span><span class="sxs-lookup"><span data-stu-id="fccd1-118">0x80041006</span></span> | <span data-ttu-id="fccd1-119">Není k dispozici dostatek paměti k dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="fccd1-119">There is not enough memory to complete the operation.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="fccd1-120">0</span><span class="sxs-lookup"><span data-stu-id="fccd1-120">0</span></span> | <span data-ttu-id="fccd1-121">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="fccd1-121">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="fccd1-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fccd1-122">Remarks</span></span>

<span data-ttu-id="fccd1-123">Tato funkce zalamuje volání na [IWbemClassObject::DeleteMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-deletemethod) metody.</span><span class="sxs-lookup"><span data-stu-id="fccd1-123">This function wraps a call to the [IWbemClassObject::DeleteMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-deletemethod) method.</span></span>

<span data-ttu-id="fccd1-124">Metoda odstranění není podporováno pro [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) ukazatele, které odkazují na instance CIM.</span><span class="sxs-lookup"><span data-stu-id="fccd1-124">Method deletion is not supported for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

## <a name="requirements"></a><span data-ttu-id="fccd1-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fccd1-125">Requirements</span></span>  
 <span data-ttu-id="fccd1-126">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fccd1-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fccd1-127">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="fccd1-127">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="fccd1-128">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="fccd1-128">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fccd1-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fccd1-129">See also</span></span>

- [<span data-ttu-id="fccd1-130">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="fccd1-130">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
