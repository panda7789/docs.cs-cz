---
title: ISymUnmanagedVariable – rozhraní
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable
helpviewer_keywords:
- ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: 704c69ba-77bc-40d7-8c0c-400061686321
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 712eca7f3f9fec9c81e638802f5a664ec6469d53
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797475"
---
# <a name="isymunmanagedvariable-interface"></a>ISymUnmanagedVariable – rozhraní
Představuje proměnnou, jako je například parametr, místní proměnné nebo pole.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetAddressField1 – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)|Získá první pole adresy pro tuto proměnnou. Její význam závisí na druhu adresu.|  
|[GetAddressField2 – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)|Získá druhý pole adresy pro tuto proměnnou. Její význam závisí na druhu adresu.|  
|[GetAddressField3 – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)|Získá pole třetí adresa pro tuto proměnnou. Její význam závisí na druhu adresu.|  
|[GetAddressKind – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)|Získá druh adresu této proměnné.|  
|[GetAttributes – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getattributes-method.md)|Získá příznaky atributu pro tuto proměnnou.|  
|[GetEndOffset – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)|Získá posun ukončení této proměnné v rámci svého nadřazeného objektu.|  
|[GetName – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getname-method.md)|Získá název této proměnné.|  
|[GetSignature – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getsignature-method.md)|Získá podpis této proměnné.|  
|[GetStartOffset – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)|Získá počáteční odsazení této proměnné v rámci svého nadřazeného objektu.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
