---
title: ICeeGen::GetSectionBlock – metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionBlock
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionBlock
helpviewer_keywords:
- GetSectionBlock method [.NET Framework metadata]
- ICeeGen::GetSectionBlock method [.NET Framework metadata]
ms.assetid: 05c78aaf-5bbd-497e-9ae2-55f4fae0c5fb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 84ccbd7a8be7d90a541fb2d54baa3d7f66d3d31e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746113"
---
# <a name="iceegengetsectionblock-method"></a>ICeeGen::GetSectionBlock – metoda
Získá blok části základu kódu.  
  
 Tato metoda je zastaralý a neměl by se používat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,     
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);   
```  
  
## <a name="parameters"></a>Parametry  
 `section`  
 [in] Části, ze kterého se má načíst blok základu kódu.  
  
 `len`  
 [in] Délka bloku, který se má načíst.  
  
 `align`  
 [in] Byte, vzhledem k začátku části, pomocí kterého se má zarovnání prvního bajtu bloku. Toto je umístění bloku v rámci oddílu.  
  
 `ppBytes`  
 [out] Ukazatel na umístění, která bude přijímat adresy načtený bloku.  
  
## <a name="remarks"></a>Poznámky  
 Volání `GetSectionBlock` pouze v případě, že máte zvláštní oddíl s požadavky, které nejsou zpracovány jinými metodami.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICeeGen – rozhraní](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
