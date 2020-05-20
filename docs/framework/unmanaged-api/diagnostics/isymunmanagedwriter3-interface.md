---
title: ISymUnmanagedWriter3 – rozhraní
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3
helpviewer_keywords:
- ISymUnmanagedWriter3 interface [.NET Framework debugging]
ms.assetid: a034c21e-e371-4360-b470-29e88288948f
topic_type:
- apiref
ms.openlocfilehash: 006045ce101884119f676e4f6324815eb21a10a4
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614653"
---
# <a name="isymunmanagedwriter3-interface"></a>ISymUnmanagedWriter3 – rozhraní
Představuje zapisovač symbolů a poskytuje metody pro definování dokumentů, sekvenčních bodů, lexikálních oborů a proměnných. Toto rozhraní rozšiřuje rozhraní [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) .  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Commit – Metoda](isymunmanagedwriter3-commit-method.md)|Potvrdí změny, které byly doposud napsány do datového proudu.|  
|[OpenMethod2 – metoda](isymunmanagedwriter3-openmethod2-method.md)|Otevře metodu a poskytne její skutečný posun oddílu v obrázku.|  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také

- [Rozhraní úložiště symbolů diagnostiky](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter – rozhraní](isymunmanagedwriter-interface.md)
- [ISymUnmanagedWriter2 – rozhraní](isymunmanagedwriter2-interface.md)
