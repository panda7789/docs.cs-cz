---
title: Vylepšené silné názvy
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies
- strong naming [.NET Framework], enhanced
ms.assetid: 6cf17a82-62a1-4f6d-8d5a-d7d06dec2bb5
ms.openlocfilehash: 1d582513b10de88e4e5b9b9ef8c338599d6980f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141171"
---
# <a name="enhanced-strong-naming"></a>Vylepšené silné názvy
Podpis silného názvu je mechanismus identity v rozhraní .NET Framework pro identifikaci sestavení. Jedná se o digitální podpis veřejného klíče, který se obvykle používá k ověření integrity dat předávaných od původce (autora podpisu) příjemci (ověřovateli). Tento podpis se používá jako jedinečná identita pro sestavení a zajišťuje, že odkazy na sestavení nejsou nejednoznačné. Sestavení je podepsáno jako součást procesu sestavení a poté ověřeno při jeho načtení.  
  
 Podpisy silného názvu pomáhají zabránit škodlivým stranám v manipulaci se sestavením a poté znovu podepsat sestavení pomocí klíče původního podepisujícího. Klíče silných názvů však neobsahují žádné spolehlivé informace o vydavateli ani neobsahují hierarchii certifikátů. Podpis silného jména nezaručuje důvěryhodnost osoby, která shromáždění podepsala, ani neoznačuje, zda byla tato osoba legitimním vlastníkem klíče; označuje pouze to, že vlastník klíče podepsal sestavení. Proto nedoporučujeme používat podpis silného názvu jako validátor zabezpečení pro důvěřování kódu jiného výrobce. Microsoft Authenticode je doporučený způsob ověření kódu.  
  
## <a name="limitations-of-conventional-strong-names"></a>Omezení konvenčních silných názvů  
 Technologie silného pojmenování používaná ve verzích před rozhraním .NET Framework 4.5 má následující nedostatky:  
  
- Klíče jsou neustále pod útokem a vylepšené techniky a hardware usnadňují odvodit soukromý klíč z veřejného klíče. Pro ochranu před útoky jsou nezbytné větší klíče. Verze rozhraní .NET Framework před rozhraním .NET Framework 4.5 poskytují možnost podepisovat klíč libovolné velikosti (výchozí velikost je 1024 bitů), ale podepisování sestavení s novým klíčem přeruší všechny binární soubory, které odkazují na starší identitu sestavení. Proto je velmi obtížné upgradovat velikost podpisového klíče, pokud chcete zachovat kompatibilitu.  
  
- Podepisování silných názvů podporuje pouze algoritmus SHA-1. Sha-1 bylo nedávno zjištěno, že je nedostatečná pro bezpečné hašování aplikací. Proto silnější algoritmus (SHA-256 nebo vyšší) je nezbytné. Je možné, že SHA-1 ztratí své postavení kompatibilní s FIPS, což by představovalo problémy pro ty, kteří se rozhodnou používat pouze software a algoritmy kompatibilní s FIPS.  
  
## <a name="advantages-of-enhanced-strong-names"></a>Výhody rozšířených silných názvů  
 Hlavními výhodami rozšířených silných názvů jsou kompatibilita s již existujícími silnými názvy a možnost tvrdit, že jedna identita je rovnocenná jiné:  
  
- Vývojáři, kteří mají již existující podepsaná sestavení, mohou migrovat své identity do algoritmů SHA-2 při zachování kompatibility se sestaveními, která odkazují na staré identity.  
  
- Vývojáři, kteří vytvářejí nová sestavení a nezabývají se již existujícími podpisy silných názvů, mohou používat bezpečnější algoritmy SHA-2 a podepisovat sestavení jako vždy.  
  
## <a name="use-enhanced-strong-names"></a>Použití rozšířených silných názvů  
 Klíče se silným názvem se skládají z klíče podpisu a klíče identity. Sestavení je podepsáno podpisovým klíčem a je identifikováno klíčem identity. Před rozhraním .NET Framework 4.5 byly tyto dva klíče identické. Počínaje rozhraním .NET Framework 4.5 zůstává klíč identity stejný jako v předchozích verzích rozhraní .NET Framework, ale klíč podpisu je vylepšen silnějším algoritmem hash. Kromě toho je podpisový klíč podepsán pomocí klíče identity k vytvoření protipodpisu.  
  
 Atribut <xref:System.Reflection.AssemblySignatureKeyAttribute> umožňuje metadatům sestavení použít již existující veřejný klíč pro identitu sestavení, což umožňuje, aby staré odkazy na sestavení pokračovaly v práci.  Atribut <xref:System.Reflection.AssemblySignatureKeyAttribute> používá protipodpis k zajištění, že vlastník nového klíče podpisu je také vlastníkem starého klíče identity.  
  
