---
title: "ISymUnmanagedENCUpdate::UpdateSymbolStore2 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedENCUpdate.UpdateSymbolStore2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::UpdateSymbolStore2
helpviewer_keywords:
- ISymUnmanagedENCUpdate::UpdateSymbolStore2 method [.NET Framework debugging]
- UpdateSymbolStore2 method [.NET Framework debugging]
ms.assetid: 35588317-6184-485c-ab41-4b15fc1765d9
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a366047530f3433ab1bfbb5f30d4b9b54c5bdb08
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedencupdateupdatesymbolstore2-method"></a>ISymUnmanagedENCUpdate::UpdateSymbolStore2 – metoda
Umožňuje kompilátoru vynechat funkce, které nebyly upraveny z datového proudu program databáze (PDB), zadaný informace řádku splňuje požadavky. Informace o správné řádku se dá určit pomocí staré informace řádku PDB a jeden rozdílové u všech spojnic ve funkci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT UpdateSymbolStore2(  
    [in]  IStream      *pIStream,  
    [in]  SYMLINEDELTA* pDeltaLines,  
    [in]  ULONG         cDeltaLines);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pIStream`  
 [v] Ukazatel na <xref:IStream> obsahující informace o řádku.  
  
 `pDeltaLines`  
 [v] Ukazatel [symlinedelta –](../../../../docs/framework/unmanaged-api/diagnostics/symlinedelta-structure.md) struktura obsahující řádky, které se změnily.  
  
 `cDeltaLines`  
 [v] A `ULONG` představující počet řádků, které se změnily.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také  
 [ISymUnmanagedENCUpdate – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
