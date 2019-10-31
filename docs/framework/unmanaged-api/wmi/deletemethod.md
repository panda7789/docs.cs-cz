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
ms.openlocfilehash: db360584dacf250be2f35e5e6666f8332b39a8dd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120650"
---
# <a name="deletemethod-function"></a><span data-ttu-id="f775e-103">Funkce DeleteMethod</span><span class="sxs-lookup"><span data-stu-id="f775e-103">DeleteMethod function</span></span>
<span data-ttu-id="f775e-104">Odstraní zadanou metodu z definice třídy CIM.</span><span class="sxs-lookup"><span data-stu-id="f775e-104">Deletes the specified method from a CIM class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="f775e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f775e-105">Syntax</span></span>  
  
```cpp  
HRESULT Delete (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName 
); 
```  

## <a name="parameters"></a><span data-ttu-id="f775e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f775e-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="f775e-107">pro Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="f775e-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="f775e-108">pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="f775e-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="f775e-109">pro Název metody, která má být odebrána z tabulky třídy.</span><span class="sxs-lookup"><span data-stu-id="f775e-109">[in] The name of the method to remove from the class table.</span></span> <span data-ttu-id="f775e-110">`wszName` musí být ukazatel na platný `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="f775e-110">`wszName` must be a pointer to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="f775e-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f775e-111">Return value</span></span>

<span data-ttu-id="f775e-112">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="f775e-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="f775e-113">Konstanta</span><span class="sxs-lookup"><span data-stu-id="f775e-113">Constant</span></span>  |<span data-ttu-id="f775e-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f775e-114">Value</span></span>  |<span data-ttu-id="f775e-115">Popis</span><span class="sxs-lookup"><span data-stu-id="f775e-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="f775e-116">0x80041002</span><span class="sxs-lookup"><span data-stu-id="f775e-116">0x80041002</span></span> | <span data-ttu-id="f775e-117">Zadaná metoda neexistuje.</span><span class="sxs-lookup"><span data-stu-id="f775e-117">The specified method does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="f775e-118">0x80041006</span><span class="sxs-lookup"><span data-stu-id="f775e-118">0x80041006</span></span> | <span data-ttu-id="f775e-119">K dokončení operace není dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="f775e-119">There is not enough memory to complete the operation.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="f775e-120">0,8</span><span class="sxs-lookup"><span data-stu-id="f775e-120">0</span></span> | <span data-ttu-id="f775e-121">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="f775e-121">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="f775e-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f775e-122">Remarks</span></span>

<span data-ttu-id="f775e-123">Tato funkce zalomí volání metody [IWbemclassObject::D eletemethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-deletemethod) .</span><span class="sxs-lookup"><span data-stu-id="f775e-123">This function wraps a call to the [IWbemClassObject::DeleteMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-deletemethod) method.</span></span>

<span data-ttu-id="f775e-124">Odstranění metody není podporováno u ukazatelů [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) odkazujících na instance CIM.</span><span class="sxs-lookup"><span data-stu-id="f775e-124">Method deletion is not supported for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

## <a name="requirements"></a><span data-ttu-id="f775e-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f775e-125">Requirements</span></span>  
 <span data-ttu-id="f775e-126">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f775e-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f775e-127">**Hlavička:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="f775e-127">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="f775e-128">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f775e-128">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f775e-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f775e-129">See also</span></span>

- [<span data-ttu-id="f775e-130">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="f775e-130">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
