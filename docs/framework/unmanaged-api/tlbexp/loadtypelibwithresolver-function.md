---
title: LoadTypeLibWithResolver – funkce
ms.date: 03/30/2017
api_name:
- LoadTypeLibWithResolver
api_location:
- TlbRef.dll
api_type:
- DLLExport
f1_keywords:
- LoadTypeLibWithResolver
helpviewer_keywords:
- LoadTypeLibWithResolver function [.NET Framework]
ms.assetid: 7123a89b-eb9b-463a-a552-a081e33b0a3a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b6a217e2212bb900d7ba83ccdd9cb00d30454baf
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45625721"
---
# <a name="loadtypelibwithresolver-function"></a>LoadTypeLibWithResolver – funkce
Načte knihovnu typů a použije zadané [itypelibresolver – rozhraní](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) vyřešit jakékoli interně odkazované knihovny typů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT LoadTypeLibWithResolver(  
    [in]  LPCOLESTR           szFile,  
    [in]  REGKIND             regkind,  
    [in]  ITypeLibResolver   *pTlbResolver,  
    [out] ITypeLib          **pptlib);  
```  
  
#### <a name="parameters"></a>Parametry  
 `szFile`  
 [in] Cesta k souboru knihovny typů.  
  
 `regkind`  
 [in] A [REGKIND výčet](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/ne-oleauto-tagregkind) příznak, který určuje způsob registrace knihovny typů. Jeho možné hodnoty jsou:  
  
-   `REGKIND_DEFAULT`: Použije výchozí chování registrace.  
  
-   `REGKIND_REGISTER`: Zaregistrujte tuto knihovnu typů.  
  
-   `REGKIND_NONE`: Neregistrujte tuto knihovnu typů.  
  
 `pTlbResolver`  
 [in] Ukazatel na implementaci [itypelibresolver – rozhraní](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md).  
  
 `pptlib`  
 [out] Odkaz na knihovnu typů, který se načítá.  
  
## <a name="return-value"></a>Návratová hodnota  
 Jedna z hodnot HRESULT uvedené v následující tabulce.  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Úspěch.|  
|`E_OUTOFMEMORY`|Nedostatek paměti|  
|`E_POINTER`|Jeden nebo více ukazatelů jsou neplatné.|  
|`E_INVALIDARG`|Jeden nebo více argumentů nejsou platné.|  
|`TYPE_E_IOERROR`|Funkce nemůže zapisovat do souboru.|  
|`TYPE_E_REGISTRYACCESS`|Nelze otevřít systémové registrační databázi.|  
|`TYPE_E_INVALIDSTATE`|Knihovnu typů nelze otevřít.|  
|`TYPE_E_CANTLOADLIBRARY`|Nelze načíst knihovnu typů nebo knihovny DLL.|  
  
## <a name="remarks"></a>Poznámky  
 [Tlbexp.exe (Exportér knihovny typů)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) volání `LoadTypeLibWithResolver` funkce během procesu převodu sestavení na typu knihovny.  
  
 Tato funkce načte zadanou knihovnu typů s minimální přístup k registru. Funkce zkontroluje knihovnu typů pro interně odkazované knihovny typů, z nichž každý musí být načten a přidány do knihovny nadřazeného typu.  
  
 Předtím, než je možné načíst odkazovanou knihovnu typů, cesta k souboru jeho odkazu musí přeložit na úplnou cestu. To lze provést prostřednictvím [resolvetypelib – metoda](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md) poskytnutou neregistrovaným [itypelibresolver – rozhraní](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md), který je předán `pTlbResolver` parametru.  
  
 Pokud známý úplné cesty k souboru z odkazované knihovny typů `LoadTypeLibWithResolver` funkce načte a přidá do nadřazené knihovny typů, vytváření knihovny typů kombinované hlavní odkazované knihovny typů.  
  
 Poté, co funkce odstraňuje a načte všechna interně odkazované knihovny typů, vrátí odkaz na hlavní rozpoznaný typ knihovny `pptlib` parametru.  
  
 `LoadTypeLibWithResolver` Funkce je obvykle volána [Tlbexp.exe (Exportér knihovny typů)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), který dodává své vlastní interní [itypelibresolver – rozhraní](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementace `pTlbResolver` parametr.  
  
 Při volání `LoadTypeLibWithResolver` přímo, je nutné zadat vlastní [itypelibresolver – rozhraní](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** TlbRef.h  
  
 **Knihovna:** TlbRef.lib  
  
 **Verze rozhraní .NET framework:** 3.5, 3.0, 2.0  
  
## <a name="see-also"></a>Viz také  
 [Pomocné funkce Tlbexp](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 [LoadTypeLibEx – funkce](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
