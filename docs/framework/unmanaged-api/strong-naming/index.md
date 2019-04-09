---
title: Silné názvy (referenční dokumentace nespravovaného rozhraní API)
ms.date: 03/30/2017
helpviewer_keywords:
- strong naming [.NET Framework], using the unmanaged API
- native API reference [.NET Framework], strong naming
- unmanaged API reference [.NET Framework], strong naming
ms.assetid: 428c68b6-a7b4-44be-b280-75905f46612c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 32e74a76b6b1bedee4efc5715d0710c8efce2455
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120754"
---
# <a name="strong-naming-unmanaged-api-reference"></a>Silné názvy (referenční dokumentace nespravovaného rozhraní API)
Rozhraní API pro silné pojmenovávání umožňuje klientovi spravovat podepisování sestavení silným názvem.  
  
 Podepisování sestavení silným názvem přidá veřejný šifrovací klíče do souboru, který obsahuje manifest sestavení. Podepisování se silným názvem pomáhají ověřit jedinečnost názvu brání falšování a poskytne volající jedinečnou identitu při odkaz je vyřešený. Žádná úroveň důvěryhodnosti je však přidružená silným názvem.  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
> [!NOTE]
>  Všechny tyto funkce jsou zastaralé od verze [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. Doporučené alternativy, najdete v článku [iclrstrongname –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) rozhraní.  
  
 [GetHashFromAssemblyFile – funkce](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromassemblyfile-function.md)  
 Získá hodnotu hash zadaného souboru sestavení, pomocí zadané hashovacího algoritmu. Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [GetHashFromAssemblyFileW – funkce](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromassemblyfilew-function.md)  
 Získá hodnotu hash souboru sestavení zadaná jako řetězec znaků Unicode, pomocí zadané hashovacího algoritmu. Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [GetHashFromBlob – funkce](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromblob-function.md)  
 Získá hodnotu hash sestavení na adrese zadaná paměťová, pomocí zadané hashovacího algoritmu. Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [GetHashFromFile – funkce](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md)  
 Vygeneruje hodnotu hash nad obsah zadaného souboru.  Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [GetHashFromFileW – funkce](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md)  
 Vygeneruje hodnotu hash přes obsah souboru určeného řetězce v kódování Unicode. Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [GetHashFromHandle – funkce](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromhandle-function.md)  
 Vygeneruje hodnotu hash přes obsah souboru pomocí zadaného popisovače souboru, pomocí zadané hashovacího algoritmu.  Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameCompareAssemblies – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnamecompareassemblies-function.md)  
 Určuje, zda se dvě sestavení liší pouze v jejich podpisy se silným názvem. Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameErrorInfo – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)  
 Získá poslední kód chyby, která byla vygenerována pomocí jedné z funkcí silného názvu.  
  
 [StrongNameFreeBuffer – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)  
 Uvolnění paměti, která byla přidělena s předchozím volání funkce silným názvem, jako například [strongnamegetpublickey –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [strongnametokenfrompublickey –](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), nebo [strongnamesignaturegeneration – ](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).   Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameGetBlob – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetblob-function.md)  
 Vyplní zadané vyrovnávací paměti binární reprezentace spustitelný soubor na zadané adrese. Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameGetBlobFromImage – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetblobfromimage-function.md)  
 Získá binární vyjádření této bitové kopie sestavení na adrese zadaná paměťová. Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameGetPublicKey – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)  
 Získá veřejný klíč z páru klíčů privátní nebo veřejné. Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameHashSize – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnamehashsize-function.md)  
 Získá velikost vyrovnávací paměti vyžadované pro hodnotu hash pomocí algoritmu zadanou hodnotu hash.  Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameKeyDelete – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeydelete-function.md)  
 Odstraní zadaný kontejner klíče. Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameKeyGen – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeygen-function.md)  
 Vytvoří nový pár veřejného a privátního klíče pro použití silným názvem.  Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameKeyGenEx – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeygenex-function.md)  
 Generuje nový pár veřejného a privátního klíče se zadanou velikostí klíče pro použití silným názvem. Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameKeyInstall – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md)  
 Importuje pár veřejného a privátního klíče do kontejneru.  Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameSignatureGeneration – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)  
 Podpis silného názvu generuje pro zadané sestavení.   Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameSignatureGenerationEx – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegenerationex-function.md)  
 Podpis silného názvu generuje pro zadané sestavení podle zadané příznaky.    Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameSignatureSize – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md)  
 Vrátí velikost položky podpis silného názvu. Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameSignatureVerification – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverification-function.md)  
 Získá hodnotu označující, zda obsahuje manifest sestavení v zadané cestě podpis silného názvu, který je ověřen podle zadané příznaky. Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameSignatureVerificationEx – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverificationex-function.md)  
 Získá hodnotu označující, zda obsahuje manifest sestavení v zadané cestě podpis silného názvu.  Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameSignatureVerificationFromImage – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverificationfromimage-function.md)  
 Ověřuje, že je platný pro přidružené veřejný klíč sestavení, které je již namapováno na paměť. Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameTokenFromAssembly – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md)  
 Vytvoří token silného názvu ze zadaného souboru sestavení.  Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameTokenFromAssemblyEx – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassemblyex-function.md)  
 Vytvoří token silného názvu ze zadaného souboru sestavení a vrátí veřejný klíč. Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameTokenFromPublicKey – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md)  
 Získá token představující veřejný klíč. Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [PublicKeyBlob – struktura](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 Představuje veřejného klíče dvojice veřejného/soukromého klíče v binárním formátu.  
  
## <a name="see-also"></a>Viz také:

- [ICLRStrongName – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
- [Nespravované rozhraní API](../../../../docs/framework/unmanaged-api/index.md)
