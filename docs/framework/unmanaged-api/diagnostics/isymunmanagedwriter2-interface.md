---
title: ISymUnmanagedWriter2 – rozhraní
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2
helpviewer_keywords:
- ISymUnmanagedWriter2 interface [.NET Framework debugging]
ms.assetid: 8e78faa4-cf43-44fb-a91d-94d6df692a25
topic_type:
- apiref
ms.openlocfilehash: 1fe6055d930c6d30e947d6bc774d0520a9e175ae
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614679"
---
# <a name="isymunmanagedwriter2-interface"></a>ISymUnmanagedWriter2 – rozhraní
Představuje zapisovač symbolů a poskytuje metody pro definování dokumentů, sekvenčních bodů, lexikálních oborů a proměnných. Toto rozhraní rozšiřuje rozhraní [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) .  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[DefineConstant2 – metoda](isymunmanagedwriter2-defineconstant2-method.md)|Definuje název pro konstantní hodnotu.|  
|[DefineGlobalVariable2 – metoda](isymunmanagedwriter2-defineglobalvariable2-method.md)|Definuje jednu globální proměnnou.|  
|[DefineLocalVariable2 – metoda](isymunmanagedwriter2-definelocalvariable2-method.md)|Definuje jednu proměnnou v aktuálním lexikálním oboru.|  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také

- [Rozhraní úložiště symbolů diagnostiky](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter – rozhraní](isymunmanagedwriter-interface.md)
- [ISymUnmanagedWriter3 – rozhraní](isymunmanagedwriter3-interface.md)
