---
title: ISymUnmanagedDocument::GetCheckSum – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetCheckSum
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocument::GetCheckSum method [.NET Framework debugging]
- GetCheckSum method [.NET Framework debugging]
ms.assetid: 9bc881b3-e2ce-48a7-ad69-17eaaa304120
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b34f985f199542612bcdb9b30ebae28649438e1b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776766"
---
# <a name="isymunmanageddocumentgetchecksum-method"></a>ISymUnmanagedDocument::GetCheckSum – metoda
Získá kontrolní součet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCheckSum(  
    [in]  ULONG32  cData,  
    [out] ULONG32  *pcData,  
    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `cData`  
 [in] Délka vyrovnávací paměti poskytované `data` parametr  
  
 `pcData`  
 [out] Velikost a délce kontrolní součet v bajtech.  
  
 `data`  
 [out] Vyrovnávací paměť, která přijímá kontrolního součtu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud metoda uspěje; S_OK v opačném případě chybový kód.  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedDocument – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
