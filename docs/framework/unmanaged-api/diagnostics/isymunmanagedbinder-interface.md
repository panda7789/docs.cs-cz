---
title: "ISymUnmanagedBinder – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedBinder
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedBinder
helpviewer_keywords: ISymUnmanagedBinder interface [.NET Framework debugging]
ms.assetid: b22fbe19-b30f-4696-8175-e6b91da9edab
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 79d3758f57976d08d4599de500e2e12e4d67cb4b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedbinder-interface"></a>ISymUnmanagedBinder – rozhraní
Představuje vazač symbol pro nespravovaného kódu.  
  
> [!IMPORTANT]
>  Je bezpečnostní riziko pro otevření souboru databáze (PDB) program z nedůvěryhodného zdroje.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetReaderForFile – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)|Vrátí zadaný metadat rozhraní a název souboru správný [ISymUnmanagedReader](isymunmanagedreader-interface.md) struktura, která budou číst související s modulem symboly pro ladění.|  
|[GetReaderFromStream – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderfromstream-method.md)|Zadaný datový proud, který obsahuje úložiště symbolů a metadat rozhraní, vrátí správné [ISymUnmanagedReader](isymunmanagedreader-interface.md) struktura, která budou číst ladění symboly z obchodu daný symbol.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [ISymUnmanagedBinder2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 [ISymUnmanagedBinder3 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
