---
title: Vylepšené silné názvy
ms.date: 03/30/2017
helpviewer_keywords:
- strong-named assemblies
- strong naming [.NET Framework], enhanced
ms.assetid: 6cf17a82-62a1-4f6d-8d5a-d7d06dec2bb5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf4a8df87cd507f2bfb17086e83dc8374a22fe71
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746888"
---
# <a name="enhanced-strong-naming"></a>Vylepšené silné názvy
Podpis silného názvu je mechanismus identity v rozhraní .NET Framework pro identifikaci sestavení. Je digitální podpis veřejného klíče, který se obvykle používá k ověření integrity dat, které jsou předávány z původce (podepisující osoba) k příjemce (ověřovatele). Tento podpis slouží jako jedinečnou identitu pro sestavení a zajišťuje, aby odkazy na sestavení byla jednoznačná. Sestavení je podepsaný jako součást procesu sestavení a potom ověřit, když je načten.  
  
 Silné jméno podpisy Zabraňte zlými úmysly manipulovat se sestavení a opětovné podepisování sestavení s klíčem původní podepisující osoba. Ale klíče silný název nesmí obsahovat žádné spolehlivé informace o vydavateli, ani obsahují hierarchie certifikačních autorit. Podpis silného názvu zaručit důvěryhodnost osoby, která podepsala sestavení nebo označuje, zda byla tato osoba legitimní vlastníka klíče; Označuje, pouze zda Vlastník klíče podepsané sestavení. Nedoporučujeme proto pomocí podpis silného názvu jako validátor zabezpečení pro důvěryhodné kód třetích stran. Microsoft Authenticode je doporučený způsob ověření kódu.  
  
## <a name="limitations-of-conventional-strong-names"></a>Omezení konvenční silné názvy  
 Silné pojmenování technologie používané ve verzi před [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] má následující nedostatků:  
  
-   Klíče jsou neustále probíhá útok a vylepšené technik a hardwaru usnadňují odvodit privátní klíč z veřejného klíče. Ochrana před útoky, větší klíče jsou nezbytné. Verze rozhraní .NET framework před [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] poskytují možnost přihlášení pomocí jakékoli velikost klíče (výchozí velikost je 1 024 bitů), ale podepsání sestavení pomocí nového klíče dělí všechny binární soubory, které odkazují na starší identitu sestavení. Proto je velmi obtížné upgrade velikost podpisový klíč, pokud chcete, aby byla zachována kompatibilita.  
  
-   Podpis silného názvu podporuje pouze algoritmus SHA-1. Nedávno bylo zjištěno SHA-1, nedostatečné pro zabezpečené hash aplikace. Proto se silnějším algoritmem je nutné (SHA-256 nebo vyšší). Je možné, že SHA-1, dojde ke ztrátě jejího kompatibilní se standardem FIPS umístění, která by měla představit problémy pro ty, kteří se rozhodnou používejte pouze kompatibilní se standardem FIPS softwaru a algoritmy.  
  
## <a name="advantages-of-enhanced-strong-names"></a>Výhody vylepšené silné názvy  
 Hlavní výhody vylepšené silné názvy jsou kompatibilitu s existující silné názvy a schopnost deklarace identity na jiný odpovídá jedné identity:  
  
-   Vývojáři, kteří mají existující podepsaná sestavení můžete migrovat své identity algoritmy SHA-2 při zachování kompatibility s sestavení, které odkazují na staré identity.  
  
-   Vývojáři, kteří vytvářejí nové sestavení a nevadí existující podpisy silným názvem můžete používat bezpečnější algoritmus SHA-2 a podepsání sestavení mají vždy.  
  
## <a name="using-enhanced-strong-names"></a>Pomocí vylepšené silné názvy  
 Silné jméno klíče obsahovat klíč podpisu a klíč identity. Sestavení je podepsán klíč podpisu a je určeno klíčem identity. Před verzí [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], tyto dva klíče byly identické. Od verze [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], klíč identity zůstává stejná jako v předchozích verzích rozhraní .NET Framework, ale klíč podpisu je rozšířené silnější algoritmus hash. Kromě toho klíč podpisu je podepsán klíč identity vytvoří kontrolní podpis.  
  
 <xref:System.Reflection.AssemblySignatureKeyAttribute> Atribut umožňuje metadata sestavení používat existující veřejný klíč pro identitu, sestavení, která umožňuje staré odkazy na sestavení, chcete-li pokračovat v práci.  <xref:System.Reflection.AssemblySignatureKeyAttribute> Atribut používá kontrolní podpis, aby vlastník nového klíče podpisu je také vlastníkem starý klíč identity.  
  
### <a name="signing-with-sha-2-without-key-migration"></a>Podepsání pomocí algoritmu SHA-2, bez migrace klíče  
 Spusťte následující příkazy z okna příkazového řádku pro podepsání sestavení bez migrace podpis silného názvu:  
  
1.  Vygenerujte nový klíč identity (v případě potřeby).  
  
    ```  
    sn -k IdentityKey.snk  
    ```  
  
2.  Extrahujte identity veřejný klíč a zadat, že algoritmus SHA-2 má být použita při přihlašování pomocí tohoto klíče.  
  
    ```  
    sn -p IdentityKey.snk IdentityPubKey.snk sha256  
    ```  
  
3.  Zpoždění podepsání sestavení s identity soubor veřejného klíče.  
  
    ```  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
4.  Nové podepsání sestavení s páru klíčů úplné identity.  
  
    ```  
    sn -Ra MyAssembly.exe IdentityKey.snk  
    ```  
  
### <a name="signing-with-sha-2-with-key-migration"></a>Podepsání pomocí algoritmu SHA-2, přičemž migrace klíče  
 Spusťte následující příkazy z okna příkazového řádku pro podepsání sestavení podpisem migrované silným názvem.  
  
1.  Generovat identity a podpis pár klíčů (v případě potřeby).  
  
    ```  
    sn -k IdentityKey.snk  
    sn -k SignatureKey.snk  
    ```  
  
2.  Extrahujte podpis veřejný klíč a zadat, že algoritmus SHA-2 má být použita při přihlašování pomocí tohoto klíče.  
  
    ```  
    sn -p SignatureKey.snk SignaturePubKey.snk sha256  
    ```  
  
3.  Extrahujte veřejný klíč identity, který určuje algoritmus hash, který generuje kontrolní podpis.  
  
    ```  
    sn -p IdentityKey.snk IdentityPubKey.snk  
    ```  
  
4.  Generovat parametry <xref:System.Reflection.AssemblySignatureKeyAttribute> atribut a atribut přiřadit sestavení.  
  
    ```  
    sn -ac IdentityPubKey.snk IdentityKey.snk SignaturePubKey.snk  
    ```  
  
5.  Zpoždění podepsání sestavení s veřejným klíčem identity.  
  
    ```  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
6.  Plně podepište sestavení tohoto páru klíčů pro podpis.  
  
    ```  
    sn -Ra MyAssembly.exe SignatureKey.snk  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Vytváření a používání sestavení se silným názvem](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
