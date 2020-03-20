---
title: QualifierSet_EndEnumeration funkce (Nespravovaný odkaz na rozhraní API)
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
ms.openlocfilehash: c606580ff2e02c5659c14b134b1a17a65651952b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176744"
---
# <a name="qualifierset_endenumeration-function"></a><span data-ttu-id="ab2b8-103">QualifierSet_EndEnumeration funkce</span><span class="sxs-lookup"><span data-stu-id="ab2b8-103">QualifierSet_EndEnumeration function</span></span>
<span data-ttu-id="ab2b8-104">Ukončí výčet, který byl zahájen voláním [funkce QualifierSet_BeginEnumeration.](qualifierset-beginenumeration.md)</span><span class="sxs-lookup"><span data-stu-id="ab2b8-104">Terminates the enumeration begun with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="ab2b8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab2b8-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_EndEnumeration (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr
);
```  

## <a name="parameters"></a><span data-ttu-id="ab2b8-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ab2b8-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="ab2b8-107">[v] Tento parametr není použit.</span><span class="sxs-lookup"><span data-stu-id="ab2b8-107">[in] This parameter is unused.</span></span>

<span data-ttu-id="ab2b8-108">`ptr`[v] Ukazatel na instanci [IWbemQualifierSet.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)</span><span class="sxs-lookup"><span data-stu-id="ab2b8-108">`ptr` [in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="ab2b8-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ab2b8-109">Return value</span></span>

<span data-ttu-id="ab2b8-110">Následující hodnota vrácená touto funkcí je definována v souboru *hlavičky WbemCli.h* nebo ji můžete definovat jako konstantu v kódu:</span><span class="sxs-lookup"><span data-stu-id="ab2b8-110">The following value returned by this function is defined in the *WbemCli.h* header file, or you can define it as a constant in your code:</span></span>

|<span data-ttu-id="ab2b8-111">Trvalé</span><span class="sxs-lookup"><span data-stu-id="ab2b8-111">Constant</span></span>  |<span data-ttu-id="ab2b8-112">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ab2b8-112">Value</span></span>  |<span data-ttu-id="ab2b8-113">Popis</span><span class="sxs-lookup"><span data-stu-id="ab2b8-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_S_NO_ERROR` | <span data-ttu-id="ab2b8-114">0</span><span class="sxs-lookup"><span data-stu-id="ab2b8-114">0</span></span> | <span data-ttu-id="ab2b8-115">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="ab2b8-115">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="ab2b8-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ab2b8-116">Remarks</span></span>

<span data-ttu-id="ab2b8-117">Tato funkce zalomí volání [metody IWbemQualifierSet::EndEnumeration.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration)</span><span class="sxs-lookup"><span data-stu-id="ab2b8-117">This function wraps a call to the [IWbemQualifierSet::EndEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration) method.</span></span>

<span data-ttu-id="ab2b8-118">Toto volání je doporučeno, ale není vyžadováno.</span><span class="sxs-lookup"><span data-stu-id="ab2b8-118">This call is recommended, but not required.</span></span> <span data-ttu-id="ab2b8-119">Okamžitě uvolní prostředky přidružené k výčtu.</span><span class="sxs-lookup"><span data-stu-id="ab2b8-119">It immediately releases resources associated with the enumeration.</span></span>

## <a name="requirements"></a><span data-ttu-id="ab2b8-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ab2b8-120">Requirements</span></span>  

<span data-ttu-id="ab2b8-121">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab2b8-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
<span data-ttu-id="ab2b8-122">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="ab2b8-122">**Header:** WMINet_Utils.idl</span></span>  
  
<span data-ttu-id="ab2b8-123">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ab2b8-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab2b8-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="ab2b8-124">See also</span></span>

- [<span data-ttu-id="ab2b8-125">Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="ab2b8-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
