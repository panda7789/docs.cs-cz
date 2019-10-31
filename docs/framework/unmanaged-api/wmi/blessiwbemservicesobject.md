---
title: BlessIWbemServicesObject – funkce (Reference nespravovaného rozhraní API)
description: Funkce BlessIWbemServicesObject určuje, jestli přihlašovací údaje uživatele povolují přístup k objektu služby IWbem.
ms.date: 11/06/2017
api_name:
- BlessIWbemServicesObject
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BlessIWbemServicesObject
helpviewer_keywords:
- BlessIWbemServicesObject function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: f77ff394668a235dd63cf0cddf71ea418a28125b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141681"
---
# <a name="blessiwbemservicesobject-function"></a><span data-ttu-id="ead59-103">Funkce BlessIWbemServicesObject</span><span class="sxs-lookup"><span data-stu-id="ead59-103">BlessIWbemServicesObject function</span></span>
<span data-ttu-id="ead59-104">Určuje, zda přihlašovací údaje uživatele povolují přístup k zadanému objektu [Služby IWbem](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) .</span><span class="sxs-lookup"><span data-stu-id="ead59-104">Indicates whether the user credentials permit access to a specified [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="ead59-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ead59-105">Syntax</span></span>

```cpp
HRESULT BlessIWbemServicesObject (
   [in] IUnknown* pIUnknown,
   [in] BSTR strUser, 
   [in] BSTR strPassword, 
   [in] BSTR strAuthority, 
   [in] DWORD impLevel, 
   [in] DWORD authnLevel
);
```

## <a name="parameters"></a><span data-ttu-id="ead59-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ead59-106">Parameters</span></span>

`pIWbemServices`\
<span data-ttu-id="ead59-107">pro Ukazatel na objekt služby WMI.</span><span class="sxs-lookup"><span data-stu-id="ead59-107">[in] A pointer to a WMI service object.</span></span>

`strUser`\
<span data-ttu-id="ead59-108">pro Uživatelské jméno</span><span class="sxs-lookup"><span data-stu-id="ead59-108">[in] The user name.</span></span>

`strPassword`\
<span data-ttu-id="ead59-109">pro Heslo přidružené k `strUser`</span><span class="sxs-lookup"><span data-stu-id="ead59-109">[in] The password associated with `strUser`.</span></span>

`strAuthority`\
<span data-ttu-id="ead59-110">pro Název domény uživatele</span><span class="sxs-lookup"><span data-stu-id="ead59-110">[in] The domain name of the user.</span></span> <span data-ttu-id="ead59-111">Další informace najdete v tématu funkce [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="ead59-111">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`impLevel`\
<span data-ttu-id="ead59-112">pro Úroveň zosobnění.</span><span class="sxs-lookup"><span data-stu-id="ead59-112">[in] The impersonation level.</span></span>

`authnLevel`\
<span data-ttu-id="ead59-113">pro Úroveň autorizace.</span><span class="sxs-lookup"><span data-stu-id="ead59-113">[in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="ead59-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ead59-114">Return value</span></span>

<span data-ttu-id="ead59-115">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *Winerror. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="ead59-115">The following values returned by this function are defined in the *WinError.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="ead59-116">Konstanta</span><span class="sxs-lookup"><span data-stu-id="ead59-116">Constant</span></span>  |<span data-ttu-id="ead59-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ead59-117">Value</span></span>  |<span data-ttu-id="ead59-118">Popis</span><span class="sxs-lookup"><span data-stu-id="ead59-118">Description</span></span>  |
|---------|---------|---------|
| `E_INVALIDARG` | <span data-ttu-id="ead59-119">0x80070057</span><span class="sxs-lookup"><span data-stu-id="ead59-119">0x80070057</span></span> | <span data-ttu-id="ead59-120">Jeden nebo více argumentů je neplatných.</span><span class="sxs-lookup"><span data-stu-id="ead59-120">One or more arguments are invalid.</span></span> |
| `E_POINTER` | <span data-ttu-id="ead59-121">0x80004003</span><span class="sxs-lookup"><span data-stu-id="ead59-121">0x80004003</span></span> | <span data-ttu-id="ead59-122">`pIWbemServices` je `null`.</span><span class="sxs-lookup"><span data-stu-id="ead59-122">`pIWbemServices` is `null`.</span></span> | 
| `E_FAIL` | <span data-ttu-id="ead59-123">0x80000008</span><span class="sxs-lookup"><span data-stu-id="ead59-123">0x80000008</span></span> | <span data-ttu-id="ead59-124">Došlo k neurčené chybě.</span><span class="sxs-lookup"><span data-stu-id="ead59-124">An unspecified error has occurred.</span></span> |
| `E_OUTOFMEMORY` | <span data-ttu-id="ead59-125">0x80000002</span><span class="sxs-lookup"><span data-stu-id="ead59-125">0x80000002</span></span> | <span data-ttu-id="ead59-126">K provedení této operace je k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="ead59-126">Insufficient memory is available to perform the operation.</span></span> | 
| `S_OK` | <span data-ttu-id="ead59-127">0,8</span><span class="sxs-lookup"><span data-stu-id="ead59-127">0</span></span> | <span data-ttu-id="ead59-128">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="ead59-128">The function call was successful.</span></span> | 

## <a name="requirements"></a><span data-ttu-id="ead59-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ead59-129">Requirements</span></span>

 <span data-ttu-id="ead59-130">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ead59-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="ead59-131">**Hlavička:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="ead59-131">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="ead59-132">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ead59-132">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ead59-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ead59-133">See also</span></span>

- [<span data-ttu-id="ead59-134">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="ead59-134">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
