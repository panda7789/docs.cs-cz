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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf35715564e58f1811618b6859a860008e9660c4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54655397"
---
# <a name="icordebugremotetargetgethostname-method"></a>ICorDebugRemoteTarget::GetHostName – metoda
Vrátí plně kvalifikovaný název domény nebo adresu IPv4 cílového počítače vzdáleného ladění. Protokol IPV6 není v tuto chvíli nepodporuje.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetHostName (  
    [in] ULONG32      cchHostName,  
    [out] ULONG32*    pcchHostName,  
    [out, size_is(cchHostName), length_is(*pcchHostName)]  
            WCHAR szHostName[]  
```  
  
#### <a name="parameters"></a>Parametry  
 `cchHostName`  
 [in] Velikost ve znacích, nástroje `szHostName` vyrovnávací paměti. Pokud tento parametr je 0 (nula), `szHostName` musí mít hodnotu null.  
  
 `pcchHostName`  
 [out] Počet znaků, včetně null zakončení, v názvu hostitele nebo IP adresu. Tento parametr může mít hodnotu null.  
  
 `szHostName`  
 [out] Vyrovnávací paměť, která obsahuje název hostitele nebo IP adresu.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 Název hostitele nebo IP adresa byla úspěšně vrácena.  
  
 E_FAIL (nebo jiné E_ návratové kódy)  
 Nelze vrátit název hostitele nebo IP adresu.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je implementována zapisovačem ladicího programu. Je nutné postupovat podle paradigmatu více volání: Při prvním volání volající předá hodnotu null pro obě `cchHostName` a `szHostName`, a `pcchHostName` vrátí velikost požadované vyrovnávací paměti. Při druhém volání je dříve vrácená velikost předána v `cchHostName`, a odpovídající velikosti vyrovnávací paměti je předáno `szHostName`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** 3.5 SP1  
  
## <a name="see-also"></a>Viz také:
- [ICorDebugRemoteTarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [ICorDebug – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
