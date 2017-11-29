---
title: "Funkce EndEnumeration – funkce (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce funkce EndEnumeration ukončí výčet."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: EndEnumeration
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: EndEnumeration
helpviewer_keywords: EndEnumeration function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 043fce26870e5af2850b9f2e91e7e97c7bee6c90
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2017
---
# <a name="endenumeration-function"></a><span data-ttu-id="5d080-103">Funkce EndEnumeration – funkce</span><span class="sxs-lookup"><span data-stu-id="5d080-103">EndEnumeration function</span></span>
<span data-ttu-id="5d080-104">Ukončí v sekvenci výčtu začít s volání [funkce BeginEnumeration funkce](beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="5d080-104">Terminates an enumeration sequence started with a call to the [BeginEnumeration function](beginenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="5d080-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5d080-105">Syntax</span></span>  
  
```  
HRESULT EndEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr 
); 
```  

## <a name="parameters"></a><span data-ttu-id="5d080-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5d080-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="5d080-107">[v] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="5d080-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="5d080-108">[v] Ukazatel na [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="5d080-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>


## <a name="return-value"></a><span data-ttu-id="5d080-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5d080-109">Return value</span></span>

<span data-ttu-id="5d080-110">Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="5d080-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="5d080-111">Konstanta</span><span class="sxs-lookup"><span data-stu-id="5d080-111">Constant</span></span>  |<span data-ttu-id="5d080-112">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5d080-112">Value</span></span>  |<span data-ttu-id="5d080-113">Popis</span><span class="sxs-lookup"><span data-stu-id="5d080-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="5d080-114">0x80041001</span><span class="sxs-lookup"><span data-stu-id="5d080-114">0x80041001</span></span> | <span data-ttu-id="5d080-115">Došlo k obecné chybě.</span><span class="sxs-lookup"><span data-stu-id="5d080-115">There has been a general failure.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="5d080-116">0</span><span class="sxs-lookup"><span data-stu-id="5d080-116">0</span></span> | <span data-ttu-id="5d080-117">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="5d080-117">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="5d080-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5d080-118">Remarks</span></span>

<span data-ttu-id="5d080-119">Tato funkce zabalí volání [IWbemClassObject::EndEnumeration](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) metoda.</span><span class="sxs-lookup"><span data-stu-id="5d080-119">This function wraps a call to the [IWbemClassObject::EndEnumeration](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) method.</span></span>

<span data-ttu-id="5d080-120">Volání `EndEnumeration` funkce se nevyžaduje, ale doporučuje se, protože se uvolní prostředky přidružené k výčtu.</span><span class="sxs-lookup"><span data-stu-id="5d080-120">A call to the `EndEnumeration` function is not required, but it is recommended because it releases resources associated with the enumeration.</span></span> <span data-ttu-id="5d080-121">Resoruces však jsou navrácena automaticky při spuštění další výčtu nebo uvolnění objektu.</span><span class="sxs-lookup"><span data-stu-id="5d080-121">However, the resoruces are deallocated automatically when the next enumeration is started or the object is released.</span></span>

## <a name="requirements"></a><span data-ttu-id="5d080-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5d080-122">Requirements</span></span>  
 <span data-ttu-id="5d080-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d080-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d080-124">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="5d080-124">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="5d080-125">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5d080-125">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d080-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="5d080-126">See also</span></span>  
[<span data-ttu-id="5d080-127">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="5d080-127">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
