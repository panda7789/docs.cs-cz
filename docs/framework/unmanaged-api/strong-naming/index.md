---
title: Silné názvy (referenční dokumentace nespravovaného rozhraní API)
ms.date: 03/30/2017
helpviewer_keywords:
- strong naming [.NET Framework], using the unmanaged API
- native API reference [.NET Framework], strong naming
- unmanaged API reference [.NET Framework], strong naming
ms.assetid: 428c68b6-a7b4-44be-b280-75905f46612c
ms.openlocfilehash: 7d18513450111d58b5d26fd834addd465cfc4267
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140633"
---
# <a name="strong-naming-unmanaged-api-reference"></a>Silné názvy (referenční dokumentace nespravovaného rozhraní API)
Rozhraní API pro silné pojmenování umožňuje klientovi spravovat podepisování silného názvu pro sestavení.  
  
 Podpis sestavení se silným názvem přidá šifrování pomocí veřejného klíče do souboru obsahujícího manifest sestavení. Podepisování silného názvu pomáhá ověřit jedinečnost názvu, zabraňuje falšování názvu a poskytuje volajícím s jedinečnou identitou, když je odkaz vyřešen. Nicméně není k dispozici žádná úroveň důvěryhodnosti se silným názvem.  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
> [!NOTE]
> Všechny tyto funkce jsou zastaralé od .NET Framework 4. Navrhované alternativy najdete v rozhraní [ICLRStrongName](../hosting/iclrstrongname-interface.md) .  
  
 [GetHashFromAssemblyFile – funkce](gethashfromassemblyfile-function.md)  
 Načte hodnotu hash zadaného souboru sestavení pomocí zadaného algoritmu hash. Zastaralé od .NET Framework 4.  
  
 [GetHashFromAssemblyFileW – funkce](gethashfromassemblyfilew-function.md)  
 Načte hodnotu hash souboru sestavení zadaného jako řetězec Unicode pomocí zadaného algoritmu hash. Zastaralé od .NET Framework 4.  
  
 [GetHashFromBlob – funkce](gethashfromblob-function.md)  
 Načte hodnotu hash sestavení v zadané adrese paměti pomocí zadaného algoritmu hash. Zastaralé od .NET Framework 4.  
  
 [GetHashFromFile – funkce](gethashfromfile-function.md)  
 Vygeneruje hodnotu hash přes obsah zadaného souboru.  Zastaralé od .NET Framework 4.  
  
 [GetHashFromFileW – funkce](gethashfromfilew-function.md)  
 Vygeneruje hodnotu hash přes obsah souboru určeného řetězcem Unicode. Zastaralé od .NET Framework 4.  
  
 [GetHashFromHandle – funkce](gethashfromhandle-function.md)  
 Vygeneruje hodnotu hash přes obsah souboru se zadaným popisovačem souboru pomocí zadaného algoritmu hash.  Zastaralé od .NET Framework 4.  
  
 [StrongNameCompareAssemblies – funkce](strongnamecompareassemblies-function.md)  
 Určuje, zda se dvě sestavení liší pouze signaturami silného názvu. Zastaralé od .NET Framework 4.  
  
 [StrongNameErrorInfo – funkce](strongnameerrorinfo-function.md)  
 Získá poslední kód chyby, který byl vyvolán jednou ze všech funkcí se silným názvem.  
  
 [StrongNameFreeBuffer – funkce](strongnamefreebuffer-function.md)  
 Uvolní paměť, která byla přidělena předchozímu volání funkce silného názvu, jako je například [StrongNameGetPublicKey –](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey –](strongnametokenfrompublickey-function.md)nebo [StrongNameSignatureGeneration –](strongnamesignaturegeneration-function.md).   Zastaralé od .NET Framework 4.  
  
 [StrongNameGetBlob – funkce](strongnamegetblob-function.md)  
 Vyplní zadanou vyrovnávací paměť binární reprezentací spustitelného souboru na zadané adrese. Zastaralé od .NET Framework 4.  
  
 [StrongNameGetBlobFromImage – funkce](strongnamegetblobfromimage-function.md)  
 Načte binární reprezentaci image sestavení v zadané adrese paměti. Zastaralé od .NET Framework 4.  
  
 [StrongNameGetPublicKey – funkce](strongnamegetpublickey-function.md)  
 Získá veřejný klíč z páru privátních a veřejných klíčů. Zastaralé od .NET Framework 4.  
  
 [StrongNameHashSize – funkce](strongnamehashsize-function.md)  
 Získá velikost vyrovnávací paměti vyžadované pro hodnotu hash pomocí zadaného algoritmu hash.  Zastaralé od .NET Framework 4.  
  
 [StrongNameKeyDelete – funkce](strongnamekeydelete-function.md)  
 Odstraní zadaný kontejner klíčů. Zastaralé od .NET Framework 4.  
  
 [StrongNameKeyGen – funkce](strongnamekeygen-function.md)  
 Vytvoří nový pár veřejného a privátního klíče pro použití se silným názvem.  Zastaralé od .NET Framework 4.  
  
 [StrongNameKeyGenEx – funkce](strongnamekeygenex-function.md)  
 Vygeneruje nový pár veřejného a privátního klíče se zadanou velikostí klíče pro použití se silným názvem. Zastaralé od .NET Framework 4.  
  
 [StrongNameKeyInstall – funkce](strongnamekeyinstall-function.md)  
 Importuje pár veřejného a privátního klíče do kontejneru.  Zastaralé od .NET Framework 4.  
  
 [StrongNameSignatureGeneration – funkce](strongnamesignaturegeneration-function.md)  
 Vygeneruje podpis silného názvu pro zadané sestavení.   Zastaralé od .NET Framework 4.  
  
 [StrongNameSignatureGenerationEx – funkce](strongnamesignaturegenerationex-function.md)  
 Vygeneruje podpis silného názvu pro zadané sestavení na základě zadaných příznaků.    Zastaralé od .NET Framework 4.  
  
 [StrongNameSignatureSize – funkce](strongnamesignaturesize-function.md)  
 Vrátí velikost podpisu silného názvu. Zastaralé od .NET Framework 4.  
  
 [StrongNameSignatureVerification – funkce](strongnamesignatureverification-function.md)  
 Získá hodnotu, která označuje, zda manifest sestavení v zadané cestě obsahuje podpis silného názvu, který je ověřen podle zadaných příznaků. Zastaralé od .NET Framework 4.  
  
 [StrongNameSignatureVerificationEx – funkce](strongnamesignatureverificationex-function.md)  
 Načte hodnotu, která označuje, zda manifest sestavení v zadané cestě obsahuje podpis silného názvu.  Zastaralé od .NET Framework 4.  
  
 [StrongNameSignatureVerificationFromImage – funkce](strongnamesignatureverificationfromimage-function.md)  
 Ověřuje, že sestavení, které již bylo namapováno do paměti, je platné pro přidružený veřejný klíč. Zastaralé od .NET Framework 4.  
  
 [StrongNameTokenFromAssembly – funkce](strongnametokenfromassembly-function.md)  
 Vytvoří ze zadaného souboru sestavení token se silným názvem.  Zastaralé od .NET Framework 4.  
  
 [StrongNameTokenFromAssemblyEx – funkce](strongnametokenfromassemblyex-function.md)  
 Vytvoří token silného názvu ze zadaného souboru sestavení a vrátí veřejný klíč. Zastaralé od .NET Framework 4.  
  
 [StrongNameTokenFromPublicKey – funkce](strongnametokenfrompublickey-function.md)  
 Získá token představující veřejný klíč. Zastaralé od .NET Framework 4.  
  
 [PublicKeyBlob – struktura](publickeyblob-structure.md)  
 Představuje veřejný klíč páru veřejného a privátního klíče v binárním formátu.  
  
## <a name="see-also"></a>Viz také:

- [ICLRStrongName – rozhraní](../hosting/iclrstrongname-interface.md)
- [Referenční informace o nespravovaném rozhraní API](../index.md)
