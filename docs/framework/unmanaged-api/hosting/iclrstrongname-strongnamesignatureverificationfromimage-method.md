---
title: ICLRStrongName::StrongNameSignatureVerificationFromImage – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerificationFromImage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerificationFromImage
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureVerificationFromImage method [.NET Framework hosting]
- StrongNameSignatureVerificationFromImage method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: da91c138-ee30-4fd4-a040-464d97d7e41a
topic_type:
- apiref
ms.openlocfilehash: 1ba7355fae1888436d57562cc21d3865ebc7a4f4
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763173"
---
# <a name="iclrstrongnamestrongnamesignatureverificationfromimage-method"></a>ICLRStrongName::StrongNameSignatureVerificationFromImage – metoda
Ověřuje, že sestavení, které již bylo namapováno do paměti, je platné pro přidružený veřejný klíč.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT StrongNameSignatureVerificationFromImage (  
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
  
- `SN_INFLAG_FORCE_VER`(0x00000001) – vynutí ověření i v případě, že je nutné přepsat nastavení registru.  
  
- `SN_INFLAG_INSTALL`(0x00000002) – určuje, že se jedná o první ověření provedené na tomto obrázku.  
  
- `SN_INFLAG_ADMIN_ACCESS`(0x00000004) – určuje, že mezipaměť povolí přístup pouze uživatelům, kteří mají oprávnění správce.  
  
- `SN_INFLAG_USER_ACCESS`(0x00000008) – určuje, zda bude sestavení přístupné pouze pro aktuálního uživatele.  
  
- `SN_INFLAG_ALL_ACCESS`(0x00000010) – určuje, že mezipaměť nebude poskytovat žádné záruky omezení přístupu.  
  
- `SN_INFLAG_RUNTIME`(0x80000000) – rezervované pro interní ladění.  
  
 `pdwOutFlags`  
 mimo Příznak pro další informace o výstupu. Je podporována následující hodnota:  
  
- `SN_OUTFLAG_WAS_VERIFIED`(0x00000001) – Tato hodnota je nastavena na hodnotu `false` , chcete-li určit, že ověření proběhlo úspěšně z důvodu nastavení registru.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`Pokud byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRStrongName – rozhraní](iclrstrongname-interface.md)
