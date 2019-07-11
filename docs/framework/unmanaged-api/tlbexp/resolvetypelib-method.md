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
ms.openlocfilehash: 0b6db8925fb966f4a8b2a213b0d6e340d0edf107
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756425"
---
# <a name="resolvetypelib-method"></a>ResolveTypeLib – metoda
Přeloží jednoduchý název knihovny typů tak, že vrací jeho úplnou cestu.  
  
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
 [in] A [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) , který obsahuje jednoduchý název knihovny typů.  
  
 `tlbid`  
 [in] Identifikátor GUID přiřazený do knihovny typů v registru.  
  
 `lcid`  
 [in] ID lokalizace knihovny typů.  
  
 `wMajorVersion`  
 [in] Číslo hlavní verze knihovny typů. Například pro verzi *x.y*, je číslo hlavní verze *x*.  
  
 `wMinorVersion`  
 [in] Číslo podverze knihovny typů. Například pro verzi *x.y*, je číslo podverze *y*.  
  
 `syskind`  
 [in] A [SYSKIND](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ne-oaidl-tagsyskind) příznak, který identifikuje provozní prostředí. Běžné hodnoty jsou SYS_WIN32 a SYS_WIN64.  
  
 `pbstrResolvedTlbName`  
 [out] Ukazatel [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) obsahující úplnou cestu knihovny typů s názvem v `bstrSimpleName` parametru.  
  
## <a name="remarks"></a>Poznámky  
 `ResolveTypeLib` Metoda je volána [loadtypelibwithresolver – funkce](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md) během [Tlbexp.exe (Exportér knihovny typů)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) zpracování.  
  
 Vlastní implementace tohoto rozhraní musí vrátit [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) obsahující úplnou cestu knihovny typů s názvem v `bstrSimpleName` parametru.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** TlbRef.idl, TlbRef.h  
  
 **Knihovna:** TlbRef.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Pomocné funkce Tlbexp](../../../../docs/framework/unmanaged-api/tlbexp/index.md)
- [LoadTypeLibEx](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
