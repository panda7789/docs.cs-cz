---
title: IEnumRAWINPUTDEVIC:Skip
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Skip method [WPF]
ms.assetid: c967b0f8-1c6a-459c-8c16-d4f08918ab65
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e232d2525f9dfa339516f766d417ea9c3ee976c7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ienumrawinputdevicskip"></a><span data-ttu-id="32e4d-102">IEnumRAWINPUTDEVIC:Skip</span><span class="sxs-lookup"><span data-stu-id="32e4d-102">IEnumRAWINPUTDEVIC:Skip</span></span>
<span data-ttu-id="32e4d-103">Dá pokyn enumerátor tak, aby přeskočil Další `celt` elementy ve výčtu tak, aby další volání do [IEnumRAWINPUTDEVIC:Next](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md) nevrátí těchto elementů.</span><span class="sxs-lookup"><span data-stu-id="32e4d-103">Instructs the enumerator to skip the next `celt` elements in the enumeration so that the next call to [IEnumRAWINPUTDEVIC:Next](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md) will not return those elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32e4d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32e4d-104">Syntax</span></span>  
  
```  
HRESULT Skip( [in] ULONG celt);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="32e4d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="32e4d-105">Parameters</span></span>  
 `celt`  
  
 <span data-ttu-id="32e4d-106">[v] Počet elementů lze vynechat.</span><span class="sxs-lookup"><span data-stu-id="32e4d-106">[in] Number of elements to be skipped.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="32e4d-107">Hodnota vlastnosti / návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="32e4d-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="32e4d-108">HRESULT: S_OK Pokud je počet elementů zadaný `celt`; S_FALSE jinak.</span><span class="sxs-lookup"><span data-stu-id="32e4d-108">HRESULT: S_OK if the number of elements supplied is `celt`; S_FALSE otherwise.</span></span>
