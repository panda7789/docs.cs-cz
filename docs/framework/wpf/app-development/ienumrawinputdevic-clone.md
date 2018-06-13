---
title: IEnumRAWINPUTDEVIC:Clone
ms.date: 03/30/2017
helpviewer_keywords:
- Clone method [WPF]
ms.assetid: 2a6a1900-aa55-45fa-9382-241d569a2dc4
ms.openlocfilehash: da089e5342e641ffebe22ca6a4a593f97faeb89c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545337"
---
# <a name="ienumrawinputdevicclone"></a><span data-ttu-id="7a6fa-102">IEnumRAWINPUTDEVIC:Clone</span><span class="sxs-lookup"><span data-stu-id="7a6fa-102">IEnumRAWINPUTDEVIC:Clone</span></span>
<span data-ttu-id="7a6fa-103">Vytvoří další nezpracované vstupní zařízení enumerátor stejného stavu jako aktuální enumerátor Iterujte přes stejný seznam.</span><span class="sxs-lookup"><span data-stu-id="7a6fa-103">Creates another raw input device enumerator with the same state as the current enumerator to iterate over the same list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a6fa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7a6fa-104">Syntax</span></span>  
  
```  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7a6fa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7a6fa-105">Parameters</span></span>  
 `ppenum`  
  
 <span data-ttu-id="7a6fa-106">[out] Adresa výstup proměnné, která přijímá [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) ukazatel rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7a6fa-106">[out] Address of output variable that receives the [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) interface pointer.</span></span> <span data-ttu-id="7a6fa-107">Pokud je metoda úspěšné, hodnotu tento výstup proměnné není definován.</span><span class="sxs-lookup"><span data-stu-id="7a6fa-107">If the method is unsuccessful, the value of this output variable is undefined.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="7a6fa-108">Hodnota vlastnosti / návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7a6fa-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="7a6fa-109">HRESULT: Tato metoda podporuje standardní návratové hodnoty E_INVALIDARG E_OUTOFMEMORY a E_UNEXPECTED.</span><span class="sxs-lookup"><span data-stu-id="7a6fa-109">HRESULT: This method supports the standard return values E_INVALIDARG, E_OUTOFMEMORY, and E_UNEXPECTED.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a6fa-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7a6fa-110">Remarks</span></span>  
 <span data-ttu-id="7a6fa-111">Tato metoda umožňuje zaznamenat bod v pořadí výčtu cílem vrátit do tohoto bodu později.</span><span class="sxs-lookup"><span data-stu-id="7a6fa-111">This method makes it possible to record a point in the enumeration sequence in order to return to that point at a later time.</span></span> <span data-ttu-id="7a6fa-112">Volající musí uvolnit tento nový enumerátor odděleně od první enumerátor.</span><span class="sxs-lookup"><span data-stu-id="7a6fa-112">The caller must release this new enumerator separately from the first enumerator.</span></span>
