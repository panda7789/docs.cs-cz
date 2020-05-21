---
title: ICorRuntimeHost::Stop – metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.Stop
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::Stop
helpviewer_keywords:
- Stop method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Stop method [.NET Framework hosting]
ms.assetid: 46a0d450-b516-4bef-8b71-8d3bf265cbed
topic_type:
- apiref
ms.openlocfilehash: 4117c1297f02032fda80520a7709833217ec94b1
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762692"
---
# <a name="icorruntimehoststop-method"></a>ICorRuntimeHost::Stop – metoda
Zastaví provádění kódu v modulu runtime pro aktuální proces.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Stop ();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Operace byla úspěšná.|  
|S_FALSE|Operaci se nepodařilo dokončit.|  
|E_FAIL|Došlo k neznámému a závažnému selhání. Pokud metoda vrátí E_FAIL, modul CLR (Common Language Runtime) již nebude v procesu použit. Následná volání všech hostitelských rozhraní API vrací HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
  
## <a name="remarks"></a>Poznámky  
 Obvykle není nutné volat `Stop` metodu, protože kód se zastaví, když se proces ukončí.  
  
> [!NOTE]
> Po volání do nástroje `Stop` nelze modul CLR znovu inicializovat do stejného procesu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** 1,0, 1,1  
  
## <a name="see-also"></a>Viz také

- [ICorRuntimeHost – rozhraní](icorruntimehost-interface.md)
