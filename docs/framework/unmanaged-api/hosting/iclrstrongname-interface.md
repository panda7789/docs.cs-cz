---
title: ICLRStrongName – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRStrongName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName
helpviewer_keywords:
- ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 2fac66fd-6b3b-4dbd-8baf-86038bd85526
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: abe967195694dd61b4af18fb4eebbc3caad2ef4f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771472"
---
# <a name="iclrstrongname-interface"></a>ICLRStrongName – rozhraní
Poskytuje základní globální statické funkce pro podepisování sestavení se silnými názvy. Všechny `ICLRStrongName` metody vrací standardní COM HRESULT.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetHashFromAssemblyFile – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)|Získá hodnotu hash zadaného souboru sestavení, pomocí zadané hashovacího algoritmu.|  
|[GetHashFromAssemblyFileW – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)|Získá hodnotu hash souboru sestavení zadaná jako řetězec znaků Unicode, pomocí zadané hashovacího algoritmu.|  
|[GetHashFromBlob – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md)|Získá hodnotu hash sestavení na adrese zadaná paměťová, pomocí zadané hashovacího algoritmu.|  
|[GetHashFromFile – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)|Vygeneruje hodnotu hash nad obsah zadaného souboru.|  
|[GetHashFromFileW – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)|Vygeneruje hodnotu hash přes obsah souboru určeného řetězce v kódování Unicode.|  
|[GetHashFromHandle – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)|Vygeneruje hodnotu hash přes obsah souboru pomocí zadaného popisovače souboru, pomocí zadané hashovacího algoritmu.|  
|[StrongNameCompareAssemblies – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md)|Určuje, zda se dvě sestavení liší pouze v jejich podpisy se silným názvem.|  
|[StrongNameFreeBuffer – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)|Uvolnění paměti, která byla přidělena s předchozí volání metody silným názvem, jako například [strongnamegetpublickey –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md), [strongnametokenfrompublickey –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md), nebo [strongnamesignaturegeneration – ](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md).|  
|[StrongNameGetBlob – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)|Vyplní zadané vyrovnávací paměti binární reprezentace spustitelný soubor na zadané adrese.|  
|[StrongNameGetBlobFromImage – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)|Získá binární vyjádření této bitové kopie sestavení na adrese zadaná paměťová.|  
|[StrongNameGetPublicKey – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)|Získá veřejný klíč z páru klíčů privátní nebo veřejné.|  
|[StrongNameHashSize – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md)|Získá velikost vyrovnávací paměti vyžadované pro hodnotu hash pomocí algoritmu zadanou hodnotu hash.|  
|[StrongNameKeyDelete – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)|Odstraní zadaný kontejner klíče.|  
|[StrongNameKeyGen – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)|Vytvoří nový pár veřejného a privátního klíče pro použití silným názvem.|  
|[StrongNameKeyGenEx – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)|Generuje nový pár veřejného a privátního klíče se zadanou velikostí klíče pro použití silným názvem.|  
|[StrongNameKeyInstall – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)|Importuje pár veřejného a privátního klíče do kontejneru.|  
|[StrongNameSignatureGeneration – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)|Podpis silného názvu generuje pro zadané sestavení.|  
|[StrongNameSignatureGenerationEx – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)|Podpis silného názvu generuje pro zadané sestavení podle zadané příznaky.|  
|[StrongNameSignatureSize – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md)|Vrátí velikost položky podpis silného názvu.|  
|[StrongNameSignatureVerification – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)|Získá hodnotu označující, zda obsahuje manifest sestavení v zadané cestě podpis silného názvu, který je ověřen podle zadané příznaky.|  
|[StrongNameSignatureVerificationEx – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)|Získá hodnotu označující, zda obsahuje manifest sestavení v zadané cestě podpis silného názvu.|  
|[StrongNameSignatureVerificationFromImage – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)|Ověřuje, že je platný pro přidružené veřejný klíč sestavení, které je již namapováno na paměť.|  
|[StrongNameTokenFromAssembly – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)|Vytvoří token silného názvu ze zadaného souboru sestavení.|  
|[StrongNameTokenFromAssemblyEx – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)|Vytvoří token silného názvu ze zadaného souboru sestavení a vrátí veřejný klíč.|  
|[StrongNameTokenFromPublicKey – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)|Získá token představující veřejný klíč.|  
  
## <a name="remarks"></a>Poznámky  
 Můžete získat instanci `ICLRStrongName` voláním [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) pomocí metody `CLSID_CLRStrongName` a `IID_ICLRStrongName` jako parametry.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
