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
ms.openlocfilehash: 46cd8b5c22f48ba45c4da7fa8876d6807a21f2b3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124142"
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
 mimo Ukazatel na parametr [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) , který obsahuje úplnou cestu knihovny typů s názvem v parametru `bstrSimpleName`.  
  
## <a name="remarks"></a>Poznámky  
 Metoda `ResolveTypeLib` je volána [funkcí LoadTypeLibWithResolver –](loadtypelibwithresolver-function.md) během zpracování [Tlbexp. exe (Exportér knihovny typů)](../../tools/tlbexp-exe-type-library-exporter.md) .  
  
 Vlastní implementace tohoto rozhraní musí vracet [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) , který obsahuje úplnou cestu knihovny typů s názvem v parametru `bstrSimpleName`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** TlbRef. idl, TlbRef. h  
  
 **Knihovna:** TlbRef. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Podpůrné funkce Tlbexp](index.md)
- [LoadTypeLibEx](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
