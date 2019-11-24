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
Represents a variable, such as a parameter, a local variable, or a field.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetAddressField1 – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)|Gets the first address field for this variable. Its meaning depends on the kind of address.|  
|[GetAddressField2 – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)|Gets the second address field for this variable. Its meaning depends on the kind of address.|  
|[GetAddressField3 – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)|Gets the third address field for this variable. Its meaning depends on the kind of address.|  
|[GetAddressKind – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)|Gets the kind of address of this variable.|  
|[GetAttributes – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getattributes-method.md)|Gets the attribute flags for this variable.|  
|[GetEndOffset – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)|Gets the end offset of this variable within its parent.|  
|[GetName – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getname-method.md)|Gets the name of this variable.|  
|[GetSignature – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getsignature-method.md)|Gets the signature of this variable.|  
|[GetStartOffset – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)|Gets the start offset of this variable within its parent.|  
  
## <a name="requirements"></a>Požadavky  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
