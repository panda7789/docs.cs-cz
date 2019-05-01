---
title: ICeeGen::EmitString – metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.EmitString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::EmitString
helpviewer_keywords:
- EmitString method [.NET Framework metadata]
- ICeeGen::EmitString method [.NET Framework metadata]
ms.assetid: ad2710a7-edb8-4493-8619-3fce235e3334
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1eabf5631fcfe7a187d0e203d64c7a7f4f5a819a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62045034"
---
# <a name="iceegenemitstring-method"></a>ICeeGen::EmitString – metoda
Zadaný řetězec vysílá do základu kódu.  
  
 Tato metoda je zastaralý a neměl by se používat.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EmitString (  
    [in]  LPWSTR    lpString,  
    [out] ULONG     *RVA  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `lpString`  
 [in] Řetězec, který se má vygenerovat.  
  
 `RVA`  
 [out] Relativní virtuální adresu emitovaný řetězce.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICeeGen – rozhraní](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
