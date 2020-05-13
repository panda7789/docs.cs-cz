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
ms.openlocfilehash: 020724c422af7cba0165e6f37d0eacb7742153ec
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379263"
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
 pro Velikost `szHostName` vyrovnávací paměti ve znacích. Pokud je tento parametr 0 (nula), `szHostName` musí mít hodnotu null.  
  
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
 Tato metoda je implementována pomocí zapisovače ladicího programu. Musí následovat za vícenásobnými paradigma volání: při prvním volání volající předává hodnotu null do a a `cchHostName` `szHostName` `pcchHostName` vrátí velikost požadované vyrovnávací paměti. Při druhém volání je výše předána velikost, která byla dříve vrácena `cchHostName` , a předána odpovídající velikost vyrovnávací paměti `szHostName` .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** 3,5 SP1  
  
## <a name="see-also"></a>Viz také

- [ICorDebugRemoteTarget – rozhraní](icordebugremotetarget-interface.md)
- [ICorDebug – rozhraní](icordebug-interface.md)
