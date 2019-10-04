---
title: Vylepšené silné názvy
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies
- strong naming [.NET Framework], enhanced
ms.assetid: 6cf17a82-62a1-4f6d-8d5a-d7d06dec2bb5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ab1087a840fe41b9fac7779c73797c470899408
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834884"
---
# <a name="enhanced-strong-naming"></a>Vylepšené silné názvy
Podpis silného názvu je mechanismus identity v .NET Framework pro identifikaci sestavení. Jedná se o digitální podpis veřejného klíče, který se obvykle používá k ověření integrity dat předávaných od původce (Signer) příjemci (Verifier). Tento podpis slouží jako jedinečná identita pro sestavení a zajišťuje, aby odkazy na sestavení nebyly jednoznačné. Sestavení je podepsáno jako součást procesu sestavení a poté ověřeno při jeho načtení.  
  
 Signatury silného názvu zabraňují škodlivým stranám v manipulaci se sestavením a pak znovu podepisovat sestavení pomocí klíče původního podepisujícího. Klíče se silným názvem ale neobsahují žádné spolehlivé informace o vydavateli, ani neobsahují hierarchii certifikátů. Podpis silného názvu nezaručuje věrohodnost osoby, která podepsala sestavení, nebo označuje, zda byla tato osoba legitimním vlastníkem tohoto klíče. indikuje pouze, že vlastník klíče podepsal sestavení. Proto nedoporučujeme používat podpis silného názvu jako validátor zabezpečení pro důvěřování kódu třetí strany. Microsoft Authenticode je doporučeným způsobem, jak kód ověřit.  
  
## <a name="limitations-of-conventional-strong-names"></a>Omezení konvenčních silných názvů  
 Technologie silného pojmenování používaná ve verzích před .NET Framework 4,5 má následující nedostatky:  
  
- Klíče jsou neustále napadené a vylepšené techniky a hardware usnadňují odvození privátního klíče z veřejného klíče. Aby bylo možné chránit před útoky, je nutné mít větší klíče. Verze .NET Framework před .NET Framework 4,5 poskytují možnost podepsat pomocí klíče libovolné velikosti (výchozí velikost je 1024 bitů), ale podepsáním sestavení pomocí nového klíče přerušují všechny binární soubory, které odkazují na starší identitu sestavení. Proto je velmi obtížné upgradovat velikost podpisového klíče, pokud chcete zachovat kompatibilitu.  
  
- Podepisování silného názvu podporuje pouze algoritmus SHA-1. V nedávné době bylo zjištěno, že SHA-1 bude pro zabezpečené aplikace hash nedostatečné. Proto je potřeba silnější algoritmus (SHA-256 nebo vyšší). Je možné, že SHA-1 ztratí své postavení kompatibilní se standardem FIPS, což by znamenalo problémy pro uživatele, kteří se rozhodli používat jenom software a algoritmy kompatibilní se standardem FIPS.  
  
## <a name="advantages-of-enhanced-strong-names"></a>Výhody rozšířených silných názvů  
 Hlavní výhody rozšířených silných názvů jsou kompatibilita se stávajícími silnými názvy a možnostmi deklarace identity, že jedna identita je ekvivalentní jiné:  
  
- Vývojáři, kteří mají již existující podepsaná sestavení, mohou migrovat své identity na algoritmy SHA-2 a přitom zachovat kompatibilitu se sestaveními, která odkazují na staré identity.  
  
- Vývojáři, kteří vytvářejí nová sestavení a nejsou dotčeni pomocí existujících podpisů se silným názvem, mohou používat bezpečnější algoritmy SHA-2 a podepisovat sestavení tak, jak jsou vždy.  
  
## <a name="use-enhanced-strong-names"></a>Použití rozšířených silných názvů  
 Klíče se silným názvem se skládají z klíče podpisu a klíče identity. Sestavení je podepsáno klíčem podpisu a je identifikováno klíčem identity. Před .NET Framework 4,5 byly tyto dva klíče identické. Počínaje verzí .NET Framework 4,5 zůstane klíč identity stejný jako ve starších .NET Framework verzích, ale klíč podpisu se rozšiřuje s silnějším algoritmem hash. Kromě toho je podpisový klíč podepsaný klíčem identity pro vytvoření počítadla signatury.  
  
 Atribut <xref:System.Reflection.AssemblySignatureKeyAttribute> umožňuje metadatům sestavení použít již existující veřejný klíč pro identitu sestavení, což umožňuje, aby staré odkazy na sestavení pokračovaly v práci.  Atribut <xref:System.Reflection.AssemblySignatureKeyAttribute> používá k zajištění toho, že vlastník nového klíče pro podpis je zároveň vlastníkem starého klíče identity.  
  
