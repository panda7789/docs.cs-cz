---
title: "Funkce QualifierSet_Get (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce QualifierSet_Get získá kvalifikátor s názvem."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: QualifierSet_Get
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: QualifierSet_Get
helpviewer_keywords: QualifierSet_Get function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: aaf5de5b8e16ee2f96c7bc29dbb09f93298dd185
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2017
---
# <a name="qualifiersetget-function"></a><span data-ttu-id="c5b7b-103">QualifierSet_Get – funkce</span><span class="sxs-lookup"><span data-stu-id="c5b7b-103">QualifierSet_Get function</span></span>
<span data-ttu-id="c5b7b-104">Získá zadaný s názvem kvalifikátor.</span><span class="sxs-lookup"><span data-stu-id="c5b7b-104">Gets the specified named qualifier.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="c5b7b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5b7b-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="c5b7b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c5b7b-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="c5b7b-107">[v] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="c5b7b-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="c5b7b-108">[v] Ukazatel na [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="c5b7b-108">[in] A pointer to an [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span></span>

`wszName`   
<span data-ttu-id="c5b7b-109">[v] Název kvalifikátor, jehož hodnota je vyžadována.</span><span class="sxs-lookup"><span data-stu-id="c5b7b-109">[in] The name of the qualifier whose value is requested.</span></span>

`lFlags`   
<span data-ttu-id="c5b7b-110">[v] Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="c5b7b-110">[in] Reserved.</span></span> <span data-ttu-id="c5b7b-111">Tento parametr musí být 0.</span><span class="sxs-lookup"><span data-stu-id="c5b7b-111">This parameter must be 0.</span></span>

`pVal`   
<span data-ttu-id="c5b7b-112">[out] Po úspěšné, správný typ a hodnotu pro kvalifikátor.</span><span class="sxs-lookup"><span data-stu-id="c5b7b-112">[out] When successful, the correct type and value for the qualifier.</span></span> <span data-ttu-id="c5b7b-113">Pokud se funkce nezdaří, `VARIANT` na kterou odkazuje `pVal` se nemění.</span><span class="sxs-lookup"><span data-stu-id="c5b7b-113">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="c5b7b-114">Pokud tento parametr je `null`, parametr je ignorován.</span><span class="sxs-lookup"><span data-stu-id="c5b7b-114">If this parameter is `null`, the parameter is ignored.</span></span>

`plFlavor`   
<span data-ttu-id="c5b7b-115">[out] Ukazatel na typ LONG, která přijímá bitů příchuť kvalifikátor pro požadovaný kvalifikátor.</span><span class="sxs-lookup"><span data-stu-id="c5b7b-115">[out] A pointer to a LONG that receives the qualifier flavor bits for the requested qualifier.</span></span> <span data-ttu-id="c5b7b-116">V případě potřeby příchuť informace není tento parametr může být `null`.</span><span class="sxs-lookup"><span data-stu-id="c5b7b-116">If flavor information is not desired, this parameter can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="c5b7b-117">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c5b7b-117">Return value</span></span>

<span data-ttu-id="c5b7b-118">Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="c5b7b-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="c5b7b-119">Konstanta</span><span class="sxs-lookup"><span data-stu-id="c5b7b-119">Constant</span></span>  |<span data-ttu-id="c5b7b-120">Hodnota</span><span class="sxs-lookup"><span data-stu-id="c5b7b-120">Value</span></span>  |<span data-ttu-id="c5b7b-121">Popis</span><span class="sxs-lookup"><span data-stu-id="c5b7b-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="c5b7b-122">0x80041008</span><span class="sxs-lookup"><span data-stu-id="c5b7b-122">0x80041008</span></span> | <span data-ttu-id="c5b7b-123">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="c5b7b-123">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="c5b7b-124">0x80041002</span><span class="sxs-lookup"><span data-stu-id="c5b7b-124">0x80041002</span></span> | <span data-ttu-id="c5b7b-125">Zadaný kvalifikátor neexistuje.</span><span class="sxs-lookup"><span data-stu-id="c5b7b-125">The specified qualifier does not exist.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="c5b7b-126">0</span><span class="sxs-lookup"><span data-stu-id="c5b7b-126">0</span></span> | <span data-ttu-id="c5b7b-127">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="c5b7b-127">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="c5b7b-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c5b7b-128">Remarks</span></span>

<span data-ttu-id="c5b7b-129">Tato funkce zabalí volání [IWbemQualifierSet::Get](https://msdn.microsoft.com/library/aa391867(v=vs.85).aspx) metoda.</span><span class="sxs-lookup"><span data-stu-id="c5b7b-129">This function wraps a call to the [IWbemQualifierSet::Get](https://msdn.microsoft.com/library/aa391867(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c5b7b-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c5b7b-130">Requirements</span></span>  
 <span data-ttu-id="c5b7b-131">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5b7b-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5b7b-132">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="c5b7b-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="c5b7b-133">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c5b7b-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5b7b-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="c5b7b-134">See also</span></span>  
[<span data-ttu-id="c5b7b-135">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="c5b7b-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
