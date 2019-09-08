---
title: ResolveTypeLib – metoda
ms.date: 03/30/2017
api_name:
- ResolveTypeLib
api_location:
- tlbref.dll
f1_keywords:
- ResolveTypeLib
helpviewer_keywords:
- ITypeLibResolver::ResolveTypeLib method [.NET Framework]
- ResolveTypeLib method [.NET Framework]
ms.assetid: 95d2aa0d-8eeb-4a9f-a216-5249f7e2c167
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce0f11547d4b16516b7c78d1b1947f5c4bc831a3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798797"
---
# <a name="resolvetypelib-method"></a>ResolveTypeLib – metoda
Vyřeší jednoduchý název knihovny typů vrácením jeho plně kvalifikované cesty.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ResolveTypeLib(  
    [in]  BSTR      bstrSimpleName,  
    [in]  GUID      tlbid,  
    [in]  LCID      lcid,  
    [in]  USHORT    wMajorVersion,  
    [in]  USHORT    wMinorVersion,  
    [in]  SYSKIND   syskind,  
    [out] BSTR     *pbstrResolvedTlbName);  
```  
  
## <a name="parameters"></a>Parametry  
 `bstrSimpleName`  
 pro Typ [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) , který obsahuje jednoduchý název knihovny typů.  
  
 `tlbid`  
 pro Identifikátor GUID přiřazený knihovně typů v registru.  
  
 `lcid`  
 pro ID lokalizace knihovny typů.  
  
 `wMajorVersion`  
 pro Hlavní číslo verze knihovny typů. Například pro verzi *x. y*je hlavní číslo verze *x*.  
  
 `wMinorVersion`  
 pro Číslo dílčí verze knihovny typů. Například pro verzi *x. y*je číslo dílčí verze *y*.  
  
 `syskind`  
 pro Příznak [SYSKIND](https://docs.microsoft.com/windows/win32/api/oaidl/ne-oaidl-syskind) , který identifikuje operační prostředí. Běžné hodnoty jsou SYS_WIN32 a SYS_WIN64.  
  
 `pbstrResolvedTlbName`  
 mimo Ukazatel na parametr [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) , který obsahuje úplnou cestu knihovny typů s názvem v `bstrSimpleName` parametru.  
  
## <a name="remarks"></a>Poznámky  
 Metoda je volána [funkcí LoadTypeLibWithResolver –](loadtypelibwithresolver-function.md) během zpracování [Tlbexp. exe (Exportér knihovny typů).](../../tools/tlbexp-exe-type-library-exporter.md) `ResolveTypeLib`  
  
 Vlastní implementace tohoto rozhraní musí vracet [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) , který obsahuje úplnou cestu knihovny typů s názvem v `bstrSimpleName` parametru.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** TlbRef. idl, TlbRef. h  
  
 **Knihovna** TlbRef.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Pomocné funkce Tlbexp](index.md)
- [LoadTypeLibEx](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
