---
title: IEnumRAWINPUTDEVIC:Skip
ms.date: 03/30/2017
helpviewer_keywords:
- Skip method [WPF]
ms.assetid: c967b0f8-1c6a-459c-8c16-d4f08918ab65
ms.openlocfilehash: f7d7df77c54d4551025aa5a344c96083c263f455
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57467165"
---
# <a name="ienumrawinputdevicskip"></a>IEnumRAWINPUTDEVIC:Skip
Dává pokyn enumerátorem přeskočit na další `celt` elementy ve výčtu tak, aby na další volání [IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md) nevrátí tyto elementy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Skip( [in] ULONG celt);  
```  
  
## <a name="parameters"></a>Parametry  
 `celt`  
  
 [in] Počet prvků, které mají být přeskočeny.  
  
## <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota  
 HODNOTA HRESULT: S_OK, pokud je počet elementů zadaný `celt`; S_FALSE jinak.
