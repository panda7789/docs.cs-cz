---
title: GetTypeLibInfo – funkce
ms.date: 03/30/2017
api_name:
- GetTypeLibInfo
api_location:
- TlbRef.dll
api_type:
- DLLExport
f1_keywords:
- GetTypeLibInfo
helpviewer_keywords:
- GetTypeLibInfo function [.NET Framework]
ms.assetid: a1c4d165-9bdc-4ca8-940e-292d4ffcc338
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 56a9b97f37240e385dbd1788bafea62578d687a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="gettypelibinfo-function"></a>GetTypeLibInfo – funkce
Vrátí informace o knihovně zadaný typ tak, že prověří jeho [TLIBATTR](https://msdn.microsoft.com/library/ms221376\(v=vs.85\).aspx) struktury.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetTypeLibInfo(  
    [in]   LPWSTR     szFile,  
    [out]  GUID      *pTypeLibID,  
    [out]  LCID      *pTypeLibLCID,  
    [out]  SYSKIND   *pTypeLibPlatform,  
    [out]  USHORT    *pTypeLibMajorVer,  
    [out]  USHORT    *pTypeLibMinorVer  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `szFile`  
 [v] Název souboru knihovny typů.  
  
 `pTypeLibID`  
 [out] Identifikátor GUID knihovny typů.  
  
 `pTypeLibLCID`  
 [out] Lokalizace ID knihovny typů.  
  
 `pTypeLibPlatform`  
 [out] A [SYSKIND](https://msdn.microsoft.com/library/ms221272\(v=vs.85\).aspx) příznak, který identifikuje cílový operační systém pro knihovny typů. Běžné hodnoty jsou SYS_WIN32 a SYS_WIN64.  
  
 `pTypeLibMajorVer`  
 [out] Hlavní číslo verze knihovny typů. Například pro verzi *x.y*, hlavní číslo verze je *x*.  
  
 `pTypeLibMinorVer`  
 [out] Číslo podverze knihovny typů. Například pro verzi *x.y*, je číslo podverze *y*.  
  
## <a name="remarks"></a>Poznámky  
 `GetTypeLibInfo` Funkce je volána [Tlbexp.exe (Exportér knihovny)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md). Tento nástroj generuje knihovny typů, které popisuje typy v sestavení běžné language runtime (CLR).  
  
 Pokud je libovolný parametr hodnotu null, funkce vrátí hodnotu `HRESULT` z `E_POINTER`. Funkce `S_OK`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** TlbRef.h  
  
 **Knihovna:** TlbRef.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Pomocné funkce Tlbexp](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 [LoadTypeLibEx – funkce](https://msdn.microsoft.com/library/ms221249\(v=vs.85\).aspx)
