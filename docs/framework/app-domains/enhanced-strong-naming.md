---
title: Vylepšené silné názvy
ms.date: 03/30/2017
helpviewer_keywords:
- strong-named assemblies
- strong naming [.NET Framework], enhanced
ms.assetid: 6cf17a82-62a1-4f6d-8d5a-d7d06dec2bb5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 659f9ffa8ebb10b34300167e9183f60568279513
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44187164"
---
# <a name="enhanced-strong-naming"></a>Vylepšené silné názvy
Podpis silného názvu je mechanismus identity v rozhraní .NET Framework pro identifikaci sestavení. Je digitální podpis veřejného klíče, který se obvykle používá k ověření integrity dat předávaných od příkazce (podepisující) příjemci (ověřovatel). Tento podpis slouží jako jedinečná identita pro sestavení a zajistí, že odkazy na sestavení nejsou nejednoznačné. Sestavení je podepsáno jako součást procesu sestavení a poté ověřeno, pokud je načten.  
  
 Podpisy se silným názvem pomáhají zabránit zlými úmysly v manipulaci se sestavením a opětovné podepsat sestavení s klíčem původního podepisujícího. Však klíče se silným názvem neobsahují žádné spolehlivé informace o vydavateli, ani neobsahují hierarchii certifikátů. Podpis silného názvu nezaručuje důvěryhodnost osoby, která podepsala sestavení nebo určit, zda tato osoba byla legitimním vlastníkem tohoto klíče; znamená to pouze, že vlastník tohoto klíče sestavení podepsal. Proto nedoporučujeme použití podpisu silného názvu jako validátoru zabezpečení pro důvěřující kód třetí strany. Microsoft Authenticode je doporučeným způsobem, jak ověřit kód.  
  
## <a name="limitations-of-conventional-strong-names"></a>Omezení konvenčních silných názvů.  
 Technologie silného pojmenování používaná ve verzích před [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] má následující nedostatky:  
  
-   Klíče jsou neustále pod útokem a dokonalejší metody a hardware usnadňují odvození soukromého klíče z veřejného klíče. Pro ochranu proti útokům jsou nezbytné větší klíče. Verze rozhraní .NET framework před [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] poskytují možnost přihlásit se pomocí klíče libovolné velikosti (výchozí velikost je 1024 bitů), ale podepsání sestavy s novým klíčem zalomí všechny binární soubory, které odkazují na starší identity sestavení. Proto je velmi obtížné upgradovat velikost podpisového klíče, pokud chcete zachovat kompatibilitu.  
  
-   Podepisování se silným názvem podporuje pouze algoritmus SHA-1. SHA-1 bylo nedávno zjištěno jako nedostatečné pro zatřiďování zabezpečených aplikací. Proto silnější algoritmus (SHA-256 nebo vyšší), je nezbytné. Je možné, že algoritmus SHA-1, dojde ke ztrátě jeho postavení kompatibilní se standardem FIPS, což by problémy pro ty, kteří se rozhodli použít pouze kompatibilní se standardem FIPS software a algoritmy.  
  
## <a name="advantages-of-enhanced-strong-names"></a>Výhody rozšířených silných názvů  
 Hlavní výhody rozšířených silných názvů jsou kompatibilita se stávajícími silnými názvy a schopnost rozhodovat, že se jedna identita odpovídá jiné:  
  
-   Vývojáři, kteří mají existující podepsaná sestavení mohou přenést svoji identitu na algoritmy SHA-2 při zachování kompatibility se sestaveními, která odkazují na staré identity.  
  
-   Vývojáři, kteří vytvářejí nová sestavení a nejsou obeznámeni s již existujícími podpisy silného názvu můžete používat bezpečnější algoritmus SHA-2 a podepsat sestavení, tak jako vždy.  
  
## <a name="using-enhanced-strong-names"></a>Použití vylepšených silných názvů  
 Klíče se silným názvem jsou tvořeny podpisovými klíči a klíč identity. Sestavení je podepsáno pomocí klíče podpisu a je určeno klíčem identity. Před verzí [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], byly tyto dva klíče identické. Počínaje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], zůstává klíč identity stejný jako v předchozích verzích rozhraní .NET Framework, ale podpis klíče jsou rozšířeny silnější hashovací algoritmus. Kromě toho podpisový klíč je podepsán klíčem identity pro tvorbu protipodpisu.  
  
 <xref:System.Reflection.AssemblySignatureKeyAttribute> Atribut umožňuje metadatům sestavení použít již existující veřejný klíč pro identitu sestavení, což umožňuje starším odkazům sestavení pokračovat v práci.  <xref:System.Reflection.AssemblySignatureKeyAttribute> Atribut používá protipodpis zajišťující, že vlastník nového klíče podpisu je také vlastníkem starého klíče identity.  
  
