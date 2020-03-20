---
title: Silné názvy (referenční dokumentace nespravovaného rozhraní API)
ms.date: 03/30/2017
helpviewer_keywords:
- strong naming [.NET Framework], using the unmanaged API
- native API reference [.NET Framework], strong naming
- unmanaged API reference [.NET Framework], strong naming
ms.assetid: 428c68b6-a7b4-44be-b280-75905f46612c
ms.openlocfilehash: 7d18513450111d58b5d26fd834addd465cfc4267
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140633"
---
# <a name="strong-naming-unmanaged-api-reference"></a>Silné názvy (referenční dokumentace nespravovaného rozhraní API)
Silné rozhraní API pro pojmenování umožňuje klientovi spravovat podepisování silných názvů pro sestavení.  
  
 Podepisování sestavení se silným názvem přidá šifrování veřejného klíče do souboru obsahujícího manifest sestavení. Podpis silného názvu pomáhá ověřit jedinečnost názvu, zabraňuje falšování názvů a poskytuje volajícím jedinečnou identitu při překladu odkazu. Žádná úroveň důvěryhodnosti však není spojena se silným názvem.  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
> [!NOTE]
> Všechny tyto funkce byly zastaralé počínaje rozhraním .NET Framework 4. Navrhované alternativy naleznete v rozhraní [ICLRStrongName.](../hosting/iclrstrongname-interface.md)  
  
 [GetHashFromAssemblyFile – funkce](gethashfromassemblyfile-function.md)  
 Získá hash zadaného souboru sestavení pomocí zadaného algoritmu hash. Zastaralé počínaje rozhraním .NET Framework 4.  
  
 [GetHashFromAssemblyFileW – funkce](gethashfromassemblyfilew-function.md)  
 Získá hash souboru sestavení zadané jako řetězec Unicode pomocí zadaný algoritmus hash. Zastaralé počínaje rozhraním .NET Framework 4.  
  
 [GetHashFromBlob – funkce](gethashfromblob-function.md)  
 Získá hash sestavení na zadanou adresu paměti pomocí zadaný algoritmus hash. Zastaralé počínaje rozhraním .NET Framework 4.  
  
 [GetHashFromFile – funkce](gethashfromfile-function.md)  
 Generuje hash nad obsahem zadaného souboru.  Zastaralé počínaje rozhraním .NET Framework 4.  
  
 [GetHashFromFileW – funkce](gethashfromfilew-function.md)  
 Generuje hash nad obsahem souboru určeného řetězcem Unicode. Zastaralé počínaje rozhraním .NET Framework 4.  
  
 [GetHashFromHandle – funkce](gethashfromhandle-function.md)  
 Generuje hash nad obsahem souboru se zadaným popisovačem souboru pomocí zadaného algoritmu hash.  Zastaralé počínaje rozhraním .NET Framework 4.  
  
 [StrongNameCompareAssemblies – funkce](strongnamecompareassemblies-function.md)  
 Určuje, zda se dvě sestavení liší pouze podpisy silného názvu. Zastaralé počínaje rozhraním .NET Framework 4.  
  
 [StrongNameErrorInfo – funkce](strongnameerrorinfo-function.md)  
 Získá poslední kód chyby, která byla vyvolána jedním z funkce silného názvu.  
  
 [StrongNameFreeBuffer – funkce](strongnamefreebuffer-function.md)  
 Uvolní paměť, která byla přidělena s předchozím voláním funkce silného názvu, jako je [například StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md)nebo [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).   Zastaralé počínaje rozhraním .NET Framework 4.  
  
 [StrongNameGetBlob – funkce](strongnamegetblob-function.md)  
 Vyplní zadanou vyrovnávací paměť binární reprezentací spustitelného souboru na zadané adrese. Zastaralé počínaje rozhraním .NET Framework 4.  
  
 [StrongNameGetBlobFromImage – funkce](strongnamegetblobfromimage-function.md)  
 Získá binární reprezentaci obrazu sestavení na zadanou adresu paměti. Zastaralé počínaje rozhraním .NET Framework 4.  
  
 [StrongNameGetPublicKey – funkce](strongnamegetpublickey-function.md)  
 Získá veřejný klíč z dvojice soukromého a veřejného klíče. Zastaralé počínaje rozhraním .NET Framework 4.  
  
 [StrongNameHashSize – funkce](strongnamehashsize-function.md)  
 Získá velikost vyrovnávací paměti požadovanou pro algoritmus hash pomocí zadaného algoritmu hash.  Zastaralé počínaje rozhraním .NET Framework 4.  
  
 [StrongNameKeyDelete – funkce](strongnamekeydelete-function.md)  
 Odstraní zadaný kontejner klíčů. Zastaralé počínaje rozhraním .NET Framework 4.  
  
 [StrongNameKeyGen – funkce](strongnamekeygen-function.md)  
 Vytvoří nový pár veřejného a soukromého klíče pro použití silného názvu.  Zastaralé počínaje rozhraním .NET Framework 4.  
  
 [StrongNameKeyGenEx – funkce](strongnamekeygenex-function.md)  
 Generuje nový pár veřejného a soukromého klíče se zadanou velikostí klíče pro použití silného názvu. Zastaralé počínaje rozhraním .NET Framework 4.  
  
 [StrongNameKeyInstall – funkce](strongnamekeyinstall-function.md)  
 Importuje pár veřejného a soukromého klíče do kontejneru.  Zastaralé počínaje rozhraním .NET Framework 4.  
  
 [StrongNameSignatureGeneration – funkce](strongnamesignaturegeneration-function.md)  
 Generuje podpis silného názvu pro zadané sestavení.   Zastaralé počínaje rozhraním .NET Framework 4.  
  
 [StrongNameSignatureGenerationEx – funkce](strongnamesignaturegenerationex-function.md)  
 Generuje podpis silného názvu pro zadané sestavení na základě zadaných příznaků.    Zastaralé počínaje rozhraním .NET Framework 4.  
  
 [StrongNameSignatureSize – funkce](strongnamesignaturesize-function.md)  
 Vrátí velikost podpisu silného názvu. Zastaralé počínaje rozhraním .NET Framework 4.  
  
 [StrongNameSignatureVerification – funkce](strongnamesignatureverification-function.md)  
 Získá hodnotu označující, zda manifest sestavení na zadané cestě obsahuje podpis silného názvu, který je ověřen podle zadaných příznaků. Zastaralé počínaje rozhraním .NET Framework 4.  
  
 [StrongNameSignatureVerificationEx – funkce](strongnamesignatureverificationex-function.md)  
 Získá hodnotu označující, zda manifest sestavení na zadané cestě obsahuje podpis silného názvu.  Zastaralé počínaje rozhraním .NET Framework 4.  
  
 [StrongNameSignatureVerificationFromImage – funkce](strongnamesignatureverificationfromimage-function.md)  
 Ověří, zda je sestavení, které již bylo namapováno do paměti, platné pro přidružený veřejný klíč. Zastaralé počínaje rozhraním .NET Framework 4.  
  
 [StrongNameTokenFromAssembly – funkce](strongnametokenfromassembly-function.md)  
 Vytvoří token silného názvu ze zadaného souboru sestavení.  Zastaralé počínaje rozhraním .NET Framework 4.  
  
 [StrongNameTokenFromAssemblyEx – funkce](strongnametokenfromassemblyex-function.md)  
 Vytvoří token silného názvu ze zadaného souboru sestavení a vrátí veřejný klíč. Zastaralé počínaje rozhraním .NET Framework 4.  
  
 [StrongNameTokenFromPublicKey – funkce](strongnametokenfrompublickey-function.md)  
 Získá token představující veřejný klíč. Zastaralé počínaje rozhraním .NET Framework 4.  
  
 [PublicKeyBlob – struktura](publickeyblob-structure.md)  
 Představuje veřejný klíč dvojice veřejného a soukromého klíče v binárním formátu.  
  
## <a name="see-also"></a>Viz také

- [ICLRStrongName – rozhraní](../hosting/iclrstrongname-interface.md)
- [Nespravované rozhraní API](../index.md)
