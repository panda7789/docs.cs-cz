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
ms.openlocfilehash: 96a9672ee05cb1fe2573620bd1dea23e57339c93
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="resolvetypelib-method"></a>ResolveTypeLib – metoda
Přeloží jednoduchý název knihovny typů vrácením jeho plně kvalifikovanou cestu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ResolveTypeLib(  
    [in]  BSTR      bstrSimpleName,  
    [in]  GUID      tlbid,  
    [in]  LCID      lcid,  
    [in]  USHORT    wMajorVersion,  
    [in]  USHORT    wMinorVersion,  
    [in]  SYSKIND   syskind,  
    [out] BSTR     *pbstrResolvedTlbName);  
```  
  
#### <a name="parameters"></a>Parametry  
 `bstrSimpleName`  
 [v] A [BSTR](http://msdn.microsoft.com/library/1b2d7d2c-47af-4389-a6b6-b01b7e915228) obsahující jednoduchý název knihovny typů.  
  
 `tlbid`  
 [v] Identifikátor GUID přiřazený knihovny typů v registru.  
  
 `lcid`  
 [v] Lokalizace ID knihovny typů.  
  
 `wMajorVersion`  
 [v] Hlavní číslo verze knihovny typů. Například pro verzi *x.y*, hlavní číslo verze je *x*.  
  
 `wMinorVersion`  
 [v] Číslo podverze knihovny typů. Například pro verzi *x.y*, je číslo podverze *y*.  
  
 `syskind`  
 [v] A [SYSKIND](http://msdn.microsoft.com/library/662048b2-59a8-48ca-9e4f-2f9a5306faa1) příznak, který identifikuje provozní prostředí. Běžné hodnoty jsou SYS_WIN32 a SYS_WIN64.  
  
 `pbstrResolvedTlbName`  
 [out] Ukazatel [BSTR](http://msdn.microsoft.com/library/1b2d7d2c-47af-4389-a6b6-b01b7e915228) obsahující úplnou cestu knihovny typů s názvem v `bstrSimpleName` parametr.  
  
## <a name="remarks"></a>Poznámky  
 `ResolveTypeLib` Metoda je volána [loadtypelibwithresolver – funkce](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md) během [Tlbexp.exe (Exportér knihovny)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) zpracování.  
  
 Vlastní implementace tohoto rozhraní musí vracet [BSTR](http://msdn.microsoft.com/library/1b2d7d2c-47af-4389-a6b6-b01b7e915228) obsahující úplnou cestu knihovny typů s názvem v `bstrSimpleName` parametr.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** TlbRef.idl, TlbRef.h  
  
 **Knihovna:** TlbRef.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Pomocné funkce Tlbexp](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 [LoadTypeLibEx](http://msdn.microsoft.com/library/56a7f9e1-810b-4a42-aa4d-691f4304f5ef)
