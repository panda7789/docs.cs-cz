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
ms.openlocfilehash: ee57ba14f048032e2cd9d0129089743c0f0304bc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445985"
---
# <a name="isymunmanagedvariable-interface"></a>ISymUnmanagedVariable – rozhraní
Představuje proměnnou, jako je například parametr, místní proměnná nebo pole.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetAddressField1 – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)|Získá první pole adresy pro tuto proměnnou. Jeho význam závisí na typu adresy.|  
|[GetAddressField2 – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)|Získá druhé pole adresy pro tuto proměnnou. Jeho význam závisí na typu adresy.|  
|[GetAddressField3 – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)|Získá třetí pole adresy pro tuto proměnnou. Jeho význam závisí na typu adresy.|  
|[GetAddressKind – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)|Získá typ adresy této proměnné.|  
|[GetAttributes – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getattributes-method.md)|Získá příznaky atributu pro tuto proměnnou.|  
|[GetEndOffset – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)|Získá koncový posun této proměnné v rámci své nadřazené položky.|  
|[GetName – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getname-method.md)|Získá název této proměnné.|  
|[GetSignature – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getsignature-method.md)|Načte podpis této proměnné.|  
|[GetStartOffset – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)|Získá počáteční posun této proměnné v rámci své nadřazené položky.|  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
