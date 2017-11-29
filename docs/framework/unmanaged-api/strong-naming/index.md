---
title: "Silné názvy (referenční dokumentace nespravovaného rozhraní API)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- strong naming [.NET Framework], using the unmanaged API
- native API reference [.NET Framework], strong naming
- unmanaged API reference [.NET Framework], strong naming
ms.assetid: 428c68b6-a7b4-44be-b280-75905f46612c
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 86d741a16a0293892d0d6d90f1763d744ed3675d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="strong-naming-unmanaged-api-reference"></a>Silné názvy (referenční dokumentace nespravovaného rozhraní API)
Silné pojmenování rozhraní API umožňuje klientovi ke správě podepsání sestavení silným názvem.  
  
 Podepisování sestavení se silným názvem přidá veřejný šifrovací klíče do souboru, který obsahuje manifest sestavení. Silné jméno podepisování pomáhá ověřit jedinečnost názvu, zabraňuje falšování a poskytuje volající jedinečnou identitu, kdy odkaz je vyřešený. Žádná úroveň důvěryhodnosti však souvisí se silným názvem.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Silné pojmenování globálních statických funkcí](http://msdn.microsoft.com/en-us/efa715df-e8cc-48f2-9ec4-26586f0dc8d0)  
 Popisuje nespravované globální statické funkce, které používá silné pojmenování rozhraní API.  
  
> [!NOTE]
>  Všechny tyto funkce jsou zastaralé od verze [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. Navrhované alternativy, najdete v článku [iclrstrongname –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) rozhraní.  
  
 [Gethashfromassemblyfile – funkce](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromassemblyfile-function.md)  
 Získá hodnotu hash souboru zadaného sestavení pomocí zadaný algoritmus hash. Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Gethashfromassemblyfilew – funkce](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromassemblyfilew-function.md)  
 Získá hodnotu hash souboru sestavení, který je zadán jako řetězec znaků Unicode, pomocí zadaný algoritmus hash. Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Gethashfromblob – funkce](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromblob-function.md)  
 Získá hodnotu hash sestavení na adrese zadaná paměťová, pomocí zadaný algoritmus hash. Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Gethashfromfile – funkce](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md)  
 Generuje součet hash přes obsah zadaného souboru.  Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Gethashfromfilew – funkce](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md)  
 Generuje součet hash přes obsah soubor určený touto řetězec znaků Unicode. Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Gethashfromhandle – funkce](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromhandle-function.md)  
 Generuje součet hash přes obsah souboru s popisovačem zadaný soubor, použití zadaný algoritmus hash.  Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Strongnamecompareassemblies – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnamecompareassemblies-function.md)  
 Určuje, zda dva sestavení liší pouze jejich podpisy silným názvem. Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Strongnameerrorinfo – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)  
 Získá poslední kód chyby, která byla vygenerována jedna z funkcí silným názvem.  
  
 [Strongnamefreebuffer – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)  
 Uvolní paměť, který byl přidělen s předchozí volání funkce silným názvem, jako [strongnamegetpublickey –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [strongnametokenfrompublickey –](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), nebo [strongnamesignaturegeneration – ](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).   Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Strongnamegetblob – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetblob-function.md)  
 Vyplní zadanou vyrovnávací paměť binární reprezentace spustitelný soubor na zadané adrese. Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Strongnamegetblobfromimage – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetblobfromimage-function.md)  
 Získá binární reprezentace sestavení image na adrese zadaná paměťová. Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Strongnamegetpublickey – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)  
 Získá veřejný klíč z páru soukromého a veřejného klíče. Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Strongnamehashsize – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnamehashsize-function.md)  
 Získá velikost vyrovnávací paměti vyžadované pro hodnotu hash, pomocí zadaný algoritmus hash.  Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Strongnamekeydelete – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeydelete-function.md)  
 Odstraní zadaný kontejner klíčů. Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Strongnamekeygen – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeygen-function.md)  
 Vytvoří nový pár veřejného a privátního klíče pro silné jméno použití.  Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Strongnamekeygenex – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeygenex-function.md)  
 Generuje nový pár veřejného a privátního klíče pomocí zadané velikost klíče pro použití silným názvem. Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Strongnamekeyinstall – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md)  
 Importuje pár veřejného a privátního klíče do kontejneru.  Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Strongnamesignaturegeneration – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)  
 Podpis silného názvu generuje pro zadané sestavení.   Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Strongnamesignaturegenerationex – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegenerationex-function.md)  
 Generuje pro zadané sestavení, podle zadaného příznaky podpis silného názvu.    Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Strongnamesignaturesize – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md)  
 Vrátí velikost podpis silného názvu. Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Strongnamesignatureverification – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverification-function.md)  
 Získá hodnotu označující, zda manifest sestavení v zadaná cesta obsahuje podpis silného názvu, který bude ověřen podle zadaného příznaky. Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Strongnamesignatureverificationex – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverificationex-function.md)  
 Získá hodnotu označující, zda manifest sestavení v zadaná cesta obsahuje podpis silného názvu.  Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Strongnamesignatureverificationfromimage – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverificationfromimage-function.md)  
 Ověřuje, že je sestavení, které už je namapovaný na paměť pro přidružené veřejný klíč platný. Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Strongnametokenfromassembly – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md)  
 Vytvoří token silným názvem ze zadaného souboru sestavení.  Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Strongnametokenfromassemblyex – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassemblyex-function.md)  
 Vytvoří token silným názvem ze zadaného souboru sestavení a vrátí veřejný klíč. Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Strongnametokenfrompublickey – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md)  
 Získá token představující veřejný klíč. Zastaralé od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Struktura silné názvy](http://msdn.microsoft.com/en-us/4b041a2f-fd12-4b91-aacd-bc3b34a5124d)  
 Popisuje strukturu nespravované silné pojmenování API používá ke správě podepsání sestavení silným názvem...  
  
 [PublicKeyBlob – struktura](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 Představuje veřejný klíč pár veřejného a privátního klíče v binárním formátu.  
  
## <a name="see-also"></a>Viz také  
 [Iclrstrongname – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 [Referenční dokumentace nespravovaného rozhraní API](../../../../docs/framework/unmanaged-api/index.md)