### <a name="sign-with-sha-2-without-key-migration"></a>Podepsat pomocí SHA-2 bez použití migrace klíče  
 Spusťte následující příkazy z příkazového řádku pro podepsání sestavení bez migrace signatury silného názvu:  
  
1. Vygenerujte nový klíč identity (v případě potřeby).  
  
    ```console  
    sn -k IdentityKey.snk  
    ```  
  
2. Extrahujte veřejný klíč identity a určete, že se při podepisování s tímto klíčem má použít algoritmus SHA-2.  
  
    ```console  
    sn -p IdentityKey.snk IdentityPubKey.snk sha256  
    ```  
  
3. Vytvoří zpožděný podpis sestavení se souborem veřejného klíče identity.  
  
    ```console  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
4. Znovu podepište sestavení pomocí páru klíčů s úplnými identitami.  
  
    ```console  
    sn -Ra MyAssembly.exe IdentityKey.snk  
    ```  
  
### <a name="sign-with-sha-2-with-key-migration"></a>Podepsání pomocí SHA-2 s migrací klíče  
 Spusťte následující příkazy z příkazového řádku pro podepsání sestavení pomocí migrované signatury silného názvu.  
  
1. Vygenerujte dvojici klíčů identity a signatury (v případě potřeby).  
  
    ```console  
    sn -k IdentityKey.snk  
    sn -k SignatureKey.snk  
    ```  
  
2. Extrahujte veřejný klíč podpisu a určete, že se při podepisování s tímto klíčem má použít algoritmus SHA-2.  
  
    ```console  
    sn -p SignatureKey.snk SignaturePubKey.snk sha256  
    ```  
  
3. Extrahujte veřejný klíč identity, který určuje algoritmus hash, který generuje podpis počítadla.  
  
    ```console  
    sn -p IdentityKey.snk IdentityPubKey.snk  
    ```  
  
4. Vygenerujte parametry pro atribut <xref:System.Reflection.AssemblySignatureKeyAttribute> a připojte atribut k sestavení.  
  
    ```console  
    sn -a IdentityPubKey.snk IdentityKey.snk SignaturePubKey.snk  
    ```  

    Výsledkem je výstup podobný následujícímu.

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

    Tento výstup je pak možné transformovat na AssemblySignatureKeyAttribute.

    ```
    [assembly:System.Reflection.AssemblySignatureKeyAttribute(
    "002400000c80000094000000060200000024000052534131000400000100010005a3a81ac0a519d96244a9c589fc147c7d403e40ccf184fc290bdd06c7339389a76b738e255a2bce1d56c3e7e936e4fc87d45adc82ca94c716b50a65d39d373eea033919a613e4341c66863cb2dc622bcb541762b43893434d219d1c43f07e9c83fada2aed400b9f6e44ff05e3ecde6c2827830b8f43f7ac8e3270a34d153cdd",
    "e3cf7c211678c4d1a7b8fb20276c894ab74c29f0b5a34de4d61e63d4a997222f78cdcbfe4c91ebe1ddf9f3505a32edcb2a76f34df0450c4f61e376b70fa3cdeb7374b1b8e2078b121e2ee6e8c6a8ed661cc35621b4af53ac29c9e41738f199a81240e8fd478c887d1a30729d34e954a97cddce66e3ae5fec2c682e57b7442738"
    )]
    ```
  
5. Vytvoří zpožděný podpis sestavení s veřejným klíčem identity.  
  
    ```console  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
6. Plně podepíše sestavení pomocí páru podpisových klíčů.  
  
    ```console  
    sn -Ra MyAssembly.exe SignatureKey.snk  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Vytváření a používání sestavení se silným názvem](create-use-strong-named.md)
