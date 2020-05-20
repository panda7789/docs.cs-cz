---
title: ISymUnmanagedBinder3 – rozhraní
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder3 Interface
helpviewer_keywords:
- ISymUnmanagedBinder3 interface [.NET Framework debugging]
ms.assetid: 37527a84-4b03-4f08-8135-94d898599089
topic_type:
- apiref
ms.openlocfilehash: 5a26de2a8f5439b7c81560927c991d449e57b76c
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441588"
---
# <a name="isymunmanagedbinder3-interface"></a>ISymUnmanagedBinder3 – rozhraní
Rozšiřuje rozhraní pořadače symbolů. Získejte toto rozhraní voláním `QueryInterface` objektu, který implementuje `ISymUnmanagedBinder` rozhraní.  
  
> [!IMPORTANT]
> Je bezpečnostním rizikem k otevření souboru programu databáze (PDB) z nedůvěryhodného zdroje.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetReaderFromCallback – metoda](isymunmanagedbinder3-getreaderfromcallback-method.md)|Umožňuje uživateli implementovat nebo dodávkovat prostřednictvím zpětného volání buď `IID_IDiaReadExeAtRVACallback` nebo `IID_IDiaReadExeAtOffsetCallback` , aby získal informace adresáře ladění z paměti.|  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také

- [Rozhraní úložiště symbolů diagnostiky](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedBinder – rozhraní](isymunmanagedbinder-interface.md)
- [ISymUnmanagedBinder2 – rozhraní](isymunmanagedbinder2-interface.md)