### <a name="signing-with-sha-2-without-key-migration"></a>Přihlášení pomocí SHA-2 bez migrace klíče  
 Spusťte následující příkazy z okna příkazového řádku a podepište tak sestavení bez přenášeného podpisu se silným názvem:  
  
1.  Generovat nový klíč identity (v případě potřeby).  
  
    ```  
    sn -k IdentityKey.snk  
    ```  
  
2.  Extrahujte veřejný klíč identity a určí, že algoritmus SHA-2 má být použit při přihlašování k tomuto klíči.  
  
    ```  
    sn -p IdentityKey.snk IdentityPubKey.snk sha256  
    ```  
  
3.  Vytvoří zpožděný podpis sestavení se souborem identity veřejného klíče.  
  
    ```  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
4.  Znovu podepište sestavení pomocí dvojice klíčů plnou identitou.  
  
    ```  
    sn -Ra MyAssembly.exe IdentityKey.snk  
    ```  
  
### <a name="signing-with-sha-2-with-key-migration"></a>Přihlášení pomocí SHA-2 s migrací klíče  
 Spusťte následující příkazy z okna příkazového řádku a podepište tak sestavení s podpisem migrované silného názvu.  
  
1.  Generování identitu a dvojici podpisových klíčů (v případě potřeby).  
  
    ```  
    sn -k IdentityKey.snk  
    sn -k SignatureKey.snk  
    ```  
  
2.  Extrahujte veřejný podpisový klíč a určí, že algoritmus SHA-2 má být použit při přihlašování k tomuto klíči.  
  
    ```  
    sn -p SignatureKey.snk SignaturePubKey.snk sha256  
    ```  
  
3.  Extrahujte veřejný klíč identity, která určuje algoritmus hash, který generuje podpis čítače.  
  
    ```  
    sn -p IdentityKey.snk IdentityPubKey.snk  
    ```  
  
4.  Parametry pro generování <xref:System.Reflection.AssemblySignatureKeyAttribute> atributu a připojení atributu k sestavení.  
  
    ```  
    sn -a IdentityPubKey.snk IdentityKey.snk SignaturePubKey.snk  
    ```  

    To vytváří výstup podobný následujícímu.

    ```
    Information for key migration attribute.
    (System.Reflection.AssemblySignatureKeyAttribute):
    publicKey=
    002400000c80000094000000060200000024000052534131000400000100010005a3a81ac0a519
    d96244a9c589fc147c7d403e40ccf184fc290bdd06c7339389a76b738e255a2bce1d56c3e7e936
    e4fc87d45adc82ca94c716b50a65d39d373eea033919a613e4341c66863cb2dc622bcb541762b4
    3893434d219d1c43f07e9c83fada2aed400b9f6e44ff05e3ecde6c2827830b8f43f7ac8e3270a3
    4d153cdd

    counterSignature=
    e3cf7c211678c4d1a7b8fb20276c894ab74c29f0b5a34de4d61e63d4a997222f78cdcbfe4c91eb
    e1ddf9f3505a32edcb2a76f34df0450c4f61e376b70fa3cdeb7374b1b8e2078b121e2ee6e8c6a8
    ed661cc35621b4af53ac29c9e41738f199a81240e8fd478c887d1a30729d34e954a97cddce66e3
    ae5fec2c682e57b7442738
    ```

    Tento výstup, pak je možné transformovat do atributu assemblysignaturekeyattribute je uveden.

    ```
    [assembly:System.Reflection.AssemblySignatureKeyAttribute(
    "002400000c80000094000000060200000024000052534131000400000100010005a3a81ac0a519d96244a9c589fc147c7d403e40ccf184fc290bdd06c7339389a76b738e255a2bce1d56c3e7e936e4fc87d45adc82ca94c716b50a65d39d373eea033919a613e4341c66863cb2dc622bcb541762b43893434d219d1c43f07e9c83fada2aed400b9f6e44ff05e3ecde6c2827830b8f43f7ac8e3270a34d153cdd",
    "e3cf7c211678c4d1a7b8fb20276c894ab74c29f0b5a34de4d61e63d4a997222f78cdcbfe4c91ebe1ddf9f3505a32edcb2a76f34df0450c4f61e376b70fa3cdeb7374b1b8e2078b121e2ee6e8c6a8ed661cc35621b4af53ac29c9e41738f199a81240e8fd478c887d1a30729d34e954a97cddce66e3ae5fec2c682e57b7442738"
    )]
    ```
  
5.  Vytvoří zpožděný podpis sestavení s veřejným klíčem identity.  
  
    ```  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
6.  Plně podepište sestavení pomocí dvojice podpisových klíčů.  
  
    ```  
    sn -Ra MyAssembly.exe SignatureKey.snk  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Vytváření a používání sestavení se silným názvem](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
