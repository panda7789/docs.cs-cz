---
title: ISymUnmanagedENCUpdate::UpdateSymbolStore2 – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5a4bcc4e6994f06fabf69e5548ad6922343b7dd5
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479789"
---
# <a name="isymunmanagedencupdateupdatesymbolstore2-method"></a>ISymUnmanagedENCUpdate::UpdateSymbolStore2 – metoda
Umožňuje kompilátoru chcete vynechat, nechte funkce, které nebyly upraveny z datového proudu databáze (PDB) programu, pokud informace o řádku splňuje požadavky. Informace o správné řádku se dá určit pomocí staré informace o řádku PDB a jeden rozdílové hodnoty všech řádků ve funkci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT UpdateSymbolStore2(  
    [in]  IStream      *pIStream,  
    [in]  SYMLINEDELTA* pDeltaLines,  
    [in]  ULONG         cDeltaLines);  
```  
  
## <a name="parameters"></a>Parametry  
 `pIStream`  
 [in] Ukazatel [IStream](/windows/desktop/api/objidl/nn-objidl-istream) , který obsahuje informace o řádku.  
  
 `pDeltaLines`  
 [in] Ukazatel [symlinedelta –](../../../../docs/framework/unmanaged-api/diagnostics/symlinedelta-structure.md) struktura obsahující řádky, které se změnily.  
  
 `cDeltaLines`  
 [in] A `ULONG` , který představuje počet řádků, které se změnily.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:
- [ISymUnmanagedENCUpdate – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
