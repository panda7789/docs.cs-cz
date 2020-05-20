---
title: ISymUnmanagedAsyncMethod::IsAsyncMethod – metoda
ms.date: 03/30/2017
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
ms.openlocfilehash: 91b4c2688dadf12fa4a835a662622267d7831cf8
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441796"
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a>ISymUnmanagedAsyncMethod::IsAsyncMethod – metoda
Kontroluje, zda metoda obsahuje asynchronní informace nebo nikoli.  
  
 Pokud se tato metoda vrátí `FALSE` , je neplatná pro volání jakékoli jiné metody v tomto rozhraní. Budou `E_UNEXPECTED` v tomto případě vráceny.  
  
## <a name="syntax"></a>Syntaxe  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
## <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrací objekt `HRESULT`.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také

- [ISymUnmanagedAsyncMethod – rozhraní](isymunmanagedasyncmethod-interface.md)
