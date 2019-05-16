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
ms.openlocfilehash: eb83bc3c0c7724dbcd3133465d4e7ad3a9eea3a9
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636507"
---
# <a name="blessiwbemservices-function"></a><span data-ttu-id="8c40b-103">Funkce BlessIWbemServices</span><span class="sxs-lookup"><span data-stu-id="8c40b-103">BlessIWbemServices function</span></span>
<span data-ttu-id="8c40b-104">Určuje, zda pověření uživatelů odkudkoli přístup k zadané [Služby IWbem](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) třídy.</span><span class="sxs-lookup"><span data-stu-id="8c40b-104">Indicates whether the user credentials permit access to the specified [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) class.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="8c40b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c40b-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="8c40b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8c40b-106">Parameters</span></span>

`pIWbemServices`\
<span data-ttu-id="8c40b-107">[in] Ukazatel [Služby IWbem](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) objektu, pro které jsou potřeba oprávnění.</span><span class="sxs-lookup"><span data-stu-id="8c40b-107">[in] A pointer to the [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object for which permissions are required.</span></span>

`strUser`\
<span data-ttu-id="8c40b-108">[in] Uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="8c40b-108">[in] The user name.</span></span>

`strPassword`\
<span data-ttu-id="8c40b-109">[in] Heslo přidružené k `strUser`.</span><span class="sxs-lookup"><span data-stu-id="8c40b-109">[in] The password associated with `strUser`.</span></span>

`strAuthority`\
<span data-ttu-id="8c40b-110">[in] Název domény uživatele.</span><span class="sxs-lookup"><span data-stu-id="8c40b-110">[in] The domain name of the user.</span></span> <span data-ttu-id="8c40b-111">Zobrazit [ConnectServerWmi](connectserverwmi.md) funkce pro další informace.</span><span class="sxs-lookup"><span data-stu-id="8c40b-111">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`impLevel`\
<span data-ttu-id="8c40b-112">[in] Úroveň zosobnění.</span><span class="sxs-lookup"><span data-stu-id="8c40b-112">[in] The impersonation level.</span></span>

`authnLevel`\
<span data-ttu-id="8c40b-113">[in] Úroveň autorizace.</span><span class="sxs-lookup"><span data-stu-id="8c40b-113">[in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="8c40b-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8c40b-114">Return value</span></span>

<span data-ttu-id="8c40b-115">Následující hodnoty vrácené touto funkcí jsou definovány v *WinError.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="8c40b-115">The following values returned by this function are defined in the *WinError.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="8c40b-116">Konstanta</span><span class="sxs-lookup"><span data-stu-id="8c40b-116">Constant</span></span>  |<span data-ttu-id="8c40b-117">Value</span><span class="sxs-lookup"><span data-stu-id="8c40b-117">Value</span></span>  |<span data-ttu-id="8c40b-118">Popis</span><span class="sxs-lookup"><span data-stu-id="8c40b-118">Description</span></span>  |
|---------|---------|---------|
| `E_INVALIDARG` | <span data-ttu-id="8c40b-119">0x80070057</span><span class="sxs-lookup"><span data-stu-id="8c40b-119">0x80070057</span></span> | <span data-ttu-id="8c40b-120">Jeden nebo více argumentů nejsou platné.</span><span class="sxs-lookup"><span data-stu-id="8c40b-120">One or more arguments are invalid.</span></span> |
| `E_POINTER` | <span data-ttu-id="8c40b-121">0x80004003</span><span class="sxs-lookup"><span data-stu-id="8c40b-121">0x80004003</span></span> | <span data-ttu-id="8c40b-122">`pIWbemServices` je `null`.</span><span class="sxs-lookup"><span data-stu-id="8c40b-122">`pIWbemServices` is `null`.</span></span> | 
| `E_FAIL` | <span data-ttu-id="8c40b-123">0x80000008</span><span class="sxs-lookup"><span data-stu-id="8c40b-123">0x80000008</span></span> | <span data-ttu-id="8c40b-124">Došlo k nespecifikované chybě.</span><span class="sxs-lookup"><span data-stu-id="8c40b-124">An unspecified error has occurred.</span></span> |
| `E_OUTOFMEMORY` | <span data-ttu-id="8c40b-125">0x80000002</span><span class="sxs-lookup"><span data-stu-id="8c40b-125">0x80000002</span></span> | <span data-ttu-id="8c40b-126">K provedení této operace není dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="8c40b-126">Insufficient memory is available to perform the operation.</span></span> | 
| `S_OK` | <span data-ttu-id="8c40b-127">0</span><span class="sxs-lookup"><span data-stu-id="8c40b-127">0</span></span> | <span data-ttu-id="8c40b-128">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="8c40b-128">The function call was successful.</span></span> | 

## <a name="requirements"></a><span data-ttu-id="8c40b-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8c40b-129">Requirements</span></span>  

 <span data-ttu-id="8c40b-130">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c40b-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c40b-131">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="8c40b-131">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="8c40b-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8c40b-132">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c40b-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8c40b-133">See also</span></span>

- [<span data-ttu-id="8c40b-134">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="8c40b-134">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
