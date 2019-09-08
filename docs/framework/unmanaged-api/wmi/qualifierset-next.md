---
title: QualifierSet_Next – funkce (Reference nespravovaného rozhraní API)
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
ms.openlocfilehash: f97a19f236b87a7f4c5b2014aca6ee4abd338c63
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798279"
---
# <a name="qualifierset_next-function"></a><span data-ttu-id="f4965-103">QualifierSet_Next – funkce</span><span class="sxs-lookup"><span data-stu-id="f4965-103">QualifierSet_Next function</span></span>
<span data-ttu-id="f4965-104">Načte další kvalifikátor ve výčtu, který začal voláním funkce [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="f4965-104">Retrieves the next qualifier in an enumeration that started with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>   

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="f4965-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f4965-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="f4965-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f4965-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="f4965-107">pro Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="f4965-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="f4965-108">pro Ukazatel na instanci [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="f4965-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`lFlags`   
<span data-ttu-id="f4965-109">pro Rezervovaný.</span><span class="sxs-lookup"><span data-stu-id="f4965-109">[in] Reserved.</span></span> <span data-ttu-id="f4965-110">Tento parametr musí mít hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="f4965-110">This parameter must be 0.</span></span>

`pstrName`   
<span data-ttu-id="f4965-111">mimo Název kvalifikátoru.</span><span class="sxs-lookup"><span data-stu-id="f4965-111">[out] The name of the qualifier.</span></span> <span data-ttu-id="f4965-112">Pokud `null`je tento parametr ignorován; `pstrName` v opačném případě by neměl ukazovat na platnou `BSTR` nebo nevrácenou paměť.</span><span class="sxs-lookup"><span data-stu-id="f4965-112">If `null`, this parameter is ignored; otherwise, `pstrName` should not point to a valid `BSTR` or a memory leak occurs.</span></span> <span data-ttu-id="f4965-113">Pokud hodnota není null, funkce při návratu `BSTR` `WBEM_S_NO_ERROR`vždy přidělí nový.</span><span class="sxs-lookup"><span data-stu-id="f4965-113">If not null, the function always allocates a new `BSTR` when it returns `WBEM_S_NO_ERROR`.</span></span>

`pVal`   
<span data-ttu-id="f4965-114">mimo Pokud je to úspěšné, hodnota kvalifikátoru.</span><span class="sxs-lookup"><span data-stu-id="f4965-114">[out] When successful, the value for the qualifier.</span></span> <span data-ttu-id="f4965-115">Pokud se funkce nezdařila `VARIANT` , odkaz `pVal` na hodnotu není změněn.</span><span class="sxs-lookup"><span data-stu-id="f4965-115">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="f4965-116">Pokud je `null`tento parametr, parametr je ignorován.</span><span class="sxs-lookup"><span data-stu-id="f4965-116">If this parameter is `null`, the parameter is ignored.</span></span>

`plFlavor`   
<span data-ttu-id="f4965-117">mimo Ukazatel na dlouhou hodnotu, který získá charakter kvalifikátoru.</span><span class="sxs-lookup"><span data-stu-id="f4965-117">[out] A pointer to a LONG that receives the qualifier flavor.</span></span> <span data-ttu-id="f4965-118">Pokud nejsou požadovány informace o charakteru, může být `null`tento parametr.</span><span class="sxs-lookup"><span data-stu-id="f4965-118">If flavor information is not desired, this parameter can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="f4965-119">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f4965-119">Return value</span></span>

<span data-ttu-id="f4965-120">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="f4965-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="f4965-121">Konstanta</span><span class="sxs-lookup"><span data-stu-id="f4965-121">Constant</span></span>  |<span data-ttu-id="f4965-122">Value</span><span class="sxs-lookup"><span data-stu-id="f4965-122">Value</span></span>  |<span data-ttu-id="f4965-123">Popis</span><span class="sxs-lookup"><span data-stu-id="f4965-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="f4965-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="f4965-124">0x80041008</span></span> | <span data-ttu-id="f4965-125">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="f4965-125">A parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="f4965-126">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="f4965-126">0x8004101d</span></span> | <span data-ttu-id="f4965-127">Volající nevolal [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="f4965-127">The caller did not call [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="f4965-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="f4965-128">0x80041006</span></span> | <span data-ttu-id="f4965-129">K zahájení nového výčtu není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="f4965-129">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="f4965-130">0x40005</span><span class="sxs-lookup"><span data-stu-id="f4965-130">0x40005</span></span> | <span data-ttu-id="f4965-131">Ve výčtu nezůstanou žádné další kvalifikátory.</span><span class="sxs-lookup"><span data-stu-id="f4965-131">No more qualifiers are left in the enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="f4965-132">0</span><span class="sxs-lookup"><span data-stu-id="f4965-132">0</span></span> | <span data-ttu-id="f4965-133">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="f4965-133">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="f4965-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f4965-134">Remarks</span></span>

<span data-ttu-id="f4965-135">Tato funkce zalomí volání metody [IWbemQualifierSet:: Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) .</span><span class="sxs-lookup"><span data-stu-id="f4965-135">This function wraps a call to the [IWbemQualifierSet::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) method.</span></span>

<span data-ttu-id="f4965-136">Voláním `QualifierSet_Next` funkce opakovaně vydáte výčet všech kvalifikátorů, dokud funkce nevrátí `WBEM_S_NO_MORE_DATA`hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f4965-136">You call the `QualifierSet_Next` function repeatedly to enumerate all the qualifiers until the function return `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="f4965-137">Chcete-li ukončit výčet na začátku, zavolejte funkci [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="f4965-137">To terminate the enumeration early, call the [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) function.</span></span>

<span data-ttu-id="f4965-138">Pořadí kvalifikátorů vrácených během výčtu není definováno.</span><span class="sxs-lookup"><span data-stu-id="f4965-138">The order of the qualifiers returned during the enumeration is undefined.</span></span>

## <a name="requirements"></a><span data-ttu-id="f4965-139">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f4965-139">Requirements</span></span>  
 <span data-ttu-id="f4965-140">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4965-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4965-141">**Hlaviček** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="f4965-141">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="f4965-142">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f4965-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4965-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f4965-143">See also</span></span>

- [<span data-ttu-id="f4965-144">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="f4965-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
