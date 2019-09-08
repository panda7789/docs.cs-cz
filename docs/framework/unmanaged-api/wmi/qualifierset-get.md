---
title: QualifierSet_Get – funkce (Reference nespravovaného rozhraní API)
description: Funkce QualifierSet_Get Získá pojmenovaný kvalifikátor.
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
ms.openlocfilehash: 751694985248346187eff016ef7a4a8054cb1212
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798311"
---
# <a name="qualifierset_get-function"></a><span data-ttu-id="e6609-103">QualifierSet_Get – funkce</span><span class="sxs-lookup"><span data-stu-id="e6609-103">QualifierSet_Get function</span></span>
<span data-ttu-id="e6609-104">Získá zadaný pojmenovaný kvalifikátor.</span><span class="sxs-lookup"><span data-stu-id="e6609-104">Gets the specified named qualifier.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="e6609-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6609-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_Get (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName,
   [in] LONG                 lFlags,
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor                 
); 
```  

## <a name="parameters"></a><span data-ttu-id="e6609-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e6609-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="e6609-107">pro Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="e6609-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="e6609-108">pro Ukazatel na instanci [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="e6609-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`wszName`   
<span data-ttu-id="e6609-109">pro Název kvalifikátoru, jehož hodnota je požadována.</span><span class="sxs-lookup"><span data-stu-id="e6609-109">[in] The name of the qualifier whose value is requested.</span></span>

`lFlags`   
<span data-ttu-id="e6609-110">pro Rezervovaný.</span><span class="sxs-lookup"><span data-stu-id="e6609-110">[in] Reserved.</span></span> <span data-ttu-id="e6609-111">Tento parametr musí mít hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="e6609-111">This parameter must be 0.</span></span>

`pVal`   
<span data-ttu-id="e6609-112">mimo Pokud je to úspěšné, správný typ a hodnotu kvalifikátoru.</span><span class="sxs-lookup"><span data-stu-id="e6609-112">[out] When successful, the correct type and value for the qualifier.</span></span> <span data-ttu-id="e6609-113">Pokud se funkce nezdařila `VARIANT` , odkaz `pVal` na hodnotu není změněn.</span><span class="sxs-lookup"><span data-stu-id="e6609-113">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="e6609-114">Pokud je `null`tento parametr, parametr je ignorován.</span><span class="sxs-lookup"><span data-stu-id="e6609-114">If this parameter is `null`, the parameter is ignored.</span></span>

`plFlavor`   
<span data-ttu-id="e6609-115">mimo Ukazatel na dlouhou dobu, který obdrží kvalifikátor charakteru pro požadovaný kvalifikátor.</span><span class="sxs-lookup"><span data-stu-id="e6609-115">[out] A pointer to a LONG that receives the qualifier flavor bits for the requested qualifier.</span></span> <span data-ttu-id="e6609-116">Pokud nejsou požadovány informace o charakteru, může být `null`tento parametr.</span><span class="sxs-lookup"><span data-stu-id="e6609-116">If flavor information is not desired, this parameter can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="e6609-117">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e6609-117">Return value</span></span>

<span data-ttu-id="e6609-118">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="e6609-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="e6609-119">Konstanta</span><span class="sxs-lookup"><span data-stu-id="e6609-119">Constant</span></span>  |<span data-ttu-id="e6609-120">Value</span><span class="sxs-lookup"><span data-stu-id="e6609-120">Value</span></span>  |<span data-ttu-id="e6609-121">Popis</span><span class="sxs-lookup"><span data-stu-id="e6609-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="e6609-122">0x80041008</span><span class="sxs-lookup"><span data-stu-id="e6609-122">0x80041008</span></span> | <span data-ttu-id="e6609-123">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="e6609-123">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="e6609-124">0x80041002</span><span class="sxs-lookup"><span data-stu-id="e6609-124">0x80041002</span></span> | <span data-ttu-id="e6609-125">Zadaný kvalifikátor neexistuje.</span><span class="sxs-lookup"><span data-stu-id="e6609-125">The specified qualifier does not exist.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="e6609-126">0</span><span class="sxs-lookup"><span data-stu-id="e6609-126">0</span></span> | <span data-ttu-id="e6609-127">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="e6609-127">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="e6609-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e6609-128">Remarks</span></span>

<span data-ttu-id="e6609-129">Tato funkce zalomí volání metody [IWbemQualifierSet:: Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) .</span><span class="sxs-lookup"><span data-stu-id="e6609-129">This function wraps a call to the [IWbemQualifierSet::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e6609-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e6609-130">Requirements</span></span>  
 <span data-ttu-id="e6609-131">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6609-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6609-132">**Hlaviček** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="e6609-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="e6609-133">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e6609-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6609-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e6609-134">See also</span></span>

- [<span data-ttu-id="e6609-135">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="e6609-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
