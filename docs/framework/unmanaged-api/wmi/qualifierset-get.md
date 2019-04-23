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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59181087"
---
# <a name="qualifiersetget-function"></a><span data-ttu-id="e7900-103">QualifierSet_Get – funkce</span><span class="sxs-lookup"><span data-stu-id="e7900-103">QualifierSet_Get function</span></span>
<span data-ttu-id="e7900-104">Získá zadaný s názvem kvalifikátoru.</span><span class="sxs-lookup"><span data-stu-id="e7900-104">Gets the specified named qualifier.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="e7900-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7900-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="e7900-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e7900-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="e7900-107">[in] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="e7900-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="e7900-108">[in] Ukazatel [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span><span class="sxs-lookup"><span data-stu-id="e7900-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`wszName`   
<span data-ttu-id="e7900-109">[in] Název kvalifikátor, jehož hodnota je požadováno.</span><span class="sxs-lookup"><span data-stu-id="e7900-109">[in] The name of the qualifier whose value is requested.</span></span>

`lFlags`   
<span data-ttu-id="e7900-110">[in] Vyhrazená.</span><span class="sxs-lookup"><span data-stu-id="e7900-110">[in] Reserved.</span></span> <span data-ttu-id="e7900-111">Tento parametr musí být 0.</span><span class="sxs-lookup"><span data-stu-id="e7900-111">This parameter must be 0.</span></span>

`pVal`   
<span data-ttu-id="e7900-112">[out] V případě úspěchu správný typ a hodnota pro kvalifikátor.</span><span class="sxs-lookup"><span data-stu-id="e7900-112">[out] When successful, the correct type and value for the qualifier.</span></span> <span data-ttu-id="e7900-113">Pokud funkce selže, `VARIANT` odkazované `pVal` se nezmění.</span><span class="sxs-lookup"><span data-stu-id="e7900-113">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="e7900-114">Pokud je tento parametr `null`, tento parametr je ignorován.</span><span class="sxs-lookup"><span data-stu-id="e7900-114">If this parameter is `null`, the parameter is ignored.</span></span>

`plFlavor`   
<span data-ttu-id="e7900-115">[out] Ukazatel, který přijímá bity charakter kvalifikátoru pro požadovaný kvalifikátor DLOUHO.</span><span class="sxs-lookup"><span data-stu-id="e7900-115">[out] A pointer to a LONG that receives the qualifier flavor bits for the requested qualifier.</span></span> <span data-ttu-id="e7900-116">Pokud není žádoucí informace charakter, tento parametr může být `null`.</span><span class="sxs-lookup"><span data-stu-id="e7900-116">If flavor information is not desired, this parameter can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="e7900-117">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e7900-117">Return value</span></span>

<span data-ttu-id="e7900-118">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="e7900-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="e7900-119">Konstanta</span><span class="sxs-lookup"><span data-stu-id="e7900-119">Constant</span></span>  |<span data-ttu-id="e7900-120">Value</span><span class="sxs-lookup"><span data-stu-id="e7900-120">Value</span></span>  |<span data-ttu-id="e7900-121">Popis</span><span class="sxs-lookup"><span data-stu-id="e7900-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="e7900-122">0x80041008</span><span class="sxs-lookup"><span data-stu-id="e7900-122">0x80041008</span></span> | <span data-ttu-id="e7900-123">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="e7900-123">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="e7900-124">0x80041002</span><span class="sxs-lookup"><span data-stu-id="e7900-124">0x80041002</span></span> | <span data-ttu-id="e7900-125">Zadaný kvalifikátor neexistuje.</span><span class="sxs-lookup"><span data-stu-id="e7900-125">The specified qualifier does not exist.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="e7900-126">0</span><span class="sxs-lookup"><span data-stu-id="e7900-126">0</span></span> | <span data-ttu-id="e7900-127">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="e7900-127">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="e7900-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e7900-128">Remarks</span></span>

<span data-ttu-id="e7900-129">Tato funkce zalamuje volání na [IWbemQualifierSet::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) metody.</span><span class="sxs-lookup"><span data-stu-id="e7900-129">This function wraps a call to the [IWbemQualifierSet::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e7900-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e7900-130">Requirements</span></span>  
 <span data-ttu-id="e7900-131">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7900-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7900-132">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="e7900-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="e7900-133">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e7900-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7900-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e7900-134">See also</span></span>

- [<span data-ttu-id="e7900-135">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="e7900-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
