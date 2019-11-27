---
title: ISymUnmanagedENCUpdate – rozhraní
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate
helpviewer_keywords:
- ISymUnmanagedENCUpdate interface [.NET Framework debugging]
ms.assetid: 63a9ef45-01a6-46da-b958-5c6dc2dc232c
topic_type:
- apiref
ms.openlocfilehash: f3305a7bb003fc50f772f1100f8a17d385e4d5fc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449002"
---
# <a name="isymunmanagedencupdate-interface"></a>ISymUnmanagedENCUpdate – rozhraní
Poskytuje funkce pro funkci upravit a pokračovat.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetLocalVariableCount – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariablecount-method.md)|Získá počet místních proměnných.|  
|[GetLocalVariables – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariables-method.md)|Získá místní proměnné.|  
|[InitializeForEnc – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-initializeforenc-method.md)|Umožňuje vypočítat hranice metod před prvním voláním metody [ISymUnmanagedENCUpdate:: updatesymbolstore2 –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) .|  
|[UpdateMethodLines – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatemethodlines-method.md)|Umožňuje aktualizovat informace o řádku pro metodu, která není znovu zkompilována, ale jejíž řádky byly přesunuty nezávisle. Rozdíl pro každý příkaz je povolen.|  
|[UpdateSymbolStore2 – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md)|Umožňuje kompilátoru vynechat funkce, které se nezměnily z datového proudu PDB (program Database) za předpokladu, že informace o řádku splňují požadavky. Správné informace o řádku lze určit pomocí původní informace na řádku PDB a jedna Delta pro všechny řádky ve funkci.|  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
