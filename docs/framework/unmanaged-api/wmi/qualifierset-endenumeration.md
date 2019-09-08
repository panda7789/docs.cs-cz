---
title: QualifierSet_EndEnumeration – funkce (Reference nespravovaného rozhraní API)
description: Funkce QualifierSet_EndEnumeration ukončí výčet.
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
ms.openlocfilehash: 2c5a817174ec4c4e4407c19bb1d6d2d852d86dd2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798315"
---
# <a name="qualifierset_endenumeration-function"></a><span data-ttu-id="3d88e-103">QualifierSet_EndEnumeration – funkce</span><span class="sxs-lookup"><span data-stu-id="3d88e-103">QualifierSet_EndEnumeration function</span></span>
<span data-ttu-id="3d88e-104">Ukončí výčet zahájený voláním funkce [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="3d88e-104">Terminates the enumeration begun with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="3d88e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d88e-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_EndEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr
); 
```  

## <a name="parameters"></a><span data-ttu-id="3d88e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3d88e-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="3d88e-107">pro Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="3d88e-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="3d88e-108">pro Ukazatel na instanci [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="3d88e-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="3d88e-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3d88e-109">Return value</span></span>

<span data-ttu-id="3d88e-110">Následující hodnota vrácená touto funkcí je definována v souboru hlaviček *WbemCli. h* nebo ji můžete definovat jako konstantu v kódu:</span><span class="sxs-lookup"><span data-stu-id="3d88e-110">The following value returned by this function is defined in the *WbemCli.h* header file, or you can define it as a constant in your code:</span></span>

|<span data-ttu-id="3d88e-111">Konstanta</span><span class="sxs-lookup"><span data-stu-id="3d88e-111">Constant</span></span>  |<span data-ttu-id="3d88e-112">Value</span><span class="sxs-lookup"><span data-stu-id="3d88e-112">Value</span></span>  |<span data-ttu-id="3d88e-113">Popis</span><span class="sxs-lookup"><span data-stu-id="3d88e-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_S_NO_ERROR` | <span data-ttu-id="3d88e-114">0</span><span class="sxs-lookup"><span data-stu-id="3d88e-114">0</span></span> | <span data-ttu-id="3d88e-115">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="3d88e-115">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="3d88e-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3d88e-116">Remarks</span></span>

<span data-ttu-id="3d88e-117">Tato funkce zalomí volání metody [IWbemQualifierSet:: funkce EndEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration) .</span><span class="sxs-lookup"><span data-stu-id="3d88e-117">This function wraps a call to the [IWbemQualifierSet::EndEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration) method.</span></span>

<span data-ttu-id="3d88e-118">Toto volání se doporučuje, ale není povinné.</span><span class="sxs-lookup"><span data-stu-id="3d88e-118">This call is recommended, but not required.</span></span> <span data-ttu-id="3d88e-119">Okamžitě uvolňuje prostředky spojené s výčtem.</span><span class="sxs-lookup"><span data-stu-id="3d88e-119">It immediately releases resources associated with the enumeration.</span></span>

## <a name="requirements"></a><span data-ttu-id="3d88e-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3d88e-120">Requirements</span></span>  

<span data-ttu-id="3d88e-121">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d88e-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
<span data-ttu-id="3d88e-122">**Hlaviček** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="3d88e-122">**Header:** WMINet_Utils.idl</span></span>  
  
<span data-ttu-id="3d88e-123">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3d88e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d88e-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3d88e-124">See also</span></span>

- [<span data-ttu-id="3d88e-125">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="3d88e-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
