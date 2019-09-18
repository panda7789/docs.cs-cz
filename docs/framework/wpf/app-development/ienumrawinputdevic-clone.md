---
title: IEnumRAWINPUTDEVIC:Clone
ms.date: 03/30/2017
helpviewer_keywords:
- Clone method [WPF]
ms.assetid: 2a6a1900-aa55-45fa-9382-241d569a2dc4
ms.openlocfilehash: cd634b4d4a88d83d425b787ed8493f9aa2504988
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053410"
---
# <a name="ienumrawinputdevicclone"></a><span data-ttu-id="331bf-102">IEnumRAWINPUTDEVIC:Clone</span><span class="sxs-lookup"><span data-stu-id="331bf-102">IEnumRAWINPUTDEVIC:Clone</span></span>
<span data-ttu-id="331bf-103">Vytvoří další výčet nezpracovaných vstupních zařízení se stejným stavem, jako je aktuální enumerátor pro iteraci přes stejný seznam.</span><span class="sxs-lookup"><span data-stu-id="331bf-103">Creates another raw input device enumerator with the same state as the current enumerator to iterate over the same list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="331bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="331bf-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="331bf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="331bf-105">Parameters</span></span>  
 `ppenum`  
  
 <span data-ttu-id="331bf-106">mimo Adresa výstupní proměnné, která přijímá ukazatel rozhraní [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) .</span><span class="sxs-lookup"><span data-stu-id="331bf-106">[out] Address of output variable that receives the [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) interface pointer.</span></span> <span data-ttu-id="331bf-107">Pokud je metoda neúspěšná, hodnota této výstupní proměnné není definována.</span><span class="sxs-lookup"><span data-stu-id="331bf-107">If the method is unsuccessful, the value of this output variable is undefined.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="331bf-108">Hodnota vlastnosti / návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="331bf-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="331bf-109">HRESULT Tato metoda podporuje standardní návratové hodnoty E_INVALIDARG, E_OUTOFMEMORY a E_UNEXPECTED.</span><span class="sxs-lookup"><span data-stu-id="331bf-109">HRESULT: This method supports the standard return values E_INVALIDARG, E_OUTOFMEMORY, and E_UNEXPECTED.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="331bf-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="331bf-110">Remarks</span></span>  
 <span data-ttu-id="331bf-111">Tato metoda umožňuje zaznamenat bod v sekvenci výčtu, aby bylo možné později vrátit k danému okamžiku.</span><span class="sxs-lookup"><span data-stu-id="331bf-111">This method makes it possible to record a point in the enumeration sequence in order to return to that point at a later time.</span></span> <span data-ttu-id="331bf-112">Volající musí vydávat nový enumerátor odděleně od prvního enumerátoru.</span><span class="sxs-lookup"><span data-stu-id="331bf-112">The caller must release this new enumerator separately from the first enumerator.</span></span>
