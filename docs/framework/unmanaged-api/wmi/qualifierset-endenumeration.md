---
title: Funkce QualifierSet_EndEnumeration (referenční dokumentace nespravovaného rozhraní API)
description: Funkce QualifierSet_EndEnumeration skončí výčet.
ms.date: 11/06/2017
api_name:
- QualifierSet_EndEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_EndEnumeration
helpviewer_keywords:
- QualifierSet_EndEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be2dfd6bb521dee14afd3728bdd9c446cb779e85
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61598841"
---
# <a name="qualifiersetendenumeration-function"></a><span data-ttu-id="0db49-103">QualifierSet_EndEnumeration – funkce</span><span class="sxs-lookup"><span data-stu-id="0db49-103">QualifierSet_EndEnumeration function</span></span>
<span data-ttu-id="0db49-104">Ukončí výčet začal s voláním [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="0db49-104">Terminates the enumeration begun with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="0db49-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0db49-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_EndEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr
); 
```  

## <a name="parameters"></a><span data-ttu-id="0db49-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0db49-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="0db49-107">[in] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="0db49-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="0db49-108">[in] Ukazatel [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span><span class="sxs-lookup"><span data-stu-id="0db49-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="0db49-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0db49-109">Return value</span></span>

<span data-ttu-id="0db49-110">Následující hodnota vrácená touto funkcí je definována v *WbemCli.h* hlavičkový soubor, nebo můžete definovat ji jako konstantu. ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="0db49-110">The following value returned by this function is defined in the *WbemCli.h* header file, or you can define it as a constant in your code:</span></span>

|<span data-ttu-id="0db49-111">Konstanta</span><span class="sxs-lookup"><span data-stu-id="0db49-111">Constant</span></span>  |<span data-ttu-id="0db49-112">Hodnota</span><span class="sxs-lookup"><span data-stu-id="0db49-112">Value</span></span>  |<span data-ttu-id="0db49-113">Popis</span><span class="sxs-lookup"><span data-stu-id="0db49-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_S_NO_ERROR` | <span data-ttu-id="0db49-114">0</span><span class="sxs-lookup"><span data-stu-id="0db49-114">0</span></span> | <span data-ttu-id="0db49-115">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="0db49-115">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="0db49-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0db49-116">Remarks</span></span>

<span data-ttu-id="0db49-117">Tato funkce zalamuje volání na [IWbemQualifierSet::EndEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration) metody.</span><span class="sxs-lookup"><span data-stu-id="0db49-117">This function wraps a call to the [IWbemQualifierSet::EndEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration) method.</span></span>

<span data-ttu-id="0db49-118">Toto volání je doporučené, ale nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="0db49-118">This call is recommended, but not required.</span></span> <span data-ttu-id="0db49-119">Okamžitě uvolní prostředky přidružené k výčtu.</span><span class="sxs-lookup"><span data-stu-id="0db49-119">It immediately releases resources associated with the enumeration.</span></span>

## <a name="requirements"></a><span data-ttu-id="0db49-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0db49-120">Requirements</span></span>  

<span data-ttu-id="0db49-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0db49-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
<span data-ttu-id="0db49-122">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="0db49-122">**Header:** WMINet_Utils.idl</span></span>  
  
<span data-ttu-id="0db49-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0db49-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0db49-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0db49-124">See also</span></span>

- [<span data-ttu-id="0db49-125">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="0db49-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
