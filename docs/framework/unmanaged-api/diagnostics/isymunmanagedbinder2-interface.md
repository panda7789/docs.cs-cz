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
ms.openlocfilehash: 8a4fbb40ec2426d000628fbd6d5f0241d3152c18
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441666"
---
# <a name="isymunmanagedbinder2-interface"></a>ISymUnmanagedBinder2 – rozhraní
Představuje pořadač symbolů pro nespravovaný kód a rozšiřuje rozhraní [ISymUnmanagedBinder](isymunmanagedbinder-interface.md) .  
  
> [!IMPORTANT]
> Je bezpečnostním rizikem k otevření souboru programu databáze (PDB) z nedůvěryhodného zdroje.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetReaderForFile2 – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)|Vzhledem k rozhraní metadat a názvu souboru vrátí správné rozhraní [ISymUnmanagedReader](isymunmanagedreader-interface.md) , které přečte symboly ladění spojené s modulem. Poskytuje rozsáhlejší hledání než metoda [ISymUnmanagedBinder:: GetReaderForFile –](isymunmanagedbinder-getreaderforfile-method.md) .|  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také

- [Rozhraní úložiště symbolů diagnostiky](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedBinder – rozhraní](isymunmanagedbinder-interface.md)
- [ISymUnmanagedBinder3 – rozhraní](isymunmanagedbinder3-interface.md)
