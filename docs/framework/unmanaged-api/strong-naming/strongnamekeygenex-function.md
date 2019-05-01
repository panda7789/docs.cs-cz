---
title: StrongNameKeyGenEx – funkce
ms.date: 03/30/2017
api_name:
- StrongNameKeyGenEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyGenEx
helpviewer_keywords:
- StrongNameKeyGenEx function [.NET Framework strong naming]
ms.assetid: 36bd10b9-9857-45f3-8d3b-0da091d6169e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: af75a645b11325b96740807f9a3df65f5a676026
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000243"
---
# <a name="strongnamekeygenex-function"></a>StrongNameKeyGenEx – funkce
Generuje nový pár veřejného a privátního klíče se zadanou velikost klíče pro použití silným názvem.  
  
 Tato funkce je zastaralá. Použití [iclrstrongname::strongnamekeygenex –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md) metoda místo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
BOOLEAN StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wszKeyContainer`  
 [in] Název požadovaný kontejner klíče. `wszKeyContainer` musí být neprázdný řetězec, nebo null, pokud chcete generovat dočasný název.  
  
 `dwFlags`  
 [in] Určuje, zda má zůstat zkratku zaregistrovanou. Podporovány jsou následující hodnoty:  
  
- 0x00000000 - nepoužívá, pokud `wszKeyContainer` má hodnotu null. k vygenerování názvu dočasného kontejneru klíčů.  
  
- 0x00000001 (`SN_LEAVE_KEY`)-určuje, že klíč by měl být vlevo zaregistrován.  
  
 `dwKeySize`  
 [in] Požadovaná velikost klíče v bitech.  
  
 `ppbKeyBlob`  
 [out] Vrácený pár veřejného a privátního klíče.  
  
 `pcbKeyBlob`  
 [out] Velikost v bajtech, z `ppbKeyBlob`.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true` Při úspěšném dokončení; v opačném případě `false`.  
  
## <a name="remarks"></a>Poznámky  
 Vyžadují rozhraní .NET Framework verze 1.0 a 1.1 `dwKeySize` z 1 024 bity k podepisování sestavení silným názvem; přidá verze 2.0 podporuje pro klíče 2048 bitů.  
  
 Po načtení klíče, měli byste zavolat [strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkce přidělená paměť uvolnit.  
  
 Pokud `StrongNameKeyGenEx` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce k načtení poslední chyby generované.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** StrongName.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [StrongNameKeyGenEx – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)
- [StrongNameKeyGen – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)
- [ICLRStrongName – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
