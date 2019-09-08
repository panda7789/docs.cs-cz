---
title: QualifierSet_Delete – funkce (Reference nespravovaného rozhraní API)
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
ms.openlocfilehash: 4bc26a16650a5beecc17898e0421e79536713deb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798335"
---
# <a name="qualifierset_delete-function"></a><span data-ttu-id="f10d4-103">QualifierSet_Delete – funkce</span><span class="sxs-lookup"><span data-stu-id="f10d4-103">QualifierSet_Delete function</span></span>
<span data-ttu-id="f10d4-104">Odstraní zadaný kvalifikátor podle názvu.</span><span class="sxs-lookup"><span data-stu-id="f10d4-104">Deletes a specified qualifier by name.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="f10d4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f10d4-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName
); 
```  

## <a name="parameters"></a><span data-ttu-id="f10d4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f10d4-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="f10d4-107">pro Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="f10d4-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="f10d4-108">pro Ukazatel na instanci [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="f10d4-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`wszName`   
<span data-ttu-id="f10d4-109">pro Název kvalifikátoru, který se má odstranit</span><span class="sxs-lookup"><span data-stu-id="f10d4-109">[in] The name of the qualifier to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="f10d4-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f10d4-110">Return value</span></span>

<span data-ttu-id="f10d4-111">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="f10d4-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="f10d4-112">Konstanta</span><span class="sxs-lookup"><span data-stu-id="f10d4-112">Constant</span></span>  |<span data-ttu-id="f10d4-113">Value</span><span class="sxs-lookup"><span data-stu-id="f10d4-113">Value</span></span>  |<span data-ttu-id="f10d4-114">Popis</span><span class="sxs-lookup"><span data-stu-id="f10d4-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="f10d4-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="f10d4-115">0x80041008</span></span> | <span data-ttu-id="f10d4-116">`wszName` Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="f10d4-116">The `wszName` parameter is not valid.</span></span> |
|`WBEM_E_INVALID_OPERATION` | <span data-ttu-id="f10d4-117">0x80041016</span><span class="sxs-lookup"><span data-stu-id="f10d4-117">0x80041016</span></span> | <span data-ttu-id="f10d4-118">Odstranění tohoto kvalifikátoru je neplatné.</span><span class="sxs-lookup"><span data-stu-id="f10d4-118">Deleting this qualifier is illegal.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="f10d4-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="f10d4-119">0x80041002</span></span> | <span data-ttu-id="f10d4-120">Zadaný kvalifikátor nebyl nalezen.</span><span class="sxs-lookup"><span data-stu-id="f10d4-120">The specified qualifier was not found.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="f10d4-121">0</span><span class="sxs-lookup"><span data-stu-id="f10d4-121">0</span></span> | <span data-ttu-id="f10d4-122">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="f10d4-122">The function call was successful.</span></span>  |
| `WBEM_S_RESET_TO_DEFAULT` | <span data-ttu-id="f10d4-123">0x40002</span><span class="sxs-lookup"><span data-stu-id="f10d4-123">0x40002</span></span> | <span data-ttu-id="f10d4-124">Místní přepsání bylo odstraněno a původní kvalifikátor z nadřazeného objektu má obnovený rozsah.</span><span class="sxs-lookup"><span data-stu-id="f10d4-124">The local override was deleted and the original qualifier from the parent object has resumed scope.</span></span> |

## <a name="remarks"></a><span data-ttu-id="f10d4-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f10d4-125">Remarks</span></span>

<span data-ttu-id="f10d4-126">Tato funkce zalomí volání metody [IWbemQualifierSet::D dstranit](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) .</span><span class="sxs-lookup"><span data-stu-id="f10d4-126">This function wraps a call to the [IWbemQualifierSet::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) method.</span></span>

<span data-ttu-id="f10d4-127">Z důvodu pravidel šíření kvalifikátoru mohl být určitý kvalifikátor zděděný z jiného objektu a pouze přepsán v aktuální třídě nebo instanci.</span><span class="sxs-lookup"><span data-stu-id="f10d4-127">Due to qualifier propagation rules, a particular qualifier may have been inherited from another object and merely overridden in the current class or instance.</span></span> <span data-ttu-id="f10d4-128">V tomto případě `QualifierSet_Delete` metoda obnoví kvalifikátor na původní zděděnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f10d4-128">In this case, the `QualifierSet_Delete` method resets the qualifier to its original inherited value.</span></span> <span data-ttu-id="f10d4-129">Funkce v tomto případě vrátí stavový kód `WBEM_S_RESET_TO_DEFAULT`.</span><span class="sxs-lookup"><span data-stu-id="f10d4-129">The function in this case returns the status code `WBEM_S_RESET_TO_DEFAULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="f10d4-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f10d4-130">Requirements</span></span>  
 <span data-ttu-id="f10d4-131">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f10d4-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f10d4-132">**Hlaviček** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="f10d4-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="f10d4-133">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f10d4-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f10d4-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f10d4-134">See also</span></span>

- [<span data-ttu-id="f10d4-135">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="f10d4-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
