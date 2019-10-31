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
ms.openlocfilehash: 82fa0903474ee04b767fd9c68812efe7f0cc4fa0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124163"
---
# <a name="loadtypelibwithresolver-function"></a>LoadTypeLibWithResolver – funkce
Načte knihovnu typů a pomocí dodaného [rozhraní ITypeLibResolver –](itypelibresolver-interface.md) vyřeší všechny interně odkazované knihovny typů.  
  
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
  
- `REGKIND_DEFAULT`: použijte výchozí chování registrace.  
  
- `REGKIND_REGISTER`: Zaregistrujte tuto knihovnu typů.  
  
- `REGKIND_NONE`: neregistrujte tuto knihovnu typů.  
  
 `pTlbResolver`  
 pro Ukazatel na implementaci [rozhraní ITypeLibResolver –](itypelibresolver-interface.md).  
  
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
 [Tlbexp. exe (Exportér knihovny typů)](../../tools/tlbexp-exe-type-library-exporter.md) volá funkci `LoadTypeLibWithResolver` během procesu převodu sestavení na typ knihovny.  
  
 Tato funkce načte zadanou knihovnu typů s minimálním přístupem k registru. Funkce pak prověřuje knihovnu typů pro interně odkazované knihovny typů, z nichž každá musí být načtena a přidána do knihovny nadřazené typu.  
  
 Předtím, než může být načtena odkazovaná knihovna typů, musí být cesta k referenčnímu souboru přeložena na úplnou cestu k souboru. To je provedeno prostřednictvím [metody ResolveTypeLib –](resolvetypelib-method.md) , která je poskytována [rozhraním ITypeLibResolver –](itypelibresolver-interface.md), které je předáno v parametru `pTlbResolver`.  
  
 Je-li známa úplná cesta k souboru odkazované knihovny typů, funkce `LoadTypeLibWithResolver` načte a přidá odkazovanou knihovnu typů do nadřazené knihovny typů a vytvoří kombinovanou hlavní knihovnu typů.  
  
 Poté, co funkce vyřeší a načte všechny interně odkazované knihovny typů, vrátí odkaz na hlavní přeloženou knihovnu typů v parametru `pptlib`.  
  
 Funkce `LoadTypeLibWithResolver` je obecně volána nástrojem [Tlbexp. exe (Exportér knihovny typů)](../../tools/tlbexp-exe-type-library-exporter.md), který poskytuje svou vlastní interní implementaci [rozhraní itypelibresolver –](itypelibresolver-interface.md) v parametru `pTlbResolver`.  
  
 Pokud zavoláte `LoadTypeLibWithResolver` přímo, musíte dodat vlastní implementaci [rozhraní ITypeLibResolver –](itypelibresolver-interface.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** TlbRef. h  
  
 **Knihovna:** TlbRef. lib  
  
 **Verze .NET Framework:** 3,5, 3,0, 2,0  
  
## <a name="see-also"></a>Viz také:

- [Podpůrné funkce Tlbexp](index.md)
- [LoadTypeLibEx – funkce](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
