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
ms.openlocfilehash: 6b9bec757071a98e085ccdeee3fc66bfc07f52bc
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040168"
---
# <a name="loadtypelibwithresolver-function"></a>LoadTypeLibWithResolver – funkce
Načte knihovnu typů a pomocí dodaného [rozhraní ITypeLibResolver –](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) vyřeší všechny interně odkazované knihovny typů.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT LoadTypeLibWithResolver(  
    [in]  LPCOLESTR           szFile,  
    [in]  REGKIND             regkind,  
    [in]  ITypeLibResolver   *pTlbResolver,  
    [out] ITypeLib          **pptlib);  
```  
  
## <a name="parameters"></a>Parametry  
 `szFile`  
 pro Cesta k souboru knihovny typů.  
  
 `regkind`  
 pro Příznak [výčtu REGKIND](https://docs.microsoft.com/windows/win32/api/oleauto/ne-oleauto-regkind) , který určuje, jak je knihovna typů registrována. Možné hodnoty jsou:  
  
- `REGKIND_DEFAULT`: Použijte výchozí chování registrace.  
  
- `REGKIND_REGISTER`: Zaregistrujte tuto knihovnu typů.  
  
- `REGKIND_NONE`: Tuto knihovnu typů neregistrujte.  
  
 `pTlbResolver`  
 pro Ukazatel na implementaci [rozhraní ITypeLibResolver –](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md).  
  
 `pptlib`  
 mimo Odkaz na knihovnu typů, která je načítána.  
  
## <a name="return-value"></a>Návratová hodnota  
 Jedna z hodnot HRESULT, které jsou uvedeny v následující tabulce.  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Nástup.|  
|`E_OUTOFMEMORY`|Nedostatek paměti|  
|`E_POINTER`|Jeden nebo více ukazatelů je neplatných.|  
|`E_INVALIDARG`|Jeden nebo více argumentů je neplatných.|  
|`TYPE_E_IOERROR`|Funkce nemohla zapisovat do souboru.|  
|`TYPE_E_REGISTRYACCESS`|Registrační databázi systému nelze otevřít.|  
|`TYPE_E_INVALIDSTATE`|Knihovnu typů nelze otevřít.|  
|`TYPE_E_CANTLOADLIBRARY`|Knihovnu typů nebo knihovnu DLL nelze načíst.|  
  
## <a name="remarks"></a>Poznámky  
 [Tlbexp. exe (Exportér knihovny typů)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) volá `LoadTypeLibWithResolver` funkci během procesu převodu sestavení na typ knihovny.  
  
 Tato funkce načte zadanou knihovnu typů s minimálním přístupem k registru. Funkce pak prověřuje knihovnu typů pro interně odkazované knihovny typů, z nichž každá musí být načtena a přidána do knihovny nadřazené typu.  
  
 Předtím, než může být načtena odkazovaná knihovna typů, musí být cesta k referenčnímu souboru přeložena na úplnou cestu k souboru. To je provedeno prostřednictvím [metody ResolveTypeLib –](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md) , která je poskytována [rozhraním ITypeLibResolver –](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md), které je `pTlbResolver` předáno v parametru.  
  
 Je-li známa úplná cesta k souboru odkazované knihovny typů, `LoadTypeLibWithResolver` funkce načte a přidá odkazovanou knihovnu typů do nadřazené knihovny typů a vytvoří kombinovanou hlavní knihovnu typů.  
  
 Poté, co funkce vyřeší a načte všechny interně odkazované knihovny typů, vrátí odkaz na hlavní přeloženou knihovnu typů v `pptlib` parametru.  
  
 Funkce je obecně volána nástrojem [Tlbexp. exe (Exportér knihovny typů)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), který poskytuje svou vlastní interní implementaci `pTlbResolver` [rozhraní ITypeLibResolver –](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) v parametru. `LoadTypeLibWithResolver`  
  
 Pokud voláte `LoadTypeLibWithResolver` přímo, musíte dodat vlastní implementaci [rozhraní ITypeLibResolver –](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlaviček** TlbRef. h  
  
 **Knihovna** TlbRef.lib  
  
 **Verze .NET Framework:** 3,5, 3,0, 2,0  
  
## <a name="see-also"></a>Viz také:

- [Pomocné funkce Tlbexp](../../../../docs/framework/unmanaged-api/tlbexp/index.md)
- [LoadTypeLibEx – funkce](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
