---
title: StrongNameSignatureVerificationFromImage – funkce
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerificationFromImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerificationFromImage
helpviewer_keywords:
- StrongnameSignatureVerificationFromImage function [.NET Framework strong naming]
ms.assetid: 9fb144d2-07e0-4a0e-8e05-907bbb6c9e03
topic_type:
- apiref
ms.openlocfilehash: 5c12ca20deee06fcaca68365644fd9dff95379ff
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121163"
---
# <a name="strongnamesignatureverificationfromimage-function"></a>StrongNameSignatureVerificationFromImage – funkce
Ověřuje, že sestavení, které již bylo namapováno do paměti, je platné pro přidružený veřejný klíč.  
  
 Tato funkce je zastaralá. Místo toho použijte metodu [ICLRStrongName:: StrongNameVerificationFromImage](../hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
BOOLEAN StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pbBase`  
 pro Relativní virtuální adresa manifestu namapovaného sestavení.  
  
 `dwLength`  
 pro Velikost mapované image v bajtech  
  
 `dwInFlags`  
 pro Příznaky, které ovlivňují chování ověřování. Podporovány jsou následující hodnoty:  
  
- `SN_INFLAG_FORCE_VER` (0x00000001) – vynutí ověření i v případě, že je nutné přepsat nastavení registru.  
  
- `SN_INFLAG_INSTALL` (0x00000002) – určuje, že se jedná o první ověření provedené na tomto obrázku.  
  
- `SN_INFLAG_ADMIN_ACCESS` (0x00000004) – určuje, že mezipaměť bude umožňovat přístup pouze uživatelům, kteří mají oprávnění správce.  
  
- `SN_INFLAG_USER_ACCESS` (0x00000008) – určuje, zda bude sestavení přístupné pouze pro aktuálního uživatele.  
  
- `SN_INFLAG_ALL_ACCESS` (0x00000010) – určuje, že mezipaměť nebude poskytovat žádné záruky omezení přístupu.  
  
- `SN_INFLAG_RUNTIME` (0x80000000) – vyhrazeno pro interní ladění.  
  
 `pdwOutFlags`  
 mimo Příznak pro další informace o výstupu. Je podporována následující hodnota:  
  
- `SN_OUTFLAG_WAS_VERIFIED` (0x00000001) – Tato hodnota je nastavena na hodnotu `false` a určí, že ověření proběhlo úspěšně z důvodu nastavení registru.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true` po úspěšném dokončení; v opačném případě `false`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud se funkce `StrongNameSignatureVerificationFromImage` nedokončila úspěšně, zavolejte funkci [StrongNameErrorInfo –](strongnameerrorinfo-function.md) , která načte poslední vygenerovanou chybu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** StrongName. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně Mscoree. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [StrongNameSignatureVerificationFromImage – metoda](../hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)
- [ICLRStrongName – rozhraní](../hosting/iclrstrongname-interface.md)
