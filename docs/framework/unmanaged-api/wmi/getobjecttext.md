---
title: GetObjectText – funkce (Reference nespravovaného rozhraní API)
description: Funkce GetObjectText vrací textové vykreslování objektu v syntaxi MOF.
ms.date: 11/06/2017
api_name:
- GetObjectText
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetObjectText
helpviewer_keywords:
- GetObjectText function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 412e1ad503fa0e0b4f813298c0ac96ae80098c06
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73102456"
---
# <a name="getobjecttext-function"></a><span data-ttu-id="257e2-103">Funkce GetObjectText</span><span class="sxs-lookup"><span data-stu-id="257e2-103">GetObjectText function</span></span>
<span data-ttu-id="257e2-104">Vrátí textové vykreslování objektu v syntaxi formát MOF (Managed Object Format) (MOF).</span><span class="sxs-lookup"><span data-stu-id="257e2-104">Returns a textual rendering of the object in the Managed Object Format (MOF) syntax.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="257e2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="257e2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectText (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
); 
```  

## <a name="parameters"></a><span data-ttu-id="257e2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="257e2-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="257e2-107">pro Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="257e2-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="257e2-108">pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="257e2-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="257e2-109">pro Normálně 0.</span><span class="sxs-lookup"><span data-stu-id="257e2-109">[in] Normally 0.</span></span> <span data-ttu-id="257e2-110">Jsou-li zadány `WBEM_FLAG_NO_FLAVORS` (nebo 0x1), jsou kvalifikátory zahrnuty bez informací o šíření nebo charakteru.</span><span class="sxs-lookup"><span data-stu-id="257e2-110">If `WBEM_FLAG_NO_FLAVORS` (or 0x1) is specified, qualifiers are included without propagation or flavor information.</span></span>

`pstrObjectText`   
<span data-ttu-id="257e2-111">mimo Ukazatel na `null` na vstupu.</span><span class="sxs-lookup"><span data-stu-id="257e2-111">[out] A pointer to a `null` on entry.</span></span> <span data-ttu-id="257e2-112">Při návratu se nově přidělená `BSTR`, která obsahuje vykreslování syntaxe MOF objektu.</span><span class="sxs-lookup"><span data-stu-id="257e2-112">On return, a newly allocated `BSTR` that contains a MOF syntax rendering of the object.</span></span>  

## <a name="return-value"></a><span data-ttu-id="257e2-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="257e2-113">Return value</span></span>

<span data-ttu-id="257e2-114">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="257e2-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="257e2-115">Konstanta</span><span class="sxs-lookup"><span data-stu-id="257e2-115">Constant</span></span>  |<span data-ttu-id="257e2-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="257e2-116">Value</span></span>  |<span data-ttu-id="257e2-117">Popis</span><span class="sxs-lookup"><span data-stu-id="257e2-117">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="257e2-118">0x80041001</span><span class="sxs-lookup"><span data-stu-id="257e2-118">0x80041001</span></span> | <span data-ttu-id="257e2-119">Došlo k obecné chybě.</span><span class="sxs-lookup"><span data-stu-id="257e2-119">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="257e2-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="257e2-120">0x80041008</span></span> | <span data-ttu-id="257e2-121">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="257e2-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="257e2-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="257e2-122">0x80041006</span></span> | <span data-ttu-id="257e2-123">K dokončení této operace není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="257e2-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="257e2-124">0,8</span><span class="sxs-lookup"><span data-stu-id="257e2-124">0</span></span> | <span data-ttu-id="257e2-125">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="257e2-125">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="257e2-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="257e2-126">Remarks</span></span>

<span data-ttu-id="257e2-127">Tato funkce zalomí volání metody [IWbemclassObject:: GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) .</span><span class="sxs-lookup"><span data-stu-id="257e2-127">This function wraps a call to the [IWbemClassObject::GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) method.</span></span>

<span data-ttu-id="257e2-128">Vrácený text MOF neobsahuje všechny informace o objektu, ale pouze dostatek informací pro kompilátor MOF, aby bylo možné znovu vytvořit původní objekt.</span><span class="sxs-lookup"><span data-stu-id="257e2-128">The MOF text returned does not contain all the information about the object, but only enough information for the MOF compiler to be able to recreate the original object.</span></span> <span data-ttu-id="257e2-129">Například nejsou zahrnuty žádné šířené vlastnosti kvalifikátorů nebo nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="257e2-129">For instance, no propagated qualifiers or parent class properties are included.</span></span>

<span data-ttu-id="257e2-130">Následující algoritmus slouží k rekonstrukci textu parametrů metody:</span><span class="sxs-lookup"><span data-stu-id="257e2-130">The following algorithm is used to reconstruct the text of the parameters of a method:</span></span>

1. <span data-ttu-id="257e2-131">Parametry se přesekvencují v pořadí jejich hodnot identifikátorů.</span><span class="sxs-lookup"><span data-stu-id="257e2-131">Parameters are resequenced in the order of their identifier values.</span></span>
1. <span data-ttu-id="257e2-132">Parametry, které jsou zadány jako `[in]` a `[out]` jsou zkombinovány do jednoho parametru.</span><span class="sxs-lookup"><span data-stu-id="257e2-132">Parameters that are specified as `[in]` and `[out]` are combined into a single parameter.</span></span>
 
<span data-ttu-id="257e2-133">`pstrObjectText` musí být ukazatel na `null` při volání funkce. nesmí ukazovat na řetězec, který je platný před voláním metody, protože ukazatel nebude navrácen.</span><span class="sxs-lookup"><span data-stu-id="257e2-133">`pstrObjectText` must be a pointer to a `null` when the function is called; it must not point to a string that is valid before the method call, because the pointer will not be deallocated.</span></span>

## <a name="requirements"></a><span data-ttu-id="257e2-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="257e2-134">Requirements</span></span>  
<span data-ttu-id="257e2-135">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="257e2-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="257e2-136">**Hlavička:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="257e2-136">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="257e2-137">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="257e2-137">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="257e2-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="257e2-138">See also</span></span>

- [<span data-ttu-id="257e2-139">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="257e2-139">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
