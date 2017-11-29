---
title: "ISymUnmanagedBinder3 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedBinder3
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedBinder3 Interface
helpviewer_keywords: ISymUnmanagedBinder3 interface [.NET Framework debugging]
ms.assetid: 37527a84-4b03-4f08-8135-94d898599089
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: df5cd6d4015fad1baf98909ee9cc923cd9bce05e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedbinder3-interface"></a>ISymUnmanagedBinder3 – rozhraní
Rozšiřuje rozhraní symbol vazač. Získat toto rozhraní vyvoláním `QueryInterface` na objekt, který implementuje `ISymUnmanagedBinder` rozhraní.  
  
> [!IMPORTANT]
>  Je bezpečnostní riziko pro otevření souboru databáze (PDB) program z nedůvěryhodného zdroje.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Getreaderfromcallback – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)|Umožňuje uživateli implementovat nebo zadat buď přes zpětného volání `IID_IDiaReadExeAtRVACallback` nebo `IID_IDiaReadExeAtOffsetCallback` získat informace o directory ladění z paměti|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [Isymunmanagedbinder – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 [Isymunmanagedbinder2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