### <a name="sign-with-sha-2-without-key-migration"></a>Podepisovat pomocí SHA-2 bez migrace klíčů  
 Spusťte následující příkazy z příkazového řádku a podepište sestavení bez migrace podpisu silného názvu:  
  
1. Vygenerujte nový klíč identity (v případě potřeby).  
  
    ```console  
    sn -k IdentityKey.snk  
    ```  
  
2. Extrahujte veřejný klíč identity a určete, že algoritmus SHA-2 by měl být použit při podepisování pomocí tohoto klíče.  
  
    ```console  
    sn -p IdentityKey.snk IdentityPubKey.snk sha256  
    ```  
  
3. Zpoždění podepsat sestavení se souborem veřejného klíče identity.  
  
    ```console  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
4. Znovu podepište sestavení pomocí dvojice klíčů úplné identity.  
  
    ```console  
    sn -Ra MyAssembly.exe IdentityKey.snk  
    ```  
  
### <a name="sign-with-sha-2-with-key-migration"></a>Podepisování pomocí SHA-2 s migrací klíčů  
 Spusťte následující příkazy z příkazového řádku a podepište sestavení s emigrovaným podpisem silného názvu.  
  
1. Vygenerujte dvojici identity a podpisového klíče (v případě potřeby).  
  
    ```console  
    sn -k IdentityKey.snk  
    sn -k SignatureKey.snk  
    ```  
  
2. Extrahujte veřejný klíč podpisu a určete, že algoritmus SHA-2 by měl být použit při podepisování pomocí tohoto klíče.  
  
    ```console  
    sn -p SignatureKey.snk SignaturePubKey.snk sha256  
    ```  
  
3. Extrahovat veřejný klíč identity, který určuje algoritmus hash, který generuje protipodpis.  
  
    ```console  
    sn -p IdentityKey.snk IdentityPubKey.snk  
    ```  
  
4. Vygenerujte <xref:System.Reflection.AssemblySignatureKeyAttribute> parametry atributu a připojte atribut k sestavení.  
  
    ```console  
    sn -a IdentityPubKey.snk IdentityKey.snk SignaturePubKey.snk  
    ```  

    To vytváří výstup podobný následujícímu.

    ```output
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

    Tento výstup pak lze transformovat do AssemblySignatureKeyAttribute.

    ```
    [assembly:System.Reflection.AssemblySignatureKeyAttribute(
    "002400000c80000094000000060200000024000052534131000400000100010005a3a81ac0a519d96244a9c589fc147c7d403e40ccf184fc290bdd06c7339389a76b738e255a2bce1d56c3e7e936e4fc87d45adc82ca94c716b50a65d39d373eea033919a613e4341c66863cb2dc622bcb541762b43893434d219d1c43f07e9c83fada2aed400b9f6e44ff05e3ecde6c2827830b8f43f7ac8e3270a34d153cdd",
    "e3cf7c211678c4d1a7b8fb20276c894ab74c29f0b5a34de4d61e63d4a997222f78cdcbfe4c91ebe1ddf9f3505a32edcb2a76f34df0450c4f61e376b70fa3cdeb7374b1b8e2078b121e2ee6e8c6a8ed661cc35621b4af53ac29c9e41738f199a81240e8fd478c887d1a30729d34e954a97cddce66e3ae5fec2c682e57b7442738"
    )]
    ```
  
5. Zpoždění podepsat sestavení s veřejným klíčem identity.  
  
    ```console  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
6. Plně podepsat sestavení s dvojicí podpisového klíče.  
  
    ```console  
    sn -Ra MyAssembly.exe SignatureKey.snk  
    ```  
  
## <a name="see-also"></a>Viz také

- [Vytváření a používání sestavení se silným názvem](create-use-strong-named.md)
