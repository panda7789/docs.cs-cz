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
ms.openlocfilehash: a8856790b655f071df704879a247169f456ae2f5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130877"
---
# <a name="strongnamesignaturesize-function"></a>StrongNameSignatureSize – funkce
Vrátí velikost podpisu silného názvu. `StrongNameSignatureSize` obvykle používá kompilátory k určení, kolik místa lze v souboru vyhradit při vytváření sestavení se zpožděným podpisem.  
  
 Tato funkce je zastaralá. Místo toho použijte metodu [ICLRStrongName:: StrongNameSignatureSize –](../hosting/iclrstrongname-strongnamesignaturesize-method.md) .  
  
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
 pro Struktura typu [PublicKeyBlob –](publickeyblob-structure.md) , která obsahuje veřejnou část páru klíčů sloužící k vygenerování podpisu silného názvu.  
  
 `cbPublicKeyBlob`  
 pro Velikost `pbPublicKeyBlob`v bajtech.  
  
 `pcbSize`  
 pro Počet bajtů vyžadovaných k uložení podpisu silného názvu.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true` po úspěšném dokončení; v opačném případě `false`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud se funkce `StrongNameSignatureSize` nedokončila úspěšně, zavolejte funkci [StrongNameErrorInfo –](strongnameerrorinfo-function.md) , která načte poslední vygenerovanou chybu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** StrongName. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [StrongNameSignatureSize – metoda](../hosting/iclrstrongname-strongnamesignaturesize-method.md)
- [ICLRStrongName – rozhraní](../hosting/iclrstrongname-interface.md)
