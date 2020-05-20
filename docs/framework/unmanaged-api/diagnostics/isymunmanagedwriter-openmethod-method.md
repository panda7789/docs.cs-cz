---
title: ISymUnmanagedWriter::OpenMethod – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenMethod
helpviewer_keywords:
- ISymUnmanagedWriter::OpenMethod method [.NET Framework debugging]
- OpenMethod method [.NET Framework debugging]
ms.assetid: fb90cb7f-af88-45e8-a99f-80a0bbddb08b
topic_type:
- apiref
ms.openlocfilehash: d2d16ab0a29fadd3a64d906a64fc46c422e01c45
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610038"
---
# <a name="isymunmanagedwriteropenmethod-method"></a>ISymUnmanagedWriter::OpenMethod – metoda
Otevře metodu, do které jsou vygenerovány informace o symbolech. Daná metoda se označuje jako aktuální metoda pro volání pro definování bodů sekvence, parametrů a lexikálních oborů. Existuje implicitní lexikální obor kolem celé metody. Opětovné otevření metody, která byla dříve zavřena, vymaže všechny dříve definované symboly pro danou metodu. V jednu chvíli může existovat jenom jedna metoda Open.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT OpenMethod(  
    [in] mdMethodDef method);  
```  
  
## <a name="parameters"></a>Parametry  
 `method`  
 pro Token metadat pro metodu, která se má otevřít  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také

- [ISymUnmanagedWriter – rozhraní](isymunmanagedwriter-interface.md)
- [CloseMethod – metoda](isymunmanagedwriter-closemethod-method.md)
- [OpenMethod2 – metoda](isymunmanagedwriter3-openmethod2-method.md)
