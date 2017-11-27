---
title: "ICorDebugMetaDataLocator::GetMetaData – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugMetaDataLocator.GetMetaData
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugMetaDataLocator::GetMetaData
helpviewer_keywords:
- ICorDebugMetaDataLocator::GetMetaData method [.NET Framework debugging]
- GetMetaData method, ICorDebugMetaDataLocator interface [.NET Framework debugging]
ms.assetid: f9b0ff22-54db-45eb-9cc3-508000a3141d
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 42c0548a626d43592184efa92619e74446058d58
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmetadatalocatorgetmetadata-method"></a>ICorDebugMetaDataLocator::GetMetaData – metoda
Požádá ladicí program na vrátit úplnou cestu k modulu, jehož metadat je potřebný pro dokončení operace, které požadovali ladicího programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetMetaData(  
      [in] LPCWSTR wszImagePath,  
      [in] DWORD   dwImageTimeStamp,  
      [in] DWORD   dwImageSize,  
      [in] ULONG32 cchPathBuffer,  
      [out] ULONG32 * pcchPathBuffer,  
      [out, size_is(cchPathBuffer), length_is(*pcchPathBuffer)]  
               WCHAR wszPathBuffer[]  
      );  
```  
  
#### <a name="parameters"></a>Parametry  
 `wszImagePath`  
 [v] Řetězec ukončené hodnotou null, který představuje úplnou cestu k souboru. Pokud je úplná cesta není k dispozici, název a příponu souboru (*filename*. *rozšíření*).  
  
 `dwImageTimeStamp`  
 [v] Časové razítko z hlavičky souboru obrázku PE. Tento parametr může potenciálně použít pro symbol server ([SymSrv](http://msdn.microsoft.com/library/cc266470.aspx)) vyhledávání.  
  
 `dwImageSize`  
 [v] Velikost bitové kopie z hlavičky souboru PE. Tento parametr může potenciálně použít pro vyhledávání SymSrv.  
  
 `cchPathBuffer`  
 [v] Znak počet za `wszPathBuffer`.  
  
 `pcchPathBuffer`  
 [out] Počet `WCHAR`s zapsána do `wszPathBuffer`.  
  
 Pokud metoda vrátí E_NOT_SUFFICIENT_BUFFER, obsahuje počet `WCHAR`s potřebný k uložení cestu.  
  
 `wszPathBuffer`  
 [out] Ukazatel na vyrovnávací paměť, do kterého bude ladicí program zkopírovat úplnou cestu souboru, který obsahuje požadovaná metadata.  
  
 `ofReadOnly` Příznak z [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) výčtu slouží k vyžádání přístup jen pro čtení k metadatům v tomto souboru.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda. Všechny ostatní hodnoty HRESULT selhání znamenat, že soubor není dá načíst.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena. `wszPathBuffer`obsahuje úplnou cestu k souboru a je ukončené hodnotou null.|  
|E_NOT_SUFFICIENT_BUFFER|Aktuální velikost `wszPathBuffer` není dostatečná pro uložení úplnou cestu. V takovém případě `pcchPathBuffer` obsahuje potřebný počet `WCHAR`s, včetně ukončující prázdný znak, a `GetMetaData` se nazývá znovu s požadovanou vyrovnávací paměť.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud `wszImagePath` obsahuje úplnou cestu pro modul z výpis, určuje cestu z počítače, kde byl shromážděn výpis. Tento soubor pravděpodobně neexistuje v tomto umístění nebo nesprávný soubor se stejným názvem, můžou být uložené na cestě.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Icordebugthread4 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 [Ladění v rozhraní](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
