---
title: Funkce QualifierSet_Get (referenční dokumentace nespravovaného rozhraní API)
description: Funkce QualifierSet_Get získá s názvem kvalifikátoru.
ms.date: 11/06/2017
api_name:
- QualifierSet_Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Get
helpviewer_keywords:
- QualifierSet_Get function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0dc76a2732bf9c1e4f3a26fa2d045bfbcd837ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61596975"
---
# <a name="qualifiersetget-function"></a><span data-ttu-id="e33c0-103">QualifierSet_Get – funkce</span><span class="sxs-lookup"><span data-stu-id="e33c0-103">QualifierSet_Get function</span></span>
<span data-ttu-id="e33c0-104">Získá zadaný s názvem kvalifikátoru.</span><span class="sxs-lookup"><span data-stu-id="e33c0-104">Gets the specified named qualifier.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="e33c0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e33c0-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_Get (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName,
   [in] LONG                 lFlags,
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor                 
); 
```  

## <a name="parameters"></a><span data-ttu-id="e33c0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e33c0-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="e33c0-107">[in] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="e33c0-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="e33c0-108">[in] Ukazatel [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span><span class="sxs-lookup"><span data-stu-id="e33c0-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`wszName`   
<span data-ttu-id="e33c0-109">[in] Název kvalifikátor, jehož hodnota je požadováno.</span><span class="sxs-lookup"><span data-stu-id="e33c0-109">[in] The name of the qualifier whose value is requested.</span></span>

`lFlags`   
<span data-ttu-id="e33c0-110">[in] Vyhrazená.</span><span class="sxs-lookup"><span data-stu-id="e33c0-110">[in] Reserved.</span></span> <span data-ttu-id="e33c0-111">Tento parametr musí být 0.</span><span class="sxs-lookup"><span data-stu-id="e33c0-111">This parameter must be 0.</span></span>

`pVal`   
<span data-ttu-id="e33c0-112">[out] V případě úspěchu správný typ a hodnota pro kvalifikátor.</span><span class="sxs-lookup"><span data-stu-id="e33c0-112">[out] When successful, the correct type and value for the qualifier.</span></span> <span data-ttu-id="e33c0-113">Pokud funkce selže, `VARIANT` odkazované `pVal` se nezmění.</span><span class="sxs-lookup"><span data-stu-id="e33c0-113">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="e33c0-114">Pokud je tento parametr `null`, tento parametr je ignorován.</span><span class="sxs-lookup"><span data-stu-id="e33c0-114">If this parameter is `null`, the parameter is ignored.</span></span>

`plFlavor`   
<span data-ttu-id="e33c0-115">[out] Ukazatel, který přijímá bity charakter kvalifikátoru pro požadovaný kvalifikátor DLOUHO.</span><span class="sxs-lookup"><span data-stu-id="e33c0-115">[out] A pointer to a LONG that receives the qualifier flavor bits for the requested qualifier.</span></span> <span data-ttu-id="e33c0-116">Pokud není žádoucí informace charakter, tento parametr může být `null`.</span><span class="sxs-lookup"><span data-stu-id="e33c0-116">If flavor information is not desired, this parameter can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="e33c0-117">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e33c0-117">Return value</span></span>

<span data-ttu-id="e33c0-118">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="e33c0-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="e33c0-119">Konstanta</span><span class="sxs-lookup"><span data-stu-id="e33c0-119">Constant</span></span>  |<span data-ttu-id="e33c0-120">Value</span><span class="sxs-lookup"><span data-stu-id="e33c0-120">Value</span></span>  |<span data-ttu-id="e33c0-121">Popis</span><span class="sxs-lookup"><span data-stu-id="e33c0-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="e33c0-122">0x80041008</span><span class="sxs-lookup"><span data-stu-id="e33c0-122">0x80041008</span></span> | <span data-ttu-id="e33c0-123">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="e33c0-123">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="e33c0-124">0x80041002</span><span class="sxs-lookup"><span data-stu-id="e33c0-124">0x80041002</span></span> | <span data-ttu-id="e33c0-125">Zadaný kvalifikátor neexistuje.</span><span class="sxs-lookup"><span data-stu-id="e33c0-125">The specified qualifier does not exist.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="e33c0-126">0</span><span class="sxs-lookup"><span data-stu-id="e33c0-126">0</span></span> | <span data-ttu-id="e33c0-127">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="e33c0-127">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="e33c0-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e33c0-128">Remarks</span></span>

<span data-ttu-id="e33c0-129">Tato funkce zalamuje volání na [IWbemQualifierSet::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) metody.</span><span class="sxs-lookup"><span data-stu-id="e33c0-129">This function wraps a call to the [IWbemQualifierSet::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e33c0-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e33c0-130">Requirements</span></span>  
 <span data-ttu-id="e33c0-131">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e33c0-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e33c0-132">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="e33c0-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="e33c0-133">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e33c0-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e33c0-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e33c0-134">See also</span></span>

- [<span data-ttu-id="e33c0-135">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="e33c0-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
