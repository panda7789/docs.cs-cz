---
title: IEnumRAWINPUTDEVIC:Clone
ms.date: 03/30/2017
helpviewer_keywords:
- Clone method [WPF]
ms.assetid: 2a6a1900-aa55-45fa-9382-241d569a2dc4
ms.openlocfilehash: abc8a6e4780c8fe50afcf1b04f7e14aeb6452704
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949588"
---
# <a name="ienumrawinputdevicclone"></a><span data-ttu-id="fa80a-102">IEnumRAWINPUTDEVIC:Clone</span><span class="sxs-lookup"><span data-stu-id="fa80a-102">IEnumRAWINPUTDEVIC:Clone</span></span>
<span data-ttu-id="fa80a-103">Vytvoří další enumerátor nezpracované vstupní zařízení pomocí stejného stavu jako aktuální enumerátor k iteraci přes stejného seznamu.</span><span class="sxs-lookup"><span data-stu-id="fa80a-103">Creates another raw input device enumerator with the same state as the current enumerator to iterate over the same list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa80a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fa80a-104">Syntax</span></span>  
  
```  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa80a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fa80a-105">Parameters</span></span>  
 `ppenum`  
  
 <span data-ttu-id="fa80a-106">[out] Adresy výstupní proměnné, která přijímá [ienumrawinputdevice –](ienumrawinputdevice.md) ukazatel rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fa80a-106">[out] Address of output variable that receives the [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) interface pointer.</span></span> <span data-ttu-id="fa80a-107">Pokud je metoda neúspěšná, hodnota této výstupní proměnné není definována.</span><span class="sxs-lookup"><span data-stu-id="fa80a-107">If the method is unsuccessful, the value of this output variable is undefined.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="fa80a-108">Hodnota vlastnosti / návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fa80a-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="fa80a-109">HODNOTA HRESULT: Tato metoda podporuje standardní návratové hodnoty E_INVALIDARG E_OUTOFMEMORY a e_unexpected, je.</span><span class="sxs-lookup"><span data-stu-id="fa80a-109">HRESULT: This method supports the standard return values E_INVALIDARG, E_OUTOFMEMORY, and E_UNEXPECTED.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa80a-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fa80a-110">Remarks</span></span>  
 <span data-ttu-id="fa80a-111">Tato metoda umožňuje zaznamenávat do bodu v pořadí výčtu vraťte do tohoto bodu později.</span><span class="sxs-lookup"><span data-stu-id="fa80a-111">This method makes it possible to record a point in the enumeration sequence in order to return to that point at a later time.</span></span> <span data-ttu-id="fa80a-112">Volající musí uvolnit tento nový čítač odděleně od první enumerátor.</span><span class="sxs-lookup"><span data-stu-id="fa80a-112">The caller must release this new enumerator separately from the first enumerator.</span></span>
