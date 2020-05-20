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
ms.openlocfilehash: d05d4451e8fb75829b22e0a1b9c9afcb0607eb8b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610168"
---
# <a name="isymunmanagedvariable-interface"></a>ISymUnmanagedVariable – rozhraní
Představuje proměnnou, jako je například parametr, místní proměnná nebo pole.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetAddressField1 – metoda](isymunmanagedvariable-getaddressfield1-method.md)|Získá první pole adresy pro tuto proměnnou. Jeho význam závisí na typu adresy.|  
|[GetAddressField2 – metoda](isymunmanagedvariable-getaddressfield2-method.md)|Získá druhé pole adresy pro tuto proměnnou. Jeho význam závisí na typu adresy.|  
|[GetAddressField3 – metoda](isymunmanagedvariable-getaddressfield3-method.md)|Získá třetí pole adresy pro tuto proměnnou. Jeho význam závisí na typu adresy.|  
|[GetAddressKind – metoda](isymunmanagedvariable-getaddresskind-method.md)|Získá typ adresy této proměnné.|  
|[GetAttributes – metoda](isymunmanagedvariable-getattributes-method.md)|Získá příznaky atributu pro tuto proměnnou.|  
|[GetEndOffset – metoda](isymunmanagedvariable-getendoffset-method.md)|Získá koncový posun této proměnné v rámci své nadřazené položky.|  
|[GetName – metoda](isymunmanagedvariable-getname-method.md)|Získá název této proměnné.|  
|[GetSignature – metoda](isymunmanagedvariable-getsignature-method.md)|Načte podpis této proměnné.|  
|[GetStartOffset – metoda](isymunmanagedvariable-getstartoffset-method.md)|Získá počáteční posun této proměnné v rámci své nadřazené položky.|  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také

- [Rozhraní úložiště symbolů diagnostiky](diagnostics-symbol-store-interfaces.md)
