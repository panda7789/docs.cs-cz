---
title: QualifierSet_Get funkce (Nespravovaný odkaz na rozhraní API)
description: Funkce QualifierSet_Get získá pojmenovaný kvalifikátor.
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
ms.openlocfilehash: 2f4e2d4518e01f3415b8f17ce5778dd98b2a45c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174885"
---
# <a name="qualifierset_get-function"></a><span data-ttu-id="fe758-103">QualifierSet_Get funkce</span><span class="sxs-lookup"><span data-stu-id="fe758-103">QualifierSet_Get function</span></span>
<span data-ttu-id="fe758-104">Získá zadaný pojmenovaný kvalifikátor.</span><span class="sxs-lookup"><span data-stu-id="fe758-104">Gets the specified named qualifier.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="fe758-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe758-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="fe758-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="fe758-106">Parameters</span></span>

<span data-ttu-id="fe758-107">`vFunc`[v] Tento parametr není použit.</span><span class="sxs-lookup"><span data-stu-id="fe758-107">`vFunc` [in] This parameter is unused.</span></span>

<span data-ttu-id="fe758-108">`ptr`[v] Ukazatel na instanci [IWbemQualifierSet.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)</span><span class="sxs-lookup"><span data-stu-id="fe758-108">`ptr` [in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

<span data-ttu-id="fe758-109">`wszName`[v] Název kvalifikátoru, jehož hodnota je požadována.</span><span class="sxs-lookup"><span data-stu-id="fe758-109">`wszName` [in] The name of the qualifier whose value is requested.</span></span>

<span data-ttu-id="fe758-110">`lFlags`[v] Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="fe758-110">`lFlags` [in] Reserved.</span></span> <span data-ttu-id="fe758-111">Tento parametr musí být 0.</span><span class="sxs-lookup"><span data-stu-id="fe758-111">This parameter must be 0.</span></span>

<span data-ttu-id="fe758-112">`pVal`[out] V případě úspěchu správný typ a hodnotu pro kvalifikátor.</span><span class="sxs-lookup"><span data-stu-id="fe758-112">`pVal` [out] When successful, the correct type and value for the qualifier.</span></span> <span data-ttu-id="fe758-113">Pokud funkce selže, `VARIANT` odkazová `pVal` na od se nezmění.</span><span class="sxs-lookup"><span data-stu-id="fe758-113">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="fe758-114">Pokud je `null`tento parametr , parametr je ignorován.</span><span class="sxs-lookup"><span data-stu-id="fe758-114">If this parameter is `null`, the parameter is ignored.</span></span>

<span data-ttu-id="fe758-115">`plFlavor`[out] Ukazatel na LONG, který obdrží kvalifikátor chuť bity pro požadované kvalifikátor.</span><span class="sxs-lookup"><span data-stu-id="fe758-115">`plFlavor` [out] A pointer to a LONG that receives the qualifier flavor bits for the requested qualifier.</span></span> <span data-ttu-id="fe758-116">Pokud informace o chuti není žádoucí, tento parametr může být `null`.</span><span class="sxs-lookup"><span data-stu-id="fe758-116">If flavor information is not desired, this parameter can be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="fe758-117">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fe758-117">Return value</span></span>

<span data-ttu-id="fe758-118">Následující hodnoty vrácené touto funkcí jsou definovány v souboru *hlavičky WbemCli.h,* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="fe758-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="fe758-119">Trvalé</span><span class="sxs-lookup"><span data-stu-id="fe758-119">Constant</span></span>  |<span data-ttu-id="fe758-120">Hodnota</span><span class="sxs-lookup"><span data-stu-id="fe758-120">Value</span></span>  |<span data-ttu-id="fe758-121">Popis</span><span class="sxs-lookup"><span data-stu-id="fe758-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="fe758-122">0x80041008</span><span class="sxs-lookup"><span data-stu-id="fe758-122">0x80041008</span></span> | <span data-ttu-id="fe758-123">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="fe758-123">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="fe758-124">0x80041002</span><span class="sxs-lookup"><span data-stu-id="fe758-124">0x80041002</span></span> | <span data-ttu-id="fe758-125">Zadaný kvalifikátor neexistuje.</span><span class="sxs-lookup"><span data-stu-id="fe758-125">The specified qualifier does not exist.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="fe758-126">0</span><span class="sxs-lookup"><span data-stu-id="fe758-126">0</span></span> | <span data-ttu-id="fe758-127">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="fe758-127">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="fe758-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fe758-128">Remarks</span></span>

<span data-ttu-id="fe758-129">Tato funkce zalomí volání [IWbemQualifierSet::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) metoda.</span><span class="sxs-lookup"><span data-stu-id="fe758-129">This function wraps a call to the [IWbemQualifierSet::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="fe758-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fe758-130">Requirements</span></span>  
 <span data-ttu-id="fe758-131">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe758-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe758-132">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="fe758-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="fe758-133">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="fe758-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe758-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="fe758-134">See also</span></span>

- [<span data-ttu-id="fe758-135">Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="fe758-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
