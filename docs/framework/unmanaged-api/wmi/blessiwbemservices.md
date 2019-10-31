---
title: BlessIWbemServices – funkce (Reference nespravovaného rozhraní API)
description: Funkce BlessIWbemServices určuje, zda přihlašovací údaje uživatele povolují přístup ke třídě služby IWbem.
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
ms.openlocfilehash: 946d29892052ea69c2a8a3bf11e7be7a1b2d7068
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138771"
---
# <a name="blessiwbemservices-function"></a><span data-ttu-id="bef8b-103">Funkce BlessIWbemServices</span><span class="sxs-lookup"><span data-stu-id="bef8b-103">BlessIWbemServices function</span></span>
<span data-ttu-id="bef8b-104">Určuje, zda přihlašovací údaje uživatele povolují přístup k zadané třídě [Služby IWbem](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) .</span><span class="sxs-lookup"><span data-stu-id="bef8b-104">Indicates whether the user credentials permit access to the specified [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) class.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="bef8b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bef8b-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="bef8b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="bef8b-106">Parameters</span></span>

`pIWbemServices`\
<span data-ttu-id="bef8b-107">pro Ukazatel na objekt [Služby IWbem](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) , pro který jsou požadována oprávnění.</span><span class="sxs-lookup"><span data-stu-id="bef8b-107">[in] A pointer to the [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object for which permissions are required.</span></span>

`strUser`\
<span data-ttu-id="bef8b-108">pro Uživatelské jméno</span><span class="sxs-lookup"><span data-stu-id="bef8b-108">[in] The user name.</span></span>

`strPassword`\
<span data-ttu-id="bef8b-109">pro Heslo přidružené k `strUser`</span><span class="sxs-lookup"><span data-stu-id="bef8b-109">[in] The password associated with `strUser`.</span></span>

`strAuthority`\
<span data-ttu-id="bef8b-110">pro Název domény uživatele</span><span class="sxs-lookup"><span data-stu-id="bef8b-110">[in] The domain name of the user.</span></span> <span data-ttu-id="bef8b-111">Další informace najdete v tématu funkce [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="bef8b-111">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`impLevel`\
<span data-ttu-id="bef8b-112">pro Úroveň zosobnění.</span><span class="sxs-lookup"><span data-stu-id="bef8b-112">[in] The impersonation level.</span></span>

`authnLevel`\
<span data-ttu-id="bef8b-113">pro Úroveň autorizace.</span><span class="sxs-lookup"><span data-stu-id="bef8b-113">[in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="bef8b-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bef8b-114">Return value</span></span>

<span data-ttu-id="bef8b-115">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *Winerror. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="bef8b-115">The following values returned by this function are defined in the *WinError.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="bef8b-116">Konstanta</span><span class="sxs-lookup"><span data-stu-id="bef8b-116">Constant</span></span>  |<span data-ttu-id="bef8b-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="bef8b-117">Value</span></span>  |<span data-ttu-id="bef8b-118">Popis</span><span class="sxs-lookup"><span data-stu-id="bef8b-118">Description</span></span>  |
|---------|---------|---------|
| `E_INVALIDARG` | <span data-ttu-id="bef8b-119">0x80070057</span><span class="sxs-lookup"><span data-stu-id="bef8b-119">0x80070057</span></span> | <span data-ttu-id="bef8b-120">Jeden nebo více argumentů je neplatných.</span><span class="sxs-lookup"><span data-stu-id="bef8b-120">One or more arguments are invalid.</span></span> |
| `E_POINTER` | <span data-ttu-id="bef8b-121">0x80004003</span><span class="sxs-lookup"><span data-stu-id="bef8b-121">0x80004003</span></span> | <span data-ttu-id="bef8b-122">`pIWbemServices` je `null`.</span><span class="sxs-lookup"><span data-stu-id="bef8b-122">`pIWbemServices` is `null`.</span></span> | 
| `E_FAIL` | <span data-ttu-id="bef8b-123">0x80000008</span><span class="sxs-lookup"><span data-stu-id="bef8b-123">0x80000008</span></span> | <span data-ttu-id="bef8b-124">Došlo k neurčené chybě.</span><span class="sxs-lookup"><span data-stu-id="bef8b-124">An unspecified error has occurred.</span></span> |
| `E_OUTOFMEMORY` | <span data-ttu-id="bef8b-125">0x80000002</span><span class="sxs-lookup"><span data-stu-id="bef8b-125">0x80000002</span></span> | <span data-ttu-id="bef8b-126">K provedení této operace je k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="bef8b-126">Insufficient memory is available to perform the operation.</span></span> | 
| `S_OK` | <span data-ttu-id="bef8b-127">0,8</span><span class="sxs-lookup"><span data-stu-id="bef8b-127">0</span></span> | <span data-ttu-id="bef8b-128">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="bef8b-128">The function call was successful.</span></span> | 

## <a name="requirements"></a><span data-ttu-id="bef8b-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bef8b-129">Requirements</span></span>  

 <span data-ttu-id="bef8b-130">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bef8b-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bef8b-131">**Hlavička:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="bef8b-131">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="bef8b-132">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bef8b-132">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bef8b-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bef8b-133">See also</span></span>

- [<span data-ttu-id="bef8b-134">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="bef8b-134">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
