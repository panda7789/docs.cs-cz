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
ms.openlocfilehash: 82627fa416f71e123ed2c03bae4584e4433310eb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127280"
---
# <a name="qualifierset_endenumeration-function"></a><span data-ttu-id="75f37-103">QualifierSet_EndEnumeration – funkce</span><span class="sxs-lookup"><span data-stu-id="75f37-103">QualifierSet_EndEnumeration function</span></span>
<span data-ttu-id="75f37-104">Ukončí výčet zahájený voláním funkce [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="75f37-104">Terminates the enumeration begun with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="75f37-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="75f37-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_EndEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr
); 
```  

## <a name="parameters"></a><span data-ttu-id="75f37-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="75f37-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="75f37-107">pro Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="75f37-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="75f37-108">pro Ukazatel na instanci [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="75f37-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="75f37-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="75f37-109">Return value</span></span>

<span data-ttu-id="75f37-110">Následující hodnota vrácená touto funkcí je definována v souboru hlaviček *WbemCli. h* nebo ji můžete definovat jako konstantu v kódu:</span><span class="sxs-lookup"><span data-stu-id="75f37-110">The following value returned by this function is defined in the *WbemCli.h* header file, or you can define it as a constant in your code:</span></span>

|<span data-ttu-id="75f37-111">Konstanta</span><span class="sxs-lookup"><span data-stu-id="75f37-111">Constant</span></span>  |<span data-ttu-id="75f37-112">Hodnota</span><span class="sxs-lookup"><span data-stu-id="75f37-112">Value</span></span>  |<span data-ttu-id="75f37-113">Popis</span><span class="sxs-lookup"><span data-stu-id="75f37-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_S_NO_ERROR` | <span data-ttu-id="75f37-114">0,8</span><span class="sxs-lookup"><span data-stu-id="75f37-114">0</span></span> | <span data-ttu-id="75f37-115">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="75f37-115">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="75f37-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="75f37-116">Remarks</span></span>

<span data-ttu-id="75f37-117">Tato funkce zalomí volání metody [IWbemQualifierSet:: funkce EndEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration) .</span><span class="sxs-lookup"><span data-stu-id="75f37-117">This function wraps a call to the [IWbemQualifierSet::EndEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration) method.</span></span>

<span data-ttu-id="75f37-118">Toto volání se doporučuje, ale není povinné.</span><span class="sxs-lookup"><span data-stu-id="75f37-118">This call is recommended, but not required.</span></span> <span data-ttu-id="75f37-119">Okamžitě uvolňuje prostředky spojené s výčtem.</span><span class="sxs-lookup"><span data-stu-id="75f37-119">It immediately releases resources associated with the enumeration.</span></span>

## <a name="requirements"></a><span data-ttu-id="75f37-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="75f37-120">Requirements</span></span>  

<span data-ttu-id="75f37-121">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75f37-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
<span data-ttu-id="75f37-122">**Hlavička:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="75f37-122">**Header:** WMINet_Utils.idl</span></span>  
  
<span data-ttu-id="75f37-123">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="75f37-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75f37-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="75f37-124">See also</span></span>

- [<span data-ttu-id="75f37-125">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="75f37-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
