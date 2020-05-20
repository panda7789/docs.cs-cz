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
ms.openlocfilehash: aa4fe2185ead7edfa47d4194799c930193e04076
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614523"
---
# <a name="isymunmanagedencupdate-interface"></a>ISymUnmanagedENCUpdate – rozhraní
Poskytuje funkce pro funkci upravit a pokračovat.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetLocalVariableCount – metoda](isymunmanagedencupdate-getlocalvariablecount-method.md)|Získá počet místních proměnných.|  
|[GetLocalVariables – metoda](isymunmanagedencupdate-getlocalvariables-method.md)|Získá místní proměnné.|  
|[InitializeForEnc – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-initializeforenc-method.md)|Umožňuje vypočítat hranice metod před prvním voláním metody [ISymUnmanagedENCUpdate:: updatesymbolstore2 –](isymunmanagedencupdate-updatesymbolstore2-method.md) .|  
|[UpdateMethodLines – metoda](isymunmanagedencupdate-updatemethodlines-method.md)|Umožňuje aktualizovat informace o řádku pro metodu, která není znovu zkompilována, ale jejíž řádky byly přesunuty nezávisle. Rozdíl pro každý příkaz je povolen.|  
|[UpdateSymbolStore2 – metoda](isymunmanagedencupdate-updatesymbolstore2-method.md)|Umožňuje kompilátoru vynechat funkce, které se nezměnily z datového proudu PDB (program Database) za předpokladu, že informace o řádku splňují požadavky. Správné informace o řádku lze určit pomocí původní informace na řádku PDB a jedna Delta pro všechny řádky ve funkci.|  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také

- [Rozhraní úložiště symbolů diagnostiky](diagnostics-symbol-store-interfaces.md)
