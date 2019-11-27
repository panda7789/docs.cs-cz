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
ms.openlocfilehash: 393984241412f543b6ac082484cf5e23edb2d9f4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448978"
---
# <a name="isymunmanagedencupdateupdatesymbolstore2-method"></a>ISymUnmanagedENCUpdate::UpdateSymbolStore2 – metoda
Umožňuje kompilátoru vynechat funkce, které se nezměnily z datového proudu PDB (program Database), za předpokladu, že informace o řádku splňují požadavky. Správné informace o řádku lze určit pomocí původní informace na řádku PDB a jedna Delta pro všechny řádky ve funkci.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT UpdateSymbolStore2(  
    [in]  IStream      *pIStream,  
    [in]  SYMLINEDELTA* pDeltaLines,  
    [in]  ULONG         cDeltaLines);  
```  
  
## <a name="parameters"></a>Parametry  
 `pIStream`  
 pro Ukazatel na [IStream](/windows/desktop/api/objidl/nn-objidl-istream) , který obsahuje informace o řádku.  
  
 `pDeltaLines`  
 pro Ukazatel na strukturu [symlinedelta –](../../../../docs/framework/unmanaged-api/diagnostics/symlinedelta-structure.md) , která obsahuje řádky, které se změnily.  
  
 `cDeltaLines`  
 pro `ULONG`, která představuje počet řádků, které byly změněny.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedENCUpdate – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
