---
title: ISymUnmanagedDocument::GetCheckSumAlgorithmId – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetCheckSumAlgorithmId
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetCheckSumAlgorithmId
helpviewer_keywords:
- ISymUnmanagedDocument::GetCheckSumAlgorithmId method [.NET Framework debugging]
- GetCheckSumAlgorithmId method [.NET Framework debugging]
ms.assetid: c7f941cd-e25b-4b85-b1ce-5f77c9208fa9
topic_type:
- apiref
ms.openlocfilehash: 2bc673d2e331cd32d5317cb20f9418eb3a3b144a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431065"
---
# <a name="isymunmanageddocumentgetchecksumalgorithmid-method"></a>ISymUnmanagedDocument::GetCheckSumAlgorithmId – metoda
Získá identifikátor algoritmu kontrolního součtu nebo vrátí identifikátor GUID všech nul, pokud neexistuje kontrolní součet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCheckSumAlgorithmId(  
    [out, retval] GUID*  pRetVal);  
```  
  
## <a name="parameters"></a>Parametry  
 `pRetVal`  
 mimo Ukazatel na proměnnou, která přijímá identifikátor algoritmu kontrolního součtu.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, zda je metoda úspěšná.  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedDocument – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
