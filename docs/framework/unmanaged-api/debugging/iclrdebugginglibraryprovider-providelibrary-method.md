---
title: "ICLRDebuggingLibraryProvider::ProvideLibrary – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebuggingLibraryProvider.ProvideLibrary Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDebuggingLibraryProvider::ProvideLibrary
helpviewer_keywords:
- ProvideLibrary method [.NET Framework debugging]
- ICLRDebuggingLibraryProvider::ProvideLibrary method [.NET Framework debugging]
ms.assetid: 86f06245-9517-49be-8d8c-ca5deaf34c02
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cf6860a616312504e3d23177734cb532405bd714
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdebugginglibraryproviderprovidelibrary-method"></a>ICLRDebuggingLibraryProvider::ProvideLibrary – metoda
Získá zprostředkovatele knihovny rozhraní zpětné volání, které umožňuje common language runtime (CLR) specifické pro verzi ladění lze knihoven najít a načíst na vyžádání.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ProvideLibrary(  
     [in] const WCHAR* pwszFileName,  
     [in] DWORD dwTimestamp,  
     [in] DWORD dwSizeOfImage,  
     [out] HMODULE* hModule);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pwszFilename`  
 [v] Název modulu požadováno.  
  
 `dwTimestamp`  
 [v] Časové razítko uložené v záhlaví souboru COFF PE souborů.  
  
 `pLibraryProvider`  
 [v] `SizeOfImage` Pole, které jsou uložené v hlavičce COFF volitelný soubor PE souborů.  
  
 `hModule`  
 [out] Popisovač požadovaný modul.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
  
## <a name="exceptions"></a>Výjimky  
  
## <a name="remarks"></a>Poznámky  
 `ProvideLibrary`umožňuje zajistit moduly, které jsou potřebné pro ladění konkrétní soubory CLR například mscordbi.dll a souboru mscordacwks.dll ladicího programu. Obslužné rutiny modulu muset nadále platné dokud volání [iclrdebugging::canunloadnow –](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md) metoda označuje, že může být uvolněno na bod, který je odpovědností volajícího k bezplatným obslužné rutiny pro zpracování.  
  
 Ladicí program může používat všechny dostupné prostředky sami nebo můžete pořídit ladění modulu.  
  
> [!IMPORTANT]
>  Tato funkce umožňuje rozhraní API volajícímu zadat modulů, které obsahují spustitelný soubor a potenciálně škodlivý kód. Jako bezpečnostní opatření, neměli používat volající `ProvideLibrary` distribuovat žádný kód, že není chtěl provést sám sebe.  
>   
>  Pokud je zjištěno porušení zabezpečení závažné již vydaných knihovny, například mscordbi.dll nebo souboru mscordacwks.dll, dá shimu opravit rozpoznat chybná verze souborů. Shim lze vydávat žádosti pro nainstalovanou opravou verze souborů a odmítnout chybná verze, pokud se poskytnou v reakci na žádnou žádostí. Tato situace může nastat, pouze v případě, že uživatel má opravit na novou verzi shim. Neopravené verze zůstane ohrožen.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
