---
title: "LoadTypeLibWithResolver – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LoadTypeLibWithResolver
api_location: TlbRef.dll
api_type: DLLExport
f1_keywords: LoadTypeLibWithResolver
helpviewer_keywords: LoadTypeLibWithResolver function [.NET Framework]
ms.assetid: 7123a89b-eb9b-463a-a552-a081e33b0a3a
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f069d09f25575c39db097024384ad1bf14eaaf02
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="loadtypelibwithresolver-function"></a>LoadTypeLibWithResolver – funkce
Načte knihovny typů a používá zadaných [itypelibresolver – rozhraní](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) vyřešit všechny knihovny interně odkazovaného typu.  
  
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
 [v] Cesta k souboru knihovny typů.  
  
 `regkind`  
 [v] A [REGKIND výčtu](https://msdn.microsoft.com/library/windows/desktop/ms221159.aspx) příznak, který řídí, jak zaregistrovat knihovnu typů. Jeho možné hodnoty jsou:  
  
-   `REGKIND_DEFAULT`: Použijte výchozí chování registrace.  
  
-   `REGKIND_REGISTER`: Zaregistrujte tuto knihovnu typů.  
  
-   `REGKIND_NONE`: Neregistrovat toto knihovny typů.  
  
 `pTlbResolver`  
 [v] Ukazatel na implementaci [itypelibresolver – rozhraní](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md).  
  
 `pptlib`  
 [out] Odkaz na knihovnu typů, který je právě načítán.  
  
## <a name="return-value"></a>Návratová hodnota  
 Jedna z hodnot HRESULT uvedené v následující tabulce.  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Úspěch.|  
|`E_OUTOFMEMORY`|Nedostatek paměti|  
|`E_POINTER`|Jeden nebo více následující ukazatele jsou neplatné.|  
|`E_INVALIDARG`|Jeden nebo více parametrů jsou neplatné.|  
|`TYPE_E_IOERROR`|Funkci nelze zapisovat do souboru.|  
|`TYPE_E_REGISTRYACCESS`|Registrační databáze systému nelze otevřít.|  
|`TYPE_E_INVALIDSTATE`|Knihovny typů nelze otevřít.|  
|`TYPE_E_CANTLOADLIBRARY`|Nelze načíst knihovny typů nebo DLL.|  
  
## <a name="remarks"></a>Poznámky  
 [Tlbexp.exe (Exportér knihovny)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) volání `LoadTypeLibWithResolver` funkce během procesu převodu sestavení na typu knihovny.  
  
 Tato funkce načte knihovnu zadaného typu s minimální přístup k registru. Funkce zkontroluje knihovnu typů pro interně odkazovaného typu knihovny, každý z nich musí být načteny a přidány do knihovny nadřazeného typu.  
  
 Předtím, než můžete načíst knihovnu odkazovaného typu, musí být vyřešeny jeho cesta k souboru odkaz na úplnou cestu. To se provádí prostřednictvím [resolvetypelib – metoda](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md) který zajišťuje [itypelibresolver – rozhraní](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md), který se předává v `pTlbResolver` parametr.  
  
 Pokud je úplná cesta odkazovaného typu knihovny se označuje, `LoadTypeLibWithResolver` funkce načte a přidá odkazovaného typu knihovny do knihovny typů nadřazenou, vytvoření knihovny kombinované hlavní typu.  
  
 Po funkce přeloží a načte všechny knihovny interně odkazovaného typu, vrátí odkaz na knihovnu hlavní přeložit typ v `pptlib` parametr.  
  
 `LoadTypeLibWithResolver` Funkce obecně volá [Tlbexp.exe (Exportér knihovny)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), které poskytuje vlastní interní [itypelibresolver – rozhraní](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementace v `pTlbResolver` parametr.  
  
 Když zavoláte `LoadTypeLibWithResolver` přímo, je nutné zadat vlastní [itypelibresolver – rozhraní](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** TlbRef.h  
  
 **Knihovna:** TlbRef.lib  
  
 **Verze rozhraní .NET framework:** 3.5, 2.0 a 3.0  
  
## <a name="see-also"></a>Viz také  
 [Pomocné funkce Tlbexp](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 [LoadTypeLibEx – funkce](https://msdn.microsoft.com/library/windows/desktop/ms221249\(v=vs.85\).aspx)
