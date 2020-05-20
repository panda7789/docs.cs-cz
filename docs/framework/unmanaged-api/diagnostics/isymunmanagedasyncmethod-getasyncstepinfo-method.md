---
title: ISymUnmanagedAsyncMethod::GetAsyncStepInfo – metoda
ms.date: 03/30/2017
ms.assetid: 3ef5b4b8-4ac7-4906-849b-f932c5e3db07
ms.openlocfilehash: e3c0d7b8eeded403ce8391cff00ee18dccc38ed5
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441887"
---
# <a name="isymunmanagedasyncmethodgetasyncstepinfo-method"></a>ISymUnmanagedAsyncMethod::GetAsyncStepInfo – metoda
Viz [Metoda defineasyncstepinfo –](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```idl  
HRESULT GetAsyncStepInfo(    [in] ULONG32 cStepInfo,    [out] ULONG32 *pcStepInfo,    [in, size_is(cStepInfo)] ULONG32 yieldOffsets[],    [in, size_is(cStepInfo)] ULONG32 breakpointOffset[],    [in, size_is(cStepInfo)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`cStepInfo`||  
|`pcStepInfo`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrací objekt `HRESULT`.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také

- [ISymUnmanagedAsyncMethod – rozhraní](isymunmanagedasyncmethod-interface.md)
