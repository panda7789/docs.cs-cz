---
title: ISymUnmanagedBinder2 – rozhraní
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder2 Interface
helpviewer_keywords:
- ISymUnmanagedBinder2 interface [.NET Framework debugging]
ms.assetid: 7a59f405-73e8-4434-8bcc-a9dc45ea08e6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 29501eeb6085dbc235112d98e8099fcfa4565000
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedbinder2-interface"></a>ISymUnmanagedBinder2 – rozhraní
Představuje vazač symbol pro nespravovaného kódu a rozšiřuje [isymunmanagedbinder –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md) rozhraní.  
  
> [!IMPORTANT]
>  Je bezpečnostní riziko pro otevření souboru databáze (PDB) program z nedůvěryhodného zdroje.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetReaderForFile2 – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)|Vrátí zadaný metadat rozhraní a název souboru správný <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> rozhraní, které budou číst související s modulem symboly pro ladění. Poskytuje rozšířené hledání než [isymunmanagedbinder::getreaderforfile –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) metoda.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [ISymUnmanagedBinder – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 [ISymUnmanagedBinder3 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
