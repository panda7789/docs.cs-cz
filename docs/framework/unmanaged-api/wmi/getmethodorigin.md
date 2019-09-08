---
title: GetMethodOrigin – funkce (Reference nespravovaného rozhraní API)
description: Funkce GetMethodOrigin určuje třídu, ve které je metoda deklarována.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9cea7251353dae093f64448c8d84157917fa74c5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798555"
---
# <a name="getmethodorigin-function"></a><span data-ttu-id="d3717-103">Funkce GetMethodOrigin</span><span class="sxs-lookup"><span data-stu-id="d3717-103">GetMethodOrigin function</span></span>
<span data-ttu-id="d3717-104">Určuje třídu, ve které je deklarována metoda.</span><span class="sxs-lookup"><span data-stu-id="d3717-104">Determines the class in which a method is declared.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="d3717-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3717-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodOrigin (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
); 
```  

## <a name="parameters"></a><span data-ttu-id="d3717-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d3717-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="d3717-107">pro Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="d3717-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="d3717-108">pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="d3717-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethodName`  
<span data-ttu-id="d3717-109">pro Název metody pro objekt, jehož vlastnící třída je požadována.</span><span class="sxs-lookup"><span data-stu-id="d3717-109">[in] The name of the method for the object whose owning class is being requested.</span></span> 

`pstrClassName`  
<span data-ttu-id="d3717-110">mimo Přijímá název třídy, která vlastní metodu.</span><span class="sxs-lookup"><span data-stu-id="d3717-110">[out] Receives the name of the class that owns the method.</span></span>

## <a name="return-value"></a><span data-ttu-id="d3717-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d3717-111">Return value</span></span>

<span data-ttu-id="d3717-112">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="d3717-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="d3717-113">Konstanta</span><span class="sxs-lookup"><span data-stu-id="d3717-113">Constant</span></span>  |<span data-ttu-id="d3717-114">Value</span><span class="sxs-lookup"><span data-stu-id="d3717-114">Value</span></span>  |<span data-ttu-id="d3717-115">Popis</span><span class="sxs-lookup"><span data-stu-id="d3717-115">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="d3717-116">0x80041002</span><span class="sxs-lookup"><span data-stu-id="d3717-116">0x80041002</span></span> | <span data-ttu-id="d3717-117">Zadaná metoda nebyla nalezena.</span><span class="sxs-lookup"><span data-stu-id="d3717-117">The specified method was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="d3717-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="d3717-118">0x80041008</span></span> | <span data-ttu-id="d3717-119">Jeden nebo více parametrů je neplatných.</span><span class="sxs-lookup"><span data-stu-id="d3717-119">One or more parameters are not valid.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="d3717-120">0</span><span class="sxs-lookup"><span data-stu-id="d3717-120">0</span></span> | <span data-ttu-id="d3717-121">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="d3717-121">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="d3717-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d3717-122">Remarks</span></span>

<span data-ttu-id="d3717-123">Tato funkce zalomí volání metody [IWbemclassObject:: GetMethodOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) .</span><span class="sxs-lookup"><span data-stu-id="d3717-123">This function wraps a call to the [IWbemClassObject::GetMethodOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) method.</span></span>

<span data-ttu-id="d3717-124">Vzhledem k tomu, že třída může dědit metody z jedné nebo více základních tříd, vývojáři často chtějí určit třídu, ve které je daná metoda definována.</span><span class="sxs-lookup"><span data-stu-id="d3717-124">Because a class can inherit methods from one or more base classes, developers often want to determine the class in which a given method is defined.</span></span>

<span data-ttu-id="d3717-125">Parametr nesmí ukazovat na platnou `BSTR` hodnotu před voláním funkce, protože se jedná o `out` parametr; po návratu funkce se tento ukazatel nevrátí. `pstrClassName`</span><span class="sxs-lookup"><span data-stu-id="d3717-125">The `pstrClassName` parameter must not point to a valid `BSTR` before the function is called because this is an `out` parameter; this pointer is not deallocated after the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="d3717-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d3717-126">Requirements</span></span>  
<span data-ttu-id="d3717-127">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3717-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3717-128">**Hlaviček** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="d3717-128">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="d3717-129">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d3717-129">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3717-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d3717-130">See also</span></span>

- [<span data-ttu-id="d3717-131">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="d3717-131">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
