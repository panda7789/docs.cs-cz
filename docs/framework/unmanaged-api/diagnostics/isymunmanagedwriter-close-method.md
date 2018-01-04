---
title: "ISymUnmanagedWriter::Close – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.Close
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::Close
helpviewer_keywords:
- Close method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::Close method [.NET Framework debugging]
ms.assetid: 4cce59e1-80b9-4fc4-b3aa-126f1c5876bc
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 70f710802862c3237cbd67693f8366946926891e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterclose-method"></a>ISymUnmanagedWriter::Close – metoda
Zavře zapisovače symbol po potvrzení symboly pro úložiště symbolů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Close();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Po toto volání zapisovače symbol stává neplatným pro další aktualizace. Zavřete modul pro zápis symbol bez potvrzení symboly, použijte [isymunmanagedwriter::Abort –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md) metoda místo.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také  
 [ISymUnmanagedWriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
