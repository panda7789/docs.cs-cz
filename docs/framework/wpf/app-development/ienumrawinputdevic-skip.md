---
title: IEnumRAWINPUTDEVIC:Skip
ms.date: 03/30/2017
helpviewer_keywords:
- Skip method [WPF]
ms.assetid: c967b0f8-1c6a-459c-8c16-d4f08918ab65
ms.openlocfilehash: a74f71345a22f6d766c2d5966ca5d2cb33ab756e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053379"
---
# <a name="ienumrawinputdevicskip"></a>IEnumRAWINPUTDEVIC:Skip
Instruuje enumerátor pro přeskočení dalších `celt` prvků výčtu, aby další volání [IEnumRAWINPUTDEVIC: Next](ienumrawinputdevic-next.md) nevrátí tyto prvky.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Skip( [in] ULONG celt);  
```  
  
## <a name="parameters"></a>Parametry  
 `celt`  
  
 pro Počet prvků, které mají být přeskočeny.  
  
## <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota  
 HRESULT S_OK, pokud je `celt`zadaný počet prvků; S_FALSE jinak.
