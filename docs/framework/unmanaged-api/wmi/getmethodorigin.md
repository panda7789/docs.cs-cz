---
title: Funkce GetMethodOrigin (Unmanaged API Reference)
description: Funkce GetMethodOrigin určuje třídu, ve které je deklarována metoda.
ms.date: 11/06/2017
api_name:
- GetMethodOrigin
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethodOrigin
helpviewer_keywords:
- GetMethodOrigin function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 5b4609b6649be875aea7dfcf52ba36b1e98ab7bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176796"
---
# <a name="getmethodorigin-function"></a><span data-ttu-id="1fac5-103">Funkce GetMethodOrigin</span><span class="sxs-lookup"><span data-stu-id="1fac5-103">GetMethodOrigin function</span></span>
<span data-ttu-id="1fac5-104">Určuje třídu, ve které je deklarována metoda.</span><span class="sxs-lookup"><span data-stu-id="1fac5-104">Determines the class in which a method is declared.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="1fac5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1fac5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodOrigin (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
);
```  

## <a name="parameters"></a><span data-ttu-id="1fac5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1fac5-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="1fac5-107">[v] Tento parametr není použit.</span><span class="sxs-lookup"><span data-stu-id="1fac5-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="1fac5-108">[v] Ukazatel na instanci [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="1fac5-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethodName`  
<span data-ttu-id="1fac5-109">[v] Název metody pro objekt, jehož vlastnící třídy je požadováno.</span><span class="sxs-lookup"><span data-stu-id="1fac5-109">[in] The name of the method for the object whose owning class is being requested.</span></span>

`pstrClassName`  
<span data-ttu-id="1fac5-110">[out] Obdrží název třídy, která vlastní metodu.</span><span class="sxs-lookup"><span data-stu-id="1fac5-110">[out] Receives the name of the class that owns the method.</span></span>

## <a name="return-value"></a><span data-ttu-id="1fac5-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1fac5-111">Return value</span></span>

<span data-ttu-id="1fac5-112">Následující hodnoty vrácené touto funkcí jsou definovány v souboru *hlavičky WbemCli.h,* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="1fac5-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="1fac5-113">Trvalé</span><span class="sxs-lookup"><span data-stu-id="1fac5-113">Constant</span></span>  |<span data-ttu-id="1fac5-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="1fac5-114">Value</span></span>  |<span data-ttu-id="1fac5-115">Popis</span><span class="sxs-lookup"><span data-stu-id="1fac5-115">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="1fac5-116">0x80041002</span><span class="sxs-lookup"><span data-stu-id="1fac5-116">0x80041002</span></span> | <span data-ttu-id="1fac5-117">Zadaná metoda nebyla nalezena.</span><span class="sxs-lookup"><span data-stu-id="1fac5-117">The specified method was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="1fac5-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="1fac5-118">0x80041008</span></span> | <span data-ttu-id="1fac5-119">Jeden nebo více parametrů není platný.</span><span class="sxs-lookup"><span data-stu-id="1fac5-119">One or more parameters are not valid.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="1fac5-120">0</span><span class="sxs-lookup"><span data-stu-id="1fac5-120">0</span></span> | <span data-ttu-id="1fac5-121">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="1fac5-121">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="1fac5-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1fac5-122">Remarks</span></span>

<span data-ttu-id="1fac5-123">Tato funkce zabalí volání metody [IWbemClassObject::GetMethodOrigin.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod)</span><span class="sxs-lookup"><span data-stu-id="1fac5-123">This function wraps a call to the [IWbemClassObject::GetMethodOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) method.</span></span>

<span data-ttu-id="1fac5-124">Vzhledem k tomu, že třída může dědit metody z jedné nebo více základních tříd, vývojáři často chtějí určit třídu, ve které je daná metoda definována.</span><span class="sxs-lookup"><span data-stu-id="1fac5-124">Because a class can inherit methods from one or more base classes, developers often want to determine the class in which a given method is defined.</span></span>

<span data-ttu-id="1fac5-125">Parametr `pstrClassName` nesmí ukazovat na `BSTR` platný před voláním funkce, `out` protože se jedná o parametr; tento ukazatel není přidělena po vrátí funkce.</span><span class="sxs-lookup"><span data-stu-id="1fac5-125">The `pstrClassName` parameter must not point to a valid `BSTR` before the function is called because this is an `out` parameter; this pointer is not deallocated after the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="1fac5-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1fac5-126">Requirements</span></span>  
<span data-ttu-id="1fac5-127">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1fac5-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fac5-128">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="1fac5-128">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="1fac5-129">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1fac5-129">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fac5-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="1fac5-130">See also</span></span>

- [<span data-ttu-id="1fac5-131">Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="1fac5-131">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
