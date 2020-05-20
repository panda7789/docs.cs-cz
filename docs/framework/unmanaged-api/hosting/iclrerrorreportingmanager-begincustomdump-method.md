---
title: ICLRErrorReportingManager::BeginCustomDump – metoda
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager.BeginCustomDump
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager::BeginCustomDump
helpviewer_keywords:
- ICLRErrorReportingManager::BeginCustomDump method [.NET Framework hosting]
- BeginCustomDump method
ms.assetid: 93424a87-ba13-4fa1-b4dc-69d44437b7ae
topic_type:
- apiref
ms.openlocfilehash: 4c83ffaf920abe005ba987e0a744e13aa0d3c016
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615667"
---
# <a name="iclrerrorreportingmanagerbegincustomdump-method"></a>ICLRErrorReportingManager::BeginCustomDump – metoda
Určuje konfiguraci vlastních výpisů paměti haldy pro zasílání zpráv o chybách.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT BeginCustomDump (  
    [in] ECustomDumpFlavor dwFlavor,  
    [in] DWORD dwNumItems,  
    [in, size_is(dwNumItems), length_is(dwNumItems)] CustomDumpItem items[],  
    DWORD dwReserved  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwFlavor`  
 pro Hodnota [ECustomDumpFlavor –](ecustomdumpflavor-enumeration.md) , která indikuje druh výpisu haldy, na který se má sestavit vlastní výpis paměti.  
  
 `dwNumItems`  
 pro Délka `items` pole. Pokud `dwFlavor` není DUMP_FLAVOR_Mini, `dwNumItems` měla by být nula.  
  
 `items`  
 pro Pole instancí [CustomDumpItem –](customdumpitem-structure.md) určujících položky, které se mají přidat do zkráceného výpisu. Pokud `dwFlavor` není DUMP_FLAVOR_Mini, `items` měl by mít hodnotu null.  
  
 `dwReserved`  
 pro Vyhrazeno pro budoucí použití.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu možné použít. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 `BeginCustomDump`Metoda nastavuje vlastní konfiguraci výpisu paměti haldy. Metoda [EndCustomDump –](iclrerrorreportingmanager-endcustomdump-method.md) vymaže vlastní konfiguraci výpisu paměti haldy a uvolní všechny přidružené stavy. Tato metoda by měla být volána poté, co je dokončen vlastní výpis haldy.  
  
> [!IMPORTANT]
> Selhání volání `EndCustomDump` způsobuje nevrácení paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [CustomDumpItem – struktura](customdumpitem-structure.md)
- [ECustomDumpFlavor – výčet](ecustomdumpflavor-enumeration.md)
- [ICLRErrorReportingManager – rozhraní](iclrerrorreportingmanager-interface.md)
