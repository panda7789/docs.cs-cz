---
title: Funkce QualifierSet_Next (referenční dokumentace nespravovaného rozhraní API)
description: Funkce QualifierSet_Next načte další kvalifikátor ve výčtu.
ms.date: 11/06/2017
api_name:
- QualifierSet_Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Next
helpviewer_keywords:
- QualifierSet_Next function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 938044a4e932139eb8a4d0a5d2f998cbc6f193cb
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507690"
---
# <a name="qualifiersetnext-function"></a><span data-ttu-id="f8fc2-103">QualifierSet_Next – funkce</span><span class="sxs-lookup"><span data-stu-id="f8fc2-103">QualifierSet_Next function</span></span>
<span data-ttu-id="f8fc2-104">Načte další kvalifikátor ve výčtu, který spustil pomocí volání [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="f8fc2-104">Retrieves the next qualifier in an enumeration that started with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>   

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="f8fc2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8fc2-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_Next (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags,
   [out] BSTR*               pstrName,        
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor                 
); 
```  

## <a name="parameters"></a><span data-ttu-id="f8fc2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f8fc2-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="f8fc2-107">[in] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="f8fc2-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="f8fc2-108">[in] Ukazatel [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span><span class="sxs-lookup"><span data-stu-id="f8fc2-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`lFlags`   
<span data-ttu-id="f8fc2-109">[in] Vyhrazená.</span><span class="sxs-lookup"><span data-stu-id="f8fc2-109">[in] Reserved.</span></span> <span data-ttu-id="f8fc2-110">Tento parametr musí být 0.</span><span class="sxs-lookup"><span data-stu-id="f8fc2-110">This parameter must be 0.</span></span>

`pstrName`   
<span data-ttu-id="f8fc2-111">[out] Název kvalifikátor.</span><span class="sxs-lookup"><span data-stu-id="f8fc2-111">[out] The name of the qualifier.</span></span> <span data-ttu-id="f8fc2-112">Pokud `null`, tento parametr se ignoruje; v opačném případě `pstrName` nesmí odkazovat na platnou `BSTR` nebo nevracení paměti.</span><span class="sxs-lookup"><span data-stu-id="f8fc2-112">If `null`, this parameter is ignored; otherwise, `pstrName` should not point to a valid `BSTR` or a memory leak occurs.</span></span> <span data-ttu-id="f8fc2-113">Pokud není null, funkce vždy přidělí novou `BSTR` při vrácení `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="f8fc2-113">If not null, the function always allocates a new `BSTR` when it returns `WBEM_S_NO_ERROR`.</span></span>

`pVal`   
<span data-ttu-id="f8fc2-114">[out] V případě úspěchu, hodnota pro kvalifikátor.</span><span class="sxs-lookup"><span data-stu-id="f8fc2-114">[out] When successful, the value for the qualifier.</span></span> <span data-ttu-id="f8fc2-115">Pokud funkce selže, `VARIANT` odkazované `pVal` se nezmění.</span><span class="sxs-lookup"><span data-stu-id="f8fc2-115">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="f8fc2-116">Pokud je tento parametr `null`, tento parametr je ignorován.</span><span class="sxs-lookup"><span data-stu-id="f8fc2-116">If this parameter is `null`, the parameter is ignored.</span></span>

`plFlavor`   
<span data-ttu-id="f8fc2-117">[out] Ukazatel, který přijímá charakter kvalifikátoru DLOUHO.</span><span class="sxs-lookup"><span data-stu-id="f8fc2-117">[out] A pointer to a LONG that receives the qualifier flavor.</span></span> <span data-ttu-id="f8fc2-118">Pokud není žádoucí informace charakter, tento parametr může být `null`.</span><span class="sxs-lookup"><span data-stu-id="f8fc2-118">If flavor information is not desired, this parameter can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="f8fc2-119">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f8fc2-119">Return value</span></span>

<span data-ttu-id="f8fc2-120">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="f8fc2-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="f8fc2-121">Konstanta</span><span class="sxs-lookup"><span data-stu-id="f8fc2-121">Constant</span></span>  |<span data-ttu-id="f8fc2-122">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f8fc2-122">Value</span></span>  |<span data-ttu-id="f8fc2-123">Popis</span><span class="sxs-lookup"><span data-stu-id="f8fc2-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="f8fc2-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="f8fc2-124">0x80041008</span></span> | <span data-ttu-id="f8fc2-125">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="f8fc2-125">A parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="f8fc2-126">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="f8fc2-126">0x8004101d</span></span> | <span data-ttu-id="f8fc2-127">Volající nezavolalo [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="f8fc2-127">The caller did not call [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="f8fc2-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="f8fc2-128">0x80041006</span></span> | <span data-ttu-id="f8fc2-129">Nedostatek paměti je k dispozici zahájíte nový výčet.</span><span class="sxs-lookup"><span data-stu-id="f8fc2-129">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="f8fc2-130">0x40005</span><span class="sxs-lookup"><span data-stu-id="f8fc2-130">0x40005</span></span> | <span data-ttu-id="f8fc2-131">Žádné další kvalifikátory jsou ponechány ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="f8fc2-131">No more qualifiers are left in the enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="f8fc2-132">0</span><span class="sxs-lookup"><span data-stu-id="f8fc2-132">0</span></span> | <span data-ttu-id="f8fc2-133">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="f8fc2-133">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="f8fc2-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f8fc2-134">Remarks</span></span>

<span data-ttu-id="f8fc2-135">Tato funkce zalamuje volání na [IWbemQualifierSet::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) metody.</span><span class="sxs-lookup"><span data-stu-id="f8fc2-135">This function wraps a call to the [IWbemQualifierSet::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) method.</span></span>

<span data-ttu-id="f8fc2-136">Volání `QualifierSet_Next` funkce opakovaně k vytvoření výčtu v kvalifikátorech dokud návratová hodnota funkce `WBEM_S_NO_MORE_DATA`.</span><span class="sxs-lookup"><span data-stu-id="f8fc2-136">You call the `QualifierSet_Next` function repeatedly to enumerate all the qualifiers until the function return `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="f8fc2-137">Chcete-li ukončit výčet již v rané fázi, zavolejte [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="f8fc2-137">To terminate the enumeration early, call the [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) function.</span></span>

<span data-ttu-id="f8fc2-138">Pořadí kvalifikátory vrátil během výčtu není definováno.</span><span class="sxs-lookup"><span data-stu-id="f8fc2-138">The order of the qualifiers returned during the enumeration is undefined.</span></span>

## <a name="requirements"></a><span data-ttu-id="f8fc2-139">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f8fc2-139">Requirements</span></span>  
 <span data-ttu-id="f8fc2-140">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8fc2-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8fc2-141">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="f8fc2-141">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="f8fc2-142">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f8fc2-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8fc2-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f8fc2-143">See also</span></span>  
[<span data-ttu-id="f8fc2-144">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="f8fc2-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
