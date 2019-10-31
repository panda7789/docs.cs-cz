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
ms.openlocfilehash: c9c824b0158618848c13183d92f88604460d5099
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141721"
---
# <a name="qualifierset_next-function"></a><span data-ttu-id="ba17d-103">QualifierSet_Next – funkce</span><span class="sxs-lookup"><span data-stu-id="ba17d-103">QualifierSet_Next function</span></span>
<span data-ttu-id="ba17d-104">Načte další kvalifikátor ve výčtu, který začal voláním funkce [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="ba17d-104">Retrieves the next qualifier in an enumeration that started with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>   

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="ba17d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba17d-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="ba17d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ba17d-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="ba17d-107">pro Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="ba17d-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="ba17d-108">pro Ukazatel na instanci [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="ba17d-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`lFlags`   
<span data-ttu-id="ba17d-109">pro Rezervovaný.</span><span class="sxs-lookup"><span data-stu-id="ba17d-109">[in] Reserved.</span></span> <span data-ttu-id="ba17d-110">Tento parametr musí mít hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="ba17d-110">This parameter must be 0.</span></span>

`pstrName`   
<span data-ttu-id="ba17d-111">mimo Název kvalifikátoru.</span><span class="sxs-lookup"><span data-stu-id="ba17d-111">[out] The name of the qualifier.</span></span> <span data-ttu-id="ba17d-112">Pokud `null`, tento parametr je ignorován. v opačném případě by `pstrName` neměla ukazovat na platný `BSTR` nebo dojde k nevrácení paměti.</span><span class="sxs-lookup"><span data-stu-id="ba17d-112">If `null`, this parameter is ignored; otherwise, `pstrName` should not point to a valid `BSTR` or a memory leak occurs.</span></span> <span data-ttu-id="ba17d-113">Pokud hodnota není null, funkce vždy přidělí novou `BSTR`, když vrátí `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="ba17d-113">If not null, the function always allocates a new `BSTR` when it returns `WBEM_S_NO_ERROR`.</span></span>

`pVal`   
<span data-ttu-id="ba17d-114">mimo Pokud je to úspěšné, hodnota kvalifikátoru.</span><span class="sxs-lookup"><span data-stu-id="ba17d-114">[out] When successful, the value for the qualifier.</span></span> <span data-ttu-id="ba17d-115">Pokud se funkce nezdařila, `VARIANT`, na kterou odkazuje `pVal`, se nezmění.</span><span class="sxs-lookup"><span data-stu-id="ba17d-115">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="ba17d-116">Pokud je tento parametr `null`, parametr je ignorován.</span><span class="sxs-lookup"><span data-stu-id="ba17d-116">If this parameter is `null`, the parameter is ignored.</span></span>

`plFlavor`   
<span data-ttu-id="ba17d-117">mimo Ukazatel na dlouhou hodnotu, který získá charakter kvalifikátoru.</span><span class="sxs-lookup"><span data-stu-id="ba17d-117">[out] A pointer to a LONG that receives the qualifier flavor.</span></span> <span data-ttu-id="ba17d-118">Pokud nejsou požadovány informace o charakteru, lze tento parametr `null`.</span><span class="sxs-lookup"><span data-stu-id="ba17d-118">If flavor information is not desired, this parameter can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="ba17d-119">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ba17d-119">Return value</span></span>

<span data-ttu-id="ba17d-120">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="ba17d-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="ba17d-121">Konstanta</span><span class="sxs-lookup"><span data-stu-id="ba17d-121">Constant</span></span>  |<span data-ttu-id="ba17d-122">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ba17d-122">Value</span></span>  |<span data-ttu-id="ba17d-123">Popis</span><span class="sxs-lookup"><span data-stu-id="ba17d-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="ba17d-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="ba17d-124">0x80041008</span></span> | <span data-ttu-id="ba17d-125">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="ba17d-125">A parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="ba17d-126">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="ba17d-126">0x8004101d</span></span> | <span data-ttu-id="ba17d-127">Volající nevolal [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="ba17d-127">The caller did not call [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="ba17d-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="ba17d-128">0x80041006</span></span> | <span data-ttu-id="ba17d-129">K zahájení nového výčtu není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="ba17d-129">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="ba17d-130">0x40005</span><span class="sxs-lookup"><span data-stu-id="ba17d-130">0x40005</span></span> | <span data-ttu-id="ba17d-131">Ve výčtu nezůstanou žádné další kvalifikátory.</span><span class="sxs-lookup"><span data-stu-id="ba17d-131">No more qualifiers are left in the enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="ba17d-132">0,8</span><span class="sxs-lookup"><span data-stu-id="ba17d-132">0</span></span> | <span data-ttu-id="ba17d-133">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="ba17d-133">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="ba17d-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ba17d-134">Remarks</span></span>

<span data-ttu-id="ba17d-135">Tato funkce zalomí volání metody [IWbemQualifierSet:: Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) .</span><span class="sxs-lookup"><span data-stu-id="ba17d-135">This function wraps a call to the [IWbemQualifierSet::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) method.</span></span>

<span data-ttu-id="ba17d-136">Voláním funkce `QualifierSet_Next` opakovaně vydáte výčet všech kvalifikátorů, dokud funkce nevrátí `WBEM_S_NO_MORE_DATA`.</span><span class="sxs-lookup"><span data-stu-id="ba17d-136">You call the `QualifierSet_Next` function repeatedly to enumerate all the qualifiers until the function return `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="ba17d-137">Chcete-li ukončit výčet na začátku, zavolejte funkci [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="ba17d-137">To terminate the enumeration early, call the [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) function.</span></span>

<span data-ttu-id="ba17d-138">Pořadí kvalifikátorů vrácených během výčtu není definováno.</span><span class="sxs-lookup"><span data-stu-id="ba17d-138">The order of the qualifiers returned during the enumeration is undefined.</span></span>

## <a name="requirements"></a><span data-ttu-id="ba17d-139">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ba17d-139">Requirements</span></span>  
 <span data-ttu-id="ba17d-140">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba17d-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba17d-141">**Hlavička:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="ba17d-141">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="ba17d-142">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ba17d-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba17d-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ba17d-143">See also</span></span>

- [<span data-ttu-id="ba17d-144">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="ba17d-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
