---
title: ISymUnmanagedENCUpdate::InitializeForEnc – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.InitializeForEnc
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::InitializeForEnc
helpviewer_keywords:
- ISymUnmanagedENCUpdate::InitializeForEnc method [.NET Framework debugging]
- InitializeForEnc method [.NET Framework debugging]
ms.assetid: 796b2154-b53c-4d07-9e67-80fd6064725a
topic_type:
- apiref
ms.openlocfilehash: 220788a38cd0ff90fed3b681a161c579206cf805
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449015"
---
# <a name="isymunmanagedencupdateinitializeforenc-method"></a>ISymUnmanagedENCUpdate::InitializeForEnc – metoda
Umožňuje vypočítat hranice metod před prvním voláním metody [ISymUnmanagedENCUpdate:: updatesymbolstore2 –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT InitializeForEnc();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedENCUpdate – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
