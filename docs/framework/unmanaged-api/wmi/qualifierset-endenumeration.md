---
title: "Funkce QualifierSet_EndEnumeration (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce QualifierSet_EndEnumeration ukončí výčet."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: QualifierSet_EndEnumeration
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: QualifierSet_EndEnumeration
helpviewer_keywords: QualifierSet_EndEnumeration function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7d8e6bb24eb471d807af2493f82b6be4f644124f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="qualifiersetendenumeration-function"></a><span data-ttu-id="f64c8-103">QualifierSet_EndEnumeration – funkce</span><span class="sxs-lookup"><span data-stu-id="f64c8-103">QualifierSet_EndEnumeration function</span></span>
<span data-ttu-id="f64c8-104">Ukončí výčtu zahájena volání [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="f64c8-104">Terminates the enumeration begun with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="f64c8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f64c8-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_EndEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr
); 
```  

## <a name="parameters"></a><span data-ttu-id="f64c8-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f64c8-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="f64c8-107">[v] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="f64c8-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="f64c8-108">[v] Ukazatel na [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="f64c8-108">[in] A pointer to an [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="f64c8-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f64c8-109">Return value</span></span>

<span data-ttu-id="f64c8-110">Následující hodnota vrácená touto funkcí je definována v *WbemCli.h* soubor hlaviček, případně je možné definovat ji jako konstanta ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="f64c8-110">The following value returned by this function is defined in the *WbemCli.h* header file, or you can define it as a constant in your code:</span></span>

|<span data-ttu-id="f64c8-111">Konstanta</span><span class="sxs-lookup"><span data-stu-id="f64c8-111">Constant</span></span>  |<span data-ttu-id="f64c8-112">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f64c8-112">Value</span></span>  |<span data-ttu-id="f64c8-113">Popis</span><span class="sxs-lookup"><span data-stu-id="f64c8-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_S_NO_ERROR` | <span data-ttu-id="f64c8-114">0</span><span class="sxs-lookup"><span data-stu-id="f64c8-114">0</span></span> | <span data-ttu-id="f64c8-115">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="f64c8-115">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="f64c8-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f64c8-116">Remarks</span></span>

<span data-ttu-id="f64c8-117">Tato funkce zabalí volání [IWbemQualifierSet::EndEnumeration](https://msdn.microsoft.com/library/aa391865(v=vs.85).aspx) metoda.</span><span class="sxs-lookup"><span data-stu-id="f64c8-117">This function wraps a call to the [IWbemQualifierSet::EndEnumeration](https://msdn.microsoft.com/library/aa391865(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="f64c8-118">Toto volání je doporučená, ale není povinný.</span><span class="sxs-lookup"><span data-stu-id="f64c8-118">This call is recommended, but not required.</span></span> <span data-ttu-id="f64c8-119">Uvolní okamžitě prostředky přidružené k výčtu.</span><span class="sxs-lookup"><span data-stu-id="f64c8-119">It immediately releases resources associated with the enumeration.</span></span>

## <a name="requirements"></a><span data-ttu-id="f64c8-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f64c8-120">Requirements</span></span>  

<span data-ttu-id="f64c8-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f64c8-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
<span data-ttu-id="f64c8-122">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="f64c8-122">**Header:** WMINet_Utils.idl</span></span>  
  
<span data-ttu-id="f64c8-123">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f64c8-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f64c8-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="f64c8-124">See also</span></span>  
[<span data-ttu-id="f64c8-125">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="f64c8-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
