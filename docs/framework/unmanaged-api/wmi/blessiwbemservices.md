---
title: BlessIWbemServices funkce (Unmanaged API Reference)
description: Funkce BlessIWbemServices označuje, zda pověření uživatele povolit přístup ke třídě IWbemServices.
ms.date: 11/06/2017
api_name:
- BlessIWbemServices
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BlessIWbemServices
helpviewer_keywords:
- BlessIWbemServices function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 4b15af840cc00b3ec261604db4f3625c6b975d3e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176861"
---
# <a name="blessiwbemservices-function"></a><span data-ttu-id="d8862-103">Funkce BlessIWbemServices</span><span class="sxs-lookup"><span data-stu-id="d8862-103">BlessIWbemServices function</span></span>
<span data-ttu-id="d8862-104">Označuje, zda pověření uživatele povolit přístup k zadané [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) třídy.</span><span class="sxs-lookup"><span data-stu-id="d8862-104">Indicates whether the user credentials permit access to the specified [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) class.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="d8862-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8862-105">Syntax</span></span>  
  
```cpp
HRESULT BlessIWbemServices (
   [in] IWbemServices* pIWbemServices,
   [in] BSTR strUser,
   [in] BSTR strPassword,
   [in] BSTR strAuthority,
   [in] DWORD impLevel,
   [in] DWORD authnLevel
);
```  

## <a name="parameters"></a><span data-ttu-id="d8862-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8862-106">Parameters</span></span>

`pIWbemServices`\
<span data-ttu-id="d8862-107">[v] Ukazatel na objekt [IWbemServices,](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) pro který jsou vyžadována oprávnění.</span><span class="sxs-lookup"><span data-stu-id="d8862-107">[in] A pointer to the [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object for which permissions are required.</span></span>

`strUser`\
<span data-ttu-id="d8862-108">[v] Uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="d8862-108">[in] The user name.</span></span>

`strPassword`\
<span data-ttu-id="d8862-109">[v] Heslo přidružené `strUser`k souboru .</span><span class="sxs-lookup"><span data-stu-id="d8862-109">[in] The password associated with `strUser`.</span></span>

`strAuthority`\
<span data-ttu-id="d8862-110">[v] Název domény uživatele.</span><span class="sxs-lookup"><span data-stu-id="d8862-110">[in] The domain name of the user.</span></span> <span data-ttu-id="d8862-111">Další informace naleznete ve funkci [ConnectServerWmi.](connectserverwmi.md)</span><span class="sxs-lookup"><span data-stu-id="d8862-111">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`impLevel`\
<span data-ttu-id="d8862-112">[v] Úroveň zosobnění.</span><span class="sxs-lookup"><span data-stu-id="d8862-112">[in] The impersonation level.</span></span>

`authnLevel`\
<span data-ttu-id="d8862-113">[v] Úroveň autorizace.</span><span class="sxs-lookup"><span data-stu-id="d8862-113">[in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="d8862-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d8862-114">Return value</span></span>

<span data-ttu-id="d8862-115">Následující hodnoty vrácené touto funkcí jsou definovány v souboru *hlavičky WinError.h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="d8862-115">The following values returned by this function are defined in the *WinError.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="d8862-116">Trvalé</span><span class="sxs-lookup"><span data-stu-id="d8862-116">Constant</span></span>  |<span data-ttu-id="d8862-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="d8862-117">Value</span></span>  |<span data-ttu-id="d8862-118">Popis</span><span class="sxs-lookup"><span data-stu-id="d8862-118">Description</span></span>  |
|---------|---------|---------|
| `E_INVALIDARG` | <span data-ttu-id="d8862-119">0x80070057</span><span class="sxs-lookup"><span data-stu-id="d8862-119">0x80070057</span></span> | <span data-ttu-id="d8862-120">Jeden nebo více argumentů je neplatných.</span><span class="sxs-lookup"><span data-stu-id="d8862-120">One or more arguments are invalid.</span></span> |
| `E_POINTER` | <span data-ttu-id="d8862-121">0x80004003</span><span class="sxs-lookup"><span data-stu-id="d8862-121">0x80004003</span></span> | <span data-ttu-id="d8862-122">`pIWbemServices` je `null`.</span><span class="sxs-lookup"><span data-stu-id="d8862-122">`pIWbemServices` is `null`.</span></span> |
| `E_FAIL` | <span data-ttu-id="d8862-123">0x80000008</span><span class="sxs-lookup"><span data-stu-id="d8862-123">0x80000008</span></span> | <span data-ttu-id="d8862-124">Došlo k nespecifikované chybě.</span><span class="sxs-lookup"><span data-stu-id="d8862-124">An unspecified error has occurred.</span></span> |
| `E_OUTOFMEMORY` | <span data-ttu-id="d8862-125">0x80000002</span><span class="sxs-lookup"><span data-stu-id="d8862-125">0x80000002</span></span> | <span data-ttu-id="d8862-126">K provedení operace není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="d8862-126">Insufficient memory is available to perform the operation.</span></span> |
| `S_OK` | <span data-ttu-id="d8862-127">0</span><span class="sxs-lookup"><span data-stu-id="d8862-127">0</span></span> | <span data-ttu-id="d8862-128">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="d8862-128">The function call was successful.</span></span> |

## <a name="requirements"></a><span data-ttu-id="d8862-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d8862-129">Requirements</span></span>  

 <span data-ttu-id="d8862-130">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8862-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8862-131">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="d8862-131">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="d8862-132">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d8862-132">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8862-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="d8862-133">See also</span></span>

- [<span data-ttu-id="d8862-134">Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="d8862-134">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
