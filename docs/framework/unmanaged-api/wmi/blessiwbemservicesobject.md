---
title: "Funkce BlessIWbemServicesObject (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce BlessIWbemServicesObject označuje, zda přihlašovací údaje uživatele povolit přístup k objektu služby IWbem"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: BlessIWbemServicesObject
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: BlessIWbemServicesObject
helpviewer_keywords: BlessIWbemServicesObject function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ebba6df29b814315180e9c8e936e5e1ad175ecf8
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2017
---
# <a name="blessiwbemservicesobject-function"></a><span data-ttu-id="25089-103">BlessIWbemServicesObject – funkce</span><span class="sxs-lookup"><span data-stu-id="25089-103">BlessIWbemServicesObject function</span></span>
<span data-ttu-id="25089-104">Určuje, zda pověření uživatelů povolit přístup k zadané [Služby IWbem](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) objektu.</span><span class="sxs-lookup"><span data-stu-id="25089-104">Indicates whether the user credentials permit access to a specified [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) object.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="25089-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25089-105">Syntax</span></span>  
  
```  
HRESULT BlessIWbemServicesObject (
   [in] IUnknown* pIUnknown,
   [in] BSTR strUser, 
   [in] BSTR strPassword, 
   [in] BSTR strAuthority, 
   [in] DWORD impLevel, 
   [in] DWORD authnLevel
);
```  

## <a name="parameters"></a><span data-ttu-id="25089-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="25089-106">Parameters</span></span>

`pIWbemServices`  
<span data-ttu-id="25089-107">[v] Ukazatel na objekt služby WMI.</span><span class="sxs-lookup"><span data-stu-id="25089-107">[in] A pointer to a WMI service object.</span></span>

`strUser`  
<span data-ttu-id="25089-108">[v] Uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="25089-108">[in] The user name.</span></span>

`strPassword`  
<span data-ttu-id="25089-109">[v] Heslo přidružené k `strUser`.</span><span class="sxs-lookup"><span data-stu-id="25089-109">[in] The password associated with `strUser`.</span></span>

<span data-ttu-id="25089-110">`strAuthority`[v] Název domény uživatele.</span><span class="sxs-lookup"><span data-stu-id="25089-110">`strAuthority` [in] The domain name of the user.</span></span> <span data-ttu-id="25089-111">Najdete v článku [ConnectServerWmi](connectserverwmi.md) funkce pro další informace.</span><span class="sxs-lookup"><span data-stu-id="25089-111">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

<span data-ttu-id="25089-112">`impLevel`[v] Úroveň zosobnění.</span><span class="sxs-lookup"><span data-stu-id="25089-112">`impLevel` [in] The impersonation level.</span></span>

<span data-ttu-id="25089-113">`authnLevel`[v] Úroveň ověřování.</span><span class="sxs-lookup"><span data-stu-id="25089-113">`authnLevel` [in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="25089-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="25089-114">Return value</span></span>

<span data-ttu-id="25089-115">Následující hodnoty, vrátí tato funkce jsou definovány v *WinError.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="25089-115">The following values returned by this function are defined in the *WinError.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="25089-116">Konstanta</span><span class="sxs-lookup"><span data-stu-id="25089-116">Constant</span></span>  |<span data-ttu-id="25089-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="25089-117">Value</span></span>  |<span data-ttu-id="25089-118">Popis</span><span class="sxs-lookup"><span data-stu-id="25089-118">Description</span></span>  |
|---------|---------|---------|
| `E_INVALIDARG` | <span data-ttu-id="25089-119">0x80070057</span><span class="sxs-lookup"><span data-stu-id="25089-119">0x80070057</span></span> | <span data-ttu-id="25089-120">Jeden nebo více argumenty nejsou platné.</span><span class="sxs-lookup"><span data-stu-id="25089-120">One or more arguments are invalid.</span></span> |
| `E_POINTER` | <span data-ttu-id="25089-121">0x80004003</span><span class="sxs-lookup"><span data-stu-id="25089-121">0x80004003</span></span> | <span data-ttu-id="25089-122">`pIWbemServices`je `null`.</span><span class="sxs-lookup"><span data-stu-id="25089-122">`pIWbemServices` is `null`.</span></span> | 
| `E_FAIL` | <span data-ttu-id="25089-123">0x80000008</span><span class="sxs-lookup"><span data-stu-id="25089-123">0x80000008</span></span> | <span data-ttu-id="25089-124">Došlo k neurčené chybě.</span><span class="sxs-lookup"><span data-stu-id="25089-124">An unspecified error has occurred.</span></span> |
| `E_OUTOFMEMORY` | <span data-ttu-id="25089-125">0x80000002</span><span class="sxs-lookup"><span data-stu-id="25089-125">0x80000002</span></span> | <span data-ttu-id="25089-126">K provedení operace není dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="25089-126">Insufficient memory is available to perform the operation.</span></span> | 
| `S_OK` | <span data-ttu-id="25089-127">0</span><span class="sxs-lookup"><span data-stu-id="25089-127">0</span></span> | <span data-ttu-id="25089-128">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="25089-128">The function call was successful.</span></span> | 

## <a name="requirements"></a><span data-ttu-id="25089-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="25089-129">Requirements</span></span>  
 <span data-ttu-id="25089-130">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25089-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25089-131">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="25089-131">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="25089-132">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="25089-132">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25089-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="25089-133">See also</span></span>  
[<span data-ttu-id="25089-134">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="25089-134">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
