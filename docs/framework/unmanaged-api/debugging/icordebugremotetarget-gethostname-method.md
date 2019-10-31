---
title: ICorDebugRemoteTarget::GetHostName – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugRemoteTarget.GetHostName
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::GetHostName
helpviewer_keywords:
- ICorDebugRemoteTarget::GetHostName method [.NET Framework debugging]
- GetHostName method, ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: 1c7276f7-7e54-470c-808c-e13745ac07a1
topic_type:
- apiref
ms.openlocfilehash: a9a6ca9ae3cdb1c6a7398d08c9f99e3cde125cf6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131899"
---
# <a name="icordebugremotetargetgethostname-method"></a>ICorDebugRemoteTarget::GetHostName – metoda
Vrátí plně kvalifikovaný název domény nebo IPv4 adresu cílového počítače vzdáleného ladění. Protokol IPV6 se v tuto chvíli nepodporuje.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetHostName (  
    [in] ULONG32      cchHostName,  
    [out] ULONG32*    pcchHostName,  
    [out, size_is(cchHostName), length_is(*pcchHostName)]  
            WCHAR szHostName[]  
```  
  
## <a name="parameters"></a>Parametry  
 `cchHostName`  
 pro Velikost vyrovnávací paměti `szHostName` v znacích. Pokud je tento parametr 0 (nula), `szHostName` musí mít hodnotu null.  
  
 `pcchHostName`  
 mimo Počet znaků, včetně ukončovacího znaku null, v názvu hostitele nebo IP adrese. Tento parametr může mít hodnotu null.  
  
 `szHostName`  
 mimo Vyrovnávací paměť, která obsahuje název hostitele nebo IP adresu.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 Název hostitele nebo IP adresa se úspěšně vrátily.  
  
 E_FAIL (nebo jiné návratové kódy E_)  
 Nelze vrátit název hostitele nebo IP adresu.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je implementována pomocí zapisovače ladicího programu. Musí následovat za vícenásobnými paradigma volání: při prvním volání volající předává hodnotu null do obou `cchHostName` i `szHostName`a `pcchHostName` vrací velikost požadované vyrovnávací paměti. Při druhém volání je výše vrácená velikost předána do `cchHostName`a v `szHostName`předává patřičnou velikost vyrovnávací paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** 3,5 SP1  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugRemoteTarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [ICorDebug – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
