---
title: ICeeGen::GetSectionCreate – metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionCreate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionCreate
helpviewer_keywords:
- ICeeGen::GetSectionCreate method [.NET Framework metadata]
- GetSectionCreate method [.NET Framework metadata]
ms.assetid: 154b2460-59ce-4874-a9f2-1b3353486ac5
topic_type:
- apiref
ms.openlocfilehash: 0cf7b15392c90694db659f6faff6feecbef65466
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008325"
---
# <a name="iceegengetsectioncreate-method"></a>ICeeGen::GetSectionCreate – metoda
Vygeneruje a získá oddíl kódu s použitím zadaných hodnot název a příznak.  
  
 Tato metoda je zastaralá a neměla by se používat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetSectionCreate (  
    [in]  const char     *name,  
    [in]  DWORD          flags,  
    [out] HCEESECTION    *section  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `name`  
 pro Ukazatel na řetězec, který určuje název oddílu, který má být vytvořen.  
  
 `flags`  
 pro Příznaky, které určují možnosti.  
  
 `section`  
 mimo Ukazatel na nově vytvořený oddíl kódu.  
  
## <a name="remarks"></a>Poznámky  
 Volejte `GetSectionCreate` pouze v případě, že máte zvláštní požadavky na oddíly, které nejsou zpracovány jinými metodami.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICeeGen – rozhraní](iceegen-interface.md)
