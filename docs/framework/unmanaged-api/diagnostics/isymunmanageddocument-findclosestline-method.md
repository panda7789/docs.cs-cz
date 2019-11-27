---
title: ISymUnmanagedDocument::FindClosestLine – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.FindClosestLine
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::FindClosestLine
helpviewer_keywords:
- FindClosestLine method [.NET Framework debugging]
- ISymUnmanagedDocument::FindClosestLine method [.NET Framework debugging]
ms.assetid: 628f2a04-e529-407d-841e-3b3da219a9cb
topic_type:
- apiref
ms.openlocfilehash: 0e95255479792c7056bee7ee4f6c507e0f41eb6a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449212"
---
# <a name="isymunmanageddocumentfindclosestline-method"></a>ISymUnmanagedDocument::FindClosestLine – metoda
Vrátí nejbližší řádek, který je sekvenčním bodem, na základě řádku v tomto dokumentu, který může nebo nemusí být bodem sekvence.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT FindClosestLine(  
    [in]  ULONG32  line,  
    [out, retval] ULONG32*  pRetVal);  
```  
  
## <a name="parameters"></a>Parametry  
 `line`  
 pro Řádek v tomto dokumentu.  
  
 `pRetVal`  
 mimo Ukazatel na proměnnou, která přijímá řádek.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě kód chyby.  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedDocument – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
