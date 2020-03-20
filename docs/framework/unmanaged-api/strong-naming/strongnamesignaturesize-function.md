---
title: StrongNameSignatureSize – funkce
ms.date: 03/30/2017
api_name:
- StrongNameSignatureSize
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureSize
helpviewer_keywords:
- StrongNameSignatureSize function [.NET Framework strong naming]
ms.assetid: 4fde4cd0-f53e-4411-a2fe-fc5c54472f95
topic_type:
- apiref
ms.openlocfilehash: a19d875b8fb81f2af3821e69452f0f0ed591cd22
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176887"
---
# <a name="strongnamesignaturesize-function"></a>StrongNameSignatureSize – funkce
Vrátí velikost podpisu silného názvu. `StrongNameSignatureSize`obvykle používá kompilátory k určení, kolik místa rezervovat v souboru při vytváření sestavení podepsané zpoždění.  
  
 Tato funkce byla zastaralá. Místo toho použijte metodu [ICLRStrongName::StrongNameSignatureSize.](../hosting/iclrstrongname-strongnamesignaturesize-method.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
BOOLEAN StrongNameSignatureSize (
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,
    [in]  DWORD  *pcbSize  
);
```  
  
## <a name="parameters"></a>Parametry  
 `pbPublicKeyBlob`  
 [v] Struktura typu [PublicKeyBlob,](publickeyblob-structure.md) který obsahuje veřejnou část dvojice klíčů slouží ke generování podpisu silného názvu.  
  
 `cbPublicKeyBlob`  
 [v] Velikost v bajtů `pbPublicKeyBlob`.  
  
 `pcbSize`  
 [v] Počet bajtů potřebných k uložení podpisu silného názvu.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`po úspěšném dokončení; v `false`opačném případě .  
  
## <a name="remarks"></a>Poznámky  
 Pokud `StrongNameSignatureSize` se funkce nedokončí úspěšně, zavolejte funkci [StrongNameErrorInfo,](strongnameerrorinfo-function.md) abyste načetli poslední vygenerovanou chybu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).  
  
 **Záhlaví:** StrongName.h  
  
 **Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [StrongNameSignatureSize – metoda](../hosting/iclrstrongname-strongnamesignaturesize-method.md)
- [ICLRStrongName – rozhraní](../hosting/iclrstrongname-interface.md)
