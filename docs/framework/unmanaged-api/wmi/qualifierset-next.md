---
title: QualifierSet_Next funkce (Unmanaged API Reference)
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
ms.openlocfilehash: d3702426bc409d601ccfc6b7a8e93e8d9729c64e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174872"
---
# <a name="qualifierset_next-function"></a><span data-ttu-id="a4b65-103">QualifierSet_Next funkce</span><span class="sxs-lookup"><span data-stu-id="a4b65-103">QualifierSet_Next function</span></span>
<span data-ttu-id="a4b65-104">Načte další kvalifikátor ve výčtu, který začal s voláním [funkce QualifierSet_BeginEnumeration.](qualifierset-beginenumeration.md)</span><span class="sxs-lookup"><span data-stu-id="a4b65-104">Retrieves the next qualifier in an enumeration that started with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="a4b65-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4b65-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_Next (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags,
   [out] BSTR*               pstrName,
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor
);
```  

## <a name="parameters"></a><span data-ttu-id="a4b65-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a4b65-106">Parameters</span></span>

<span data-ttu-id="a4b65-107">`vFunc`[v] Tento parametr není použit.</span><span class="sxs-lookup"><span data-stu-id="a4b65-107">`vFunc` [in] This parameter is unused.</span></span>

<span data-ttu-id="a4b65-108">`ptr`[v] Ukazatel na instanci [IWbemQualifierSet.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)</span><span class="sxs-lookup"><span data-stu-id="a4b65-108">`ptr` [in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

<span data-ttu-id="a4b65-109">`lFlags`[v] Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="a4b65-109">`lFlags` [in] Reserved.</span></span> <span data-ttu-id="a4b65-110">Tento parametr musí být 0.</span><span class="sxs-lookup"><span data-stu-id="a4b65-110">This parameter must be 0.</span></span>

<span data-ttu-id="a4b65-111">`pstrName`[out] Název kvalifikátoru.</span><span class="sxs-lookup"><span data-stu-id="a4b65-111">`pstrName` [out] The name of the qualifier.</span></span> <span data-ttu-id="a4b65-112">Pokud `null`je tento parametr ignorován; v `pstrName` opačném případě by `BSTR` neměl apoukázat na platný nebo dojde k nevracení paměti.</span><span class="sxs-lookup"><span data-stu-id="a4b65-112">If `null`, this parameter is ignored; otherwise, `pstrName` should not point to a valid `BSTR` or a memory leak occurs.</span></span> <span data-ttu-id="a4b65-113">Pokud není null, funkce vždy `BSTR` přiděluje nový, když vrátí `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="a4b65-113">If not null, the function always allocates a new `BSTR` when it returns `WBEM_S_NO_ERROR`.</span></span>

<span data-ttu-id="a4b65-114">`pVal`[out] V případě úspěchu, hodnota pro kvalifikátor.</span><span class="sxs-lookup"><span data-stu-id="a4b65-114">`pVal` [out] When successful, the value for the qualifier.</span></span> <span data-ttu-id="a4b65-115">Pokud funkce selže, `VARIANT` odkazová `pVal` na od se nezmění.</span><span class="sxs-lookup"><span data-stu-id="a4b65-115">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="a4b65-116">Pokud je `null`tento parametr , parametr je ignorován.</span><span class="sxs-lookup"><span data-stu-id="a4b65-116">If this parameter is `null`, the parameter is ignored.</span></span>

<span data-ttu-id="a4b65-117">`plFlavor`[out] Ukazatel na LONG, který obdrží kvalifikátor chuť.</span><span class="sxs-lookup"><span data-stu-id="a4b65-117">`plFlavor` [out] A pointer to a LONG that receives the qualifier flavor.</span></span> <span data-ttu-id="a4b65-118">Pokud informace o chuti není žádoucí, tento parametr může být `null`.</span><span class="sxs-lookup"><span data-stu-id="a4b65-118">If flavor information is not desired, this parameter can be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="a4b65-119">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a4b65-119">Return value</span></span>

<span data-ttu-id="a4b65-120">Následující hodnoty vrácené touto funkcí jsou definovány v souboru *hlavičky WbemCli.h,* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="a4b65-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="a4b65-121">Trvalé</span><span class="sxs-lookup"><span data-stu-id="a4b65-121">Constant</span></span>  |<span data-ttu-id="a4b65-122">Hodnota</span><span class="sxs-lookup"><span data-stu-id="a4b65-122">Value</span></span>  |<span data-ttu-id="a4b65-123">Popis</span><span class="sxs-lookup"><span data-stu-id="a4b65-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="a4b65-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="a4b65-124">0x80041008</span></span> | <span data-ttu-id="a4b65-125">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="a4b65-125">A parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="a4b65-126">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="a4b65-126">0x8004101d</span></span> | <span data-ttu-id="a4b65-127">Volající nevolal [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="a4b65-127">The caller did not call [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="a4b65-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="a4b65-128">0x80041006</span></span> | <span data-ttu-id="a4b65-129">Není k dispozici dostatek paměti pro zahájení nového výčtu.</span><span class="sxs-lookup"><span data-stu-id="a4b65-129">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="a4b65-130">0x40005</span><span class="sxs-lookup"><span data-stu-id="a4b65-130">0x40005</span></span> | <span data-ttu-id="a4b65-131">Žádné další kvalifikátory jsou ponechány ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="a4b65-131">No more qualifiers are left in the enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="a4b65-132">0</span><span class="sxs-lookup"><span data-stu-id="a4b65-132">0</span></span> | <span data-ttu-id="a4b65-133">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="a4b65-133">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="a4b65-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a4b65-134">Remarks</span></span>

<span data-ttu-id="a4b65-135">Tato funkce zalomí volání [IWbemQualifierSet::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) metoda.</span><span class="sxs-lookup"><span data-stu-id="a4b65-135">This function wraps a call to the [IWbemQualifierSet::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) method.</span></span>

<span data-ttu-id="a4b65-136">Volání `QualifierSet_Next` funkce opakovaně výčet všech kvalifikátorů, `WBEM_S_NO_MORE_DATA`dokud funkce vrátit .</span><span class="sxs-lookup"><span data-stu-id="a4b65-136">You call the `QualifierSet_Next` function repeatedly to enumerate all the qualifiers until the function return `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="a4b65-137">Chcete-li výčet ukončit dříve, zavolejte [funkci QualifierSet_EndEnumeration.](qualifierset-endenumeration.md)</span><span class="sxs-lookup"><span data-stu-id="a4b65-137">To terminate the enumeration early, call the [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) function.</span></span>

<span data-ttu-id="a4b65-138">Pořadí kvalifikátory vrácené během výčtu není definováno.</span><span class="sxs-lookup"><span data-stu-id="a4b65-138">The order of the qualifiers returned during the enumeration is undefined.</span></span>

## <a name="requirements"></a><span data-ttu-id="a4b65-139">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a4b65-139">Requirements</span></span>  
 <span data-ttu-id="a4b65-140">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4b65-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4b65-141">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="a4b65-141">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="a4b65-142">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a4b65-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4b65-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="a4b65-143">See also</span></span>

- [<span data-ttu-id="a4b65-144">Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="a4b65-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
