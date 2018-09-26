---
title: Funkce QualifierSet_Delete (referenční dokumentace nespravovaného rozhraní API)
description: Funkce QualifierSet_Delete odstraní kvalifikátor podle názvu.
ms.date: 11/06/2017
api_name:
- QualifierSet_Delete
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Delete
helpviewer_keywords:
- QualifierSet_Delete function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ca4cc9fb65d1a4bd8713f969bbda5551ce5a2e2
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47090172"
---
# <a name="qualifiersetdelete-function"></a><span data-ttu-id="71367-103">QualifierSet_Delete – funkce</span><span class="sxs-lookup"><span data-stu-id="71367-103">QualifierSet_Delete function</span></span>
<span data-ttu-id="71367-104">Odstraní zadaný kvalifikátor podle názvu.</span><span class="sxs-lookup"><span data-stu-id="71367-104">Deletes a specified qualifier by name.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="71367-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="71367-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName
); 
```  

## <a name="parameters"></a><span data-ttu-id="71367-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="71367-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="71367-107">[in] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="71367-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="71367-108">[in] Ukazatel [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span><span class="sxs-lookup"><span data-stu-id="71367-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`wszName`   
<span data-ttu-id="71367-109">[in] Název kvalifikátor odstranit.</span><span class="sxs-lookup"><span data-stu-id="71367-109">[in] The name of the qualifier to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="71367-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="71367-110">Return value</span></span>

<span data-ttu-id="71367-111">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="71367-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="71367-112">Konstanta</span><span class="sxs-lookup"><span data-stu-id="71367-112">Constant</span></span>  |<span data-ttu-id="71367-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="71367-113">Value</span></span>  |<span data-ttu-id="71367-114">Popis</span><span class="sxs-lookup"><span data-stu-id="71367-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="71367-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="71367-115">0x80041008</span></span> | <span data-ttu-id="71367-116">`wszName` Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="71367-116">The `wszName` parameter is not valid.</span></span> |
|`WBEM_E_INVALID_OPERATION` | <span data-ttu-id="71367-117">0x80041016</span><span class="sxs-lookup"><span data-stu-id="71367-117">0x80041016</span></span> | <span data-ttu-id="71367-118">Odstraňuje se tento kvalifikátor je neplatný.</span><span class="sxs-lookup"><span data-stu-id="71367-118">Deleting this qualifier is illegal.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="71367-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="71367-119">0x80041002</span></span> | <span data-ttu-id="71367-120">Zadaný kvalifikátor se nenašel.</span><span class="sxs-lookup"><span data-stu-id="71367-120">The specified qualifier was not found.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="71367-121">0</span><span class="sxs-lookup"><span data-stu-id="71367-121">0</span></span> | <span data-ttu-id="71367-122">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="71367-122">The function call was successful.</span></span>  |
| `WBEM_S_RESET_TO_DEFAULT` | <span data-ttu-id="71367-123">0x40002</span><span class="sxs-lookup"><span data-stu-id="71367-123">0x40002</span></span> | <span data-ttu-id="71367-124">Místní přepsání byl odstraněn a oboru došlo k obnovení původního kvalifikátor z nadřazeného objektu.</span><span class="sxs-lookup"><span data-stu-id="71367-124">The local override was deleted and the original qualifier from the parent object has resumed scope.</span></span> |

## <a name="remarks"></a><span data-ttu-id="71367-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="71367-125">Remarks</span></span>

<span data-ttu-id="71367-126">Tato funkce zalamuje volání na [IWbemQualifierSet::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) metody.</span><span class="sxs-lookup"><span data-stu-id="71367-126">This function wraps a call to the [IWbemQualifierSet::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) method.</span></span>

<span data-ttu-id="71367-127">Z důvodu pravidla pro šíření kvalifikátor zejména kvalifikátor může byly zděděné z jiného objektu a pouze přepsání v aktuální třídě nebo instanci.</span><span class="sxs-lookup"><span data-stu-id="71367-127">Due to qualifier propagation rules, a particular qualifier may have been inherited from another object and merely overridden in the current class or instance.</span></span> <span data-ttu-id="71367-128">V takovém případě `QualifierSet_Delete` způsob, obnovíte na původní hodnotu zděděného kvalifikátor.</span><span class="sxs-lookup"><span data-stu-id="71367-128">In this case, the `QualifierSet_Delete` method resets the qualifier to its original inherited value.</span></span> <span data-ttu-id="71367-129">V tomto případě vrátí stavový kód `WBEM_S_RESET_TO_DEFAULT`.</span><span class="sxs-lookup"><span data-stu-id="71367-129">The function in this case returns the status code `WBEM_S_RESET_TO_DEFAULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="71367-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="71367-130">Requirements</span></span>  
 <span data-ttu-id="71367-131">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71367-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71367-132">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="71367-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="71367-133">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="71367-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71367-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="71367-134">See also</span></span>  
[<span data-ttu-id="71367-135">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="71367-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
