---
title: ICLRDataTarget::WriteVirtual – metoda
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.WriteVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::WriteVirtual
helpviewer_keywords:
- ICLRDataTarget::WriteVirtual method [.NET Framework debugging]
- WriteVirtual method [.NET Framework debugging]
ms.assetid: d627e8b7-a605-40ac-b9bb-da9a3f1b66d9
topic_type:
- apiref
ms.openlocfilehash: 6a7a7736837f7e6bbf1ad4982e78a75550abbeab
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860499"
---
# <a name="iclrdatatargetwritevirtual-method"></a>ICLRDataTarget::WriteVirtual – metoda
Zapisuje data ze zadané vyrovnávací paměti do zadané adresy virtuální paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT WriteVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [in, size_is(bytesRequested)]
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesWritten  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `address`  
 pro CLRDATA_ADDRESS, který ukládá adresu virtuální paměti.  
  
 `buffer`  
 pro Ukazatel na vyrovnávací paměť, ve kterém jsou uložena data, která mají být zapsána.  
  
 `bytesRequested`  
 pro Počet bajtů, které mají být zapsány.  
  
 `bytesWritten`  
 mimo Ukazatel na skutečný počet zapsaných bajtů.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** ClrData. idl, ClrData. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRDataTarget – rozhraní](iclrdatatarget-interface.md)
