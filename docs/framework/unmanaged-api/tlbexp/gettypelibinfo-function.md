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
ms.openlocfilehash: d8ea7df9396e9199d04ad5609daa9d2b01761f36
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798890"
---
# <a name="gettypelibinfo-function"></a>GetTypeLibInfo – funkce
Vrátí informace o zadané knihovně typů prozkoumáním její struktury [TLIBATTR](https://docs.microsoft.com/windows/win32/api/oaidl/ns-oaidl-tlibattr) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetTypeLibInfo(  
    [in]   LPWSTR     szFile,  
    [out]  GUID      *pTypeLibID,  
    [out]  LCID      *pTypeLibLCID,  
    [out]  SYSKIND   *pTypeLibPlatform,  
    [out]  USHORT    *pTypeLibMajorVer,  
    [out]  USHORT    *pTypeLibMinorVer  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szFile`  
 pro Název souboru knihovny typů.  
  
 `pTypeLibID`  
 mimo Identifikátor GUID knihovny typů  
  
 `pTypeLibLCID`  
 mimo ID lokalizace knihovny typů.  
  
 `pTypeLibPlatform`  
 mimo Příznak [SYSKIND](https://docs.microsoft.com/windows/win32/api/oaidl/ne-oaidl-syskind) , který identifikuje cílový operační systém pro knihovnu typů. Běžné hodnoty jsou SYS_WIN32 a SYS_WIN64.  
  
 `pTypeLibMajorVer`  
 mimo Hlavní číslo verze knihovny typů. Například pro verzi *x. y*je hlavní číslo verze *x*.  
  
 `pTypeLibMinorVer`  
 mimo Číslo dílčí verze knihovny typů. Například pro verzi *x. y*je číslo dílčí verze *y*.  
  
## <a name="remarks"></a>Poznámky  
 Funkce je volána nástrojem [Tlbexp. exe (Exportér knihovny typů).](../../tools/tlbexp-exe-type-library-exporter.md) `GetTypeLibInfo` Tento nástroj generuje knihovnu typů, která popisuje typy v sestavení modulu CLR (Common Language Runtime).  
  
 Pokud je libovolný parametr null, funkce vrátí hodnotu `HRESULT` z. `E_POINTER` V opačném případě `S_OK`vrátí.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** TlbRef. h  
  
 **Knihovna** TlbRef.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Pomocné funkce Tlbexp](index.md)
- [LoadTypeLibEx – funkce](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
