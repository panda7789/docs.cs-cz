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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e9eef4e1b1c9c82d8576c01dd124ee9ac68c2583
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64610044"
---
# <a name="strongnamesignatureverificationfromimage-function"></a>StrongNameSignatureVerificationFromImage – funkce
Ověřuje, že je platný pro přidružené veřejný klíč sestavení, které je již namapováno na paměť.  
  
 Tato funkce je zastaralá. Použití [ICLRStrongName::StrongNameVerificationFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) metoda místo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
BOOLEAN StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pbBase`  
 [in] Relativní virtuální adresu z namapované sestavení manifestu.  
  
 `dwLength`  
 [in] Velikost v bajtech, z namapované bitové kopie.  
  
 `dwInFlags`  
 [in] Příznaky, které ovlivňují chování ověřování. Podporovány jsou následující hodnoty:  
  
- `SN_INFLAG_FORCE_VER` (0x00000001) – vynutí ověření i v případě, že je potřeba přepsat nastavení registru.  
  
- `SN_INFLAG_INSTALL` (0x00000002) - určuje, že se jedná o první ověřování prováděné na tomto obrázku.  
  
- `SN_INFLAG_ADMIN_ACCESS` (0x00000004) - určuje, že mezipaměť bude umožňovat přístup pouze uživatelům, kteří mají oprávnění správce.  
  
- `SN_INFLAG_USER_ACCESS` (0x00000008) - určuje, zda sestavení přístupné pouze pro aktuálního uživatele.  
  
- `SN_INFLAG_ALL_ACCESS` (0x00000010) - určuje, že mezipaměť bude poskytovat žádné záruky omezení přístupu.  
  
- `SN_INFLAG_RUNTIME` (0x80000000) – vyhrazené pro interní ladění.  
  
 `pdwOutFlags`  
 [out] Příznak pro další výstupní informace. Je podporován následující hodnotu:  
  
- `SN_OUTFLAG_WAS_VERIFIED` (0x00000001) – Tato hodnota nastavená na `false` k určení, že ověření proběhlo úspěšně z důvodu nastavení registru.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true` Při úspěšném dokončení; v opačném případě `false`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud `StrongNameSignatureVerificationFromImage` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce k načtení poslední chyby generované.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** StrongName.h  
  
 **Knihovna:** Zahrnuté jako prostředek v mscoree.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [StrongNameSignatureVerificationFromImage – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)
- [ICLRStrongName – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
