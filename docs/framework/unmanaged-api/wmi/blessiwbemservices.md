---
title: Funkce BlessIWbemServices (referenční dokumentace nespravovaného rozhraní API)
description: Funkce BlessIWbemServices označuje, jestli přihlašovací údaje uživatele povolit přístup do služby IWbem třídy.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 23b72856015d028e50c1e3bfd4a12e0f220291c3
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354606"
---
# <a name="blessiwbemservices-function"></a><span data-ttu-id="b5924-103">Funkce BlessIWbemServices</span><span class="sxs-lookup"><span data-stu-id="b5924-103">BlessIWbemServices function</span></span>
<span data-ttu-id="b5924-104">Určuje, zda pověření uživatelů odkudkoli přístup k zadané [Služby IWbem](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) třídy.</span><span class="sxs-lookup"><span data-stu-id="b5924-104">Indicates whether the user credentials permit access to the specified [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) class.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="b5924-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5924-105">Syntax</span></span>  
  
```  
HRESULT BlessIWbemServices (
   [in] IWbemServices* pIWbemServices,
   [in] BSTR strUser, 
   [in] BSTR strPassword, 
   [in] BSTR strAuthority, 
   [in] DWORD impLevel, 
   [in] DWORD authnLevel
);
```  

## <a name="parameters"></a><span data-ttu-id="b5924-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b5924-106">Parameters</span></span>

`pIWbemServices`\
<span data-ttu-id="b5924-107">[in] Ukazatel [Služby IWbem](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) objektu, pro které jsou potřeba oprávnění.</span><span class="sxs-lookup"><span data-stu-id="b5924-107">[in] A pointer to the [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object for which permissions are required.</span></span>

`strUser`\
<span data-ttu-id="b5924-108">[in] Uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="b5924-108">[in] The user name.</span></span>

`strPassword`\
<span data-ttu-id="b5924-109">[in] Heslo přidružené k `strUser`.</span><span class="sxs-lookup"><span data-stu-id="b5924-109">[in] The password associated with `strUser`.</span></span>

`strAuthority`\
<span data-ttu-id="b5924-110">[in] Název domény uživatele.</span><span class="sxs-lookup"><span data-stu-id="b5924-110">[in] The domain name of the user.</span></span> <span data-ttu-id="b5924-111">Zobrazit [ConnectServerWmi](connectserverwmi.md) funkce pro další informace.</span><span class="sxs-lookup"><span data-stu-id="b5924-111">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`impLevel`\
<span data-ttu-id="b5924-112">[in] Úroveň zosobnění.</span><span class="sxs-lookup"><span data-stu-id="b5924-112">[in] The impersonation level.</span></span>

`authnLevel`\
<span data-ttu-id="b5924-113">[in] Úroveň autorizace.</span><span class="sxs-lookup"><span data-stu-id="b5924-113">[in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="b5924-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b5924-114">Return value</span></span>

<span data-ttu-id="b5924-115">Následující hodnoty vrácené touto funkcí jsou definovány v *WinError.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="b5924-115">The following values returned by this function are defined in the *WinError.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="b5924-116">Konstanta</span><span class="sxs-lookup"><span data-stu-id="b5924-116">Constant</span></span>  |<span data-ttu-id="b5924-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="b5924-117">Value</span></span>  |<span data-ttu-id="b5924-118">Popis</span><span class="sxs-lookup"><span data-stu-id="b5924-118">Description</span></span>  |
|---------|---------|---------|
| `E_INVALIDARG` | <span data-ttu-id="b5924-119">0x80070057</span><span class="sxs-lookup"><span data-stu-id="b5924-119">0x80070057</span></span> | <span data-ttu-id="b5924-120">Jeden nebo více argumentů nejsou platné.</span><span class="sxs-lookup"><span data-stu-id="b5924-120">One or more arguments are invalid.</span></span> |
| `E_POINTER` | <span data-ttu-id="b5924-121">0x80004003</span><span class="sxs-lookup"><span data-stu-id="b5924-121">0x80004003</span></span> | <span data-ttu-id="b5924-122">`pIWbemServices` je `null`.</span><span class="sxs-lookup"><span data-stu-id="b5924-122">`pIWbemServices` is `null`.</span></span> | 
| `E_FAIL` | <span data-ttu-id="b5924-123">0x80000008</span><span class="sxs-lookup"><span data-stu-id="b5924-123">0x80000008</span></span> | <span data-ttu-id="b5924-124">Došlo k nespecifikované chybě.</span><span class="sxs-lookup"><span data-stu-id="b5924-124">An unspecified error has occurred.</span></span> |
| `E_OUTOFMEMORY` | <span data-ttu-id="b5924-125">0x80000002</span><span class="sxs-lookup"><span data-stu-id="b5924-125">0x80000002</span></span> | <span data-ttu-id="b5924-126">K provedení této operace není dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="b5924-126">Insufficient memory is available to perform the operation.</span></span> | 
| `S_OK` | <span data-ttu-id="b5924-127">0</span><span class="sxs-lookup"><span data-stu-id="b5924-127">0</span></span> | <span data-ttu-id="b5924-128">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="b5924-128">The function call was successful.</span></span> | 

## <a name="requirements"></a><span data-ttu-id="b5924-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b5924-129">Requirements</span></span>  

 <span data-ttu-id="b5924-130">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5924-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5924-131">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="b5924-131">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="b5924-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b5924-132">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5924-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b5924-133">See also</span></span>

- [<span data-ttu-id="b5924-134">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="b5924-134">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)