---
title: ISymUnmanagedScope2 – rozhraní
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2
helpviewer_keywords:
- ISymUnmanagedScope2 interface [.NET Framework debugging]
ms.assetid: 2ed6a387-ba45-483e-9a1e-b0c69f67998b
topic_type:
- apiref
ms.openlocfilehash: 886ba693183a6b99eb03635e95a9661d105de40e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610857"
---
# <a name="isymunmanagedscope2-interface"></a>ISymUnmanagedScope2 – rozhraní
Představuje lexikální obor v rámci metody. Toto rozhraní rozšiřuje rozhraní [ISymUnmanagedScope](isymunmanagedscope-interface.md) o metody, které získávají informace o konstantách definovaných v rámci oboru.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetConstantCount – metoda](isymunmanagedscope2-getconstantcount-method.md)|Získá počet konstant definovaných v rámci tohoto oboru.|  
|[GetConstants – metoda](isymunmanagedscope2-getconstants-method.md)|Získá místní konstanty definované v rámci tohoto oboru.|  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také

- [Rozhraní úložiště symbolů diagnostiky](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedScope – rozhraní](isymunmanagedscope-interface.md)
