---
title: DeleteMethod – funkce (Reference nespravovaného rozhraní API)
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
ms.openlocfilehash: 4db81c4c7e123eed82b3092912b8d871edb54618
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798655"
---
# <a name="deletemethod-function"></a><span data-ttu-id="bf9bf-103">Funkce DeleteMethod</span><span class="sxs-lookup"><span data-stu-id="bf9bf-103">DeleteMethod function</span></span>
<span data-ttu-id="bf9bf-104">Odstraní zadanou metodu z definice třídy CIM.</span><span class="sxs-lookup"><span data-stu-id="bf9bf-104">Deletes the specified method from a CIM class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="bf9bf-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf9bf-105">Syntax</span></span>  
  
```cpp  
HRESULT Delete (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName 
); 
```  

## <a name="parameters"></a><span data-ttu-id="bf9bf-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="bf9bf-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="bf9bf-107">pro Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="bf9bf-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="bf9bf-108">pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="bf9bf-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="bf9bf-109">pro Název metody, která má být odebrána z tabulky třídy.</span><span class="sxs-lookup"><span data-stu-id="bf9bf-109">[in] The name of the method to remove from the class table.</span></span> <span data-ttu-id="bf9bf-110">`wszName`musí být ukazatel na platný `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="bf9bf-110">`wszName` must be a pointer to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="bf9bf-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bf9bf-111">Return value</span></span>

<span data-ttu-id="bf9bf-112">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="bf9bf-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="bf9bf-113">Konstanta</span><span class="sxs-lookup"><span data-stu-id="bf9bf-113">Constant</span></span>  |<span data-ttu-id="bf9bf-114">Value</span><span class="sxs-lookup"><span data-stu-id="bf9bf-114">Value</span></span>  |<span data-ttu-id="bf9bf-115">Popis</span><span class="sxs-lookup"><span data-stu-id="bf9bf-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="bf9bf-116">0x80041002</span><span class="sxs-lookup"><span data-stu-id="bf9bf-116">0x80041002</span></span> | <span data-ttu-id="bf9bf-117">Zadaná metoda neexistuje.</span><span class="sxs-lookup"><span data-stu-id="bf9bf-117">The specified method does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="bf9bf-118">0x80041006</span><span class="sxs-lookup"><span data-stu-id="bf9bf-118">0x80041006</span></span> | <span data-ttu-id="bf9bf-119">K dokončení operace není dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="bf9bf-119">There is not enough memory to complete the operation.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="bf9bf-120">0</span><span class="sxs-lookup"><span data-stu-id="bf9bf-120">0</span></span> | <span data-ttu-id="bf9bf-121">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="bf9bf-121">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="bf9bf-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bf9bf-122">Remarks</span></span>

<span data-ttu-id="bf9bf-123">Tato funkce zalomí volání metody [IWbemclassObject::D eletemethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-deletemethod) .</span><span class="sxs-lookup"><span data-stu-id="bf9bf-123">This function wraps a call to the [IWbemClassObject::DeleteMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-deletemethod) method.</span></span>

<span data-ttu-id="bf9bf-124">Odstranění metody není podporováno u ukazatelů [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) odkazujících na instance CIM.</span><span class="sxs-lookup"><span data-stu-id="bf9bf-124">Method deletion is not supported for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

## <a name="requirements"></a><span data-ttu-id="bf9bf-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bf9bf-125">Requirements</span></span>  
 <span data-ttu-id="bf9bf-126">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf9bf-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf9bf-127">**Hlaviček** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="bf9bf-127">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="bf9bf-128">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bf9bf-128">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf9bf-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bf9bf-129">See also</span></span>

- [<span data-ttu-id="bf9bf-130">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="bf9bf-130">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
