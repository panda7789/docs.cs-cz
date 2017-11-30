---
title: "Sn.exe (nástroj pro silný název)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- public keys, signing files
- Strong Name tool
- Sn.exe
- assemblies [.NET Framework], signing
- signing files
- strong-named assemblies, signing files
- key pairs for signing files
ms.assetid: c1d2b532-1b8e-4c7a-8ac5-53b801135ec6
caps.latest.revision: "44"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e303246737d52f76d893074973804710b2dc9b71
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="snexe-strong-name-tool"></a>Sn.exe (nástroj pro silný název)
Nástroj silného názvu (Sn.exe) pomáhá přihlašovací sestavení s [silné názvy](../../../docs/framework/app-domains/strong-named-assemblies.md). Nástroj Sn.exe poskytuje možnosti pro správu klíčů, generování podpisů a ověřování podpisů.  
  
 Další informace o silné názvy a sestavení se silným názvem naleznete v tématu [sestavení se silným názvem](../../../docs/framework/app-domains/strong-named-assemblies.md) a [postupy: podepsání sestavení se silným názvem](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).  
  
 Nástroj Strong Name je automaticky nainstalován se sadou Visual Studio. Spusťte nástroj pomocí příkazového řádku vývojáře (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace najdete v tématu [příkazového řádku](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
> [!NOTE]
>  Na 64bitových počítačích spusťte 32bitovou verzi Sn.exe pomocí příkazového řádku Visual Studio a 64bitová verze pomocí příkazového řádku Visual Studia x64 Win64.  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
sn [-quiet][option [parameter(s)]]  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Možnost|Popis|  
|------------|-----------------|  
|**-a** *identityKeyPairFile* *signaturePublicKeyFile*|Generuje <xref:System.Reflection.AssemblySignatureKeyAttribute> data migrovat do klíč podpisu klíč identity ze souboru.|  
|**-ac** *identityPublicKeyFile* *identityKeyPairContainer* *signaturePublicKeyFile*|Generuje <xref:System.Reflection.AssemblySignatureKeyAttribute> data migrovat do klíč podpisu klíč identity z kontejneru klíčů.|  
|**-c** [*csp*]|Nastaví výchozího zprostředkovatele kryptografických služeb (CSP) pro použití k podepisování se silným názvem. Toto nastavení platí pro celý počítač. Pokud název CSP nezadáte, nástroj Sn.exe vymaže aktuální nastavení.|  
|**-d** *kontejneru*|Odstraní zadaný kontejner klíče z CSP silného názvu.|  
|**-D***assembly1 assembly2* |Ověří, zda se dvě sestavení liší pouze v podpisu. Toto se často používá jako kontrola poté, co bylo sestavení znovu podepsáno jiným párem klíčů.|  
|**-e***Výstupní_soubor sestavení* |Extrahuje veřejného klíče z *sestavení* a uloží jej do *Výstupní_soubor.*|  
|**-h**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**-i** *Vstupní_soubor kontejneru*|Nainstaluje pár klíčů z *Vstupní_soubor* v zadaném kontejneru klíčů. Kontejner klíčů je umístěn v CSP silného názvu.|  
|**-k** [*velikost klíče*] *Výstupní_soubor*|Generuje nový <xref:System.Security.Cryptography.RSACryptoServiceProvider> klíče zadané velikosti a zapíše ho do zadaného souboru.  Do souboru je zapsán veřejný i soukromý klíč.<br /><br /> Nezadáte-li velikost klíče, je dle výchozího nastavení vygenerován 1024bitový klíč, pokud máte nainstalovaný vylepšený zprostředkovatel kryptografických služeb Microsoft. V opačném případě je vygenerován 512bitový klíč.<br /><br /> *Velikost klíče* parametr podporuje délky klíčů z 384 bitů na 16 384 bitů v přírůstcích po 8 bitů, pokud máte Microsoft rozšířené zprostředkovatelem kryptografických služeb nainstalován.  Je-li nainstalován základní zprostředkovatel kryptografických služeb Microsoft, podporuje délky klíčů od 384 do 512 bitů v krocích po 8 bitech.|  
|**-m** [**y** *&#124;* **n**]|Určí, zda jsou kontejnery klíčů specifické pro počítač nebo pro uživatele. Pokud zadáte *y*, kontejnery klíčů jsou specifické pro počítač. Pokud zadáte  *n* , kontejnery klíčů jsou specifické pro uživatele.<br /><br /> Není-li zadána žádná z hodnot y nebo n, zobrazí tato možnost aktuální nastavení.|  
|**-o***Vstupní_soubor* [*Výstupní_soubor*]  |Extrahuje veřejného klíče z *Vstupní_soubor* a ukládá je v souboru CSV. Každý bajt veřejného klíče je oddělen čárkou. Tento formát je užitečný pro pevné zakódování odkazů na klíče jako inicializovaných polí ve zdrojovém kódu. Pokud nezadáte *Výstupní_soubor*, tato možnost umístí výstup do schránky. **Poznámka:** tato možnost není ověřte, zda vstup je veřejný klíč. Pokud `infile` obsahuje pár klíčů s privátním klíčem, je také extrahován privátní klíč.|  
|**-p** *Vstupní_soubor Výstupní_soubor* [*Algoritmus_hash*]|Extrahuje veřejný klíč z tohoto páru klíčů v *Vstupní_soubor* a uloží jej do *Výstupní_soubor*, volitelně pomocí algoritmu RSA určeného *Algoritmus_hash*. Tento veřejný klíč může být použit zpoždění podepsání sestavení pomocí **/delaysign+** a **/keyfile** možnosti [Linker sestavení (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md). Pokud je sestavení podepsáno opožděně, je v době kompilace nastaven pouze veřejný klíč a v souboru je vyhrazen prostor pro pozdější přidání podpisu, až bude znám soukromý klíč.|  
|**-pc***kontejneru* *Výstupní_soubor* [*Algoritmus_hash*]  |Extrahuje veřejný klíč z tohoto páru klíčů v *kontejneru* a uloží jej do *Výstupní_soubor*. Pokud použijete *Algoritmus_hash* možnost, algoritmus RSA slouží k extrakci veřejný klíč.|  
|**-Pb** [**y** *&#124;* **n**]|Určí, zda bude vynucena zásada potlačení silných názvů. Pokud zadáte *y*, silné názvy pro plné důvěryhodnosti sestavení uděláte, neověřuje při načítání do plné důvěryhodnosti <xref:System.AppDomain>. Pokud zadáte  *n* , silné názvy se ověří správnost, ale ne pro konkrétní silný název. <xref:System.Security.Permissions.StrongNameIdentityPermission> Nemá žádný vliv na sestavení plné důvěryhodnosti. Je zapotřebí provést vlastní kontrolu shody silných názvů.<br /><br /> Pokud ani `y` ani `n` není zadaný, tato možnost zobrazí aktuální nastavení. Výchozí hodnota je `y`. **Poznámka:** na 64bitových počítačích, musí v 32bitová verze a 64bitová verze instance Sn.exe nastavte tento parametr.|  
|**-q**[**uiet**]|Určuje použití tichého režimu; potlačí zobrazování zpráv o úspěchu.|  
|**-R**[****] *sestavení* *Vstupní_soubor*|Znovu podepíše dříve podepsané nebo zpoždění podepsané sestavení s páru klíčů v *Vstupní_soubor*.<br /><br /> Pokud **-Ra** se používá, hodnoty hash přepočítávány pro všechny soubory v sestavení.|  
|**-Rc**[****] *kontejneru sestavení*|Znovu podepíše dříve podepsané nebo zpoždění podepsané sestavení s páru klíčů v *kontejneru*.<br /><br /> Pokud **- Rca** se používá, hodnoty hash přepočítávány pro všechny soubory v sestavení.|  
|**-Rh** *sestavení*|Přepočítá hodnoty hash pro všechny soubory v sestavení.|  
|**-t**[**p**] *Vstupní_soubor*|Zobrazí token pro veřejný klíč uložené v *Vstupní_soubor*. Obsah *Vstupní_soubor* musí být veřejný klíč dříve generované ze souboru pár klíčů pomocí **-p**.  Nepoužívejte **-t [p]** možnost extrahuje daný token přímo ze souboru pár klíčů.<br /><br /> Nástroj Sn.exe počítá token z veřejného klíče pomocí funkce hash. Z důvodu šetření místem ukládá modul CLR tokeny veřejných klíčů do manifestů jako součást odkazů na jiné sestavení ve chvíli, kdy je do sestavení se silným názvem zaznamenána závislost. **- Tp** možnost zobrazí veřejný klíč kromě token. Pokud <xref:System.Reflection.AssemblySignatureKeyAttribute> byl použit atribut sestavení, je token pro klíč identity a se zobrazí název algoritmu hash a klíč identity.<br /><br /> Tato možnost neověřuje popis sestavení a neměla by být použita pro rozhodování o důvěryhodnosti.  Tato možnost zobrazuje pouze nezpracovaná data tokenu veřejného klíče.|  
|**-T**[**p**] *sestavení*|Zobrazí token veřejného klíče pro *sestavení.* *Sestavení* musí být název souboru, který obsahuje manifest sestavení.<br /><br /> Nástroj Sn.exe počítá token z veřejného klíče pomocí funkce hash. Z důvodu šetření místem ukládá modul runtime tokeny veřejných klíčů do manifestů jako součást odkazů na jiné sestavení ve chvíli, kdy je do sestavení se silným názvem zaznamenána závislost. **- Tp** možnost zobrazí veřejný klíč kromě token. Pokud <xref:System.Reflection.AssemblySignatureKeyAttribute> byl použit atribut sestavení, je token pro klíč identity a se zobrazí název algoritmu hash a klíč identity.<br /><br /> Tato možnost neověřuje popis sestavení a neměla by být použita pro rozhodování o důvěryhodnosti.  Tato možnost zobrazuje pouze nezpracovaná data tokenu veřejného klíče.|  
|`-TS` `assembly` `infile`|Test přihlásí podepsaný držitelem nebo částečně podepsané `assembly` s páru klíčů v `infile`.|  
|-`TSc``assembly``container`|Test přihlásí podepsaný držitelem nebo částečně podepsané `assembly` s páru klíčů v kontejneru klíčů `container`.|  
|**-v** *sestavení*|Ověřuje silného názvu v *sestavení*, kde *sestavení* je název souboru, který obsahuje manifest sestavení.|  
|**-vf***sestavení* |Ověřuje silného názvu v *sestavení.* Na rozdíl od **- v** možnost, **-vf** vynutí ověření, i když je zakázán, pomocí **- Vr** možnost.|  
|**-Vk***regfile.reg* *sestavení* [*userlist*] [*Vstupní_soubor*]  |Vytvoří soubor registračních položek (.reg), které lze použít k registraci zadaného sestavení pro vynechání ověření. Pravidla pro názvy sestavení, která se vztahují k **- Vr** možnost použít **– Vk** také. Informace o *userlist* a *Vstupní_soubor* najdete v části Možnosti, **– Vr** možnost.|  
|**-Vl**|Vypíše aktuální nastavení pro ověřování silných názvů v tomto počítači.|  
|**-Vr***sestavení* [*userlist*] [*Vstupní_soubor*]  |Zaregistruje *sestavení* pro přeskočení ověření. Volitelně lze také zadat čárkou oddělený seznam uživatelských jmen, pro která by vynechání ověřování mělo platit. Pokud zadáte *Vstupní_soubor*, zůstanou ověření povoleno, ale veřejný klíč v *Vstupní_soubor* se používá v operacích ověření. Můžete zadat *sestavení* ve tvaru  *\*, strongname* pro registraci všechny sestavení se silným názvem zadaný. Pro *strongname*, zadejte řetězec šestnáctkových číslic představující tokenizovaná formu veřejný klíč. Najdete v článku **-t** a **-T** možnosti zobrazíte token veřejného klíče. **Upozornění:** pomocí této možnosti pouze během vývoje. Přidání sestavení na seznam pro přeskočení ověření vytvoří ohrožení zabezpečení. Škodlivé sestavení by mohlo použít plně zadaný název sestavení (název sestavení, verze, jazyková verze a token veřejného klíče), které je přidáno do seznamu pro přeskočení ověření, k falšování identity. To by také umožnilo škodlivému sestavení přeskočit ověření.|  
|||  
|**-Vu***sestavení* |Zruší registraci *sestavení* pro přeskočení ověření. Stejná pravidla pro sestavení názvy, které platí pro **- Vr** týkají **- Vu**.|  
|**-Vx**|Odstraní všechny záznamy o vynechání ověřování.|  
|**-?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
> [!NOTE]
>  Všechny možnosti nástroje Sn.exe rozlišují velká a malá písmena a musí být pro rozpoznání nástrojem zapsána přesně dle tabulky.  
  
## <a name="remarks"></a>Poznámky  
 **-R** a **– Rc** možnosti jsou užitečné s sestavení, která byla podepsána zpoždění. V tomto scénáři byl při kompilování nastaven pouze veřejný klíč a podepsání bylo provedeno později, až při znalosti soukromého klíče.  
  
> [!NOTE]
>  Pro parametry (například –**Vr)** , zápis k chráněným prostředkům, například registr, SN.exe spustit jako správce.  
  
## <a name="examples"></a>Příklady  
 Následující příkaz vytvoří dvojici klíčů nové, náhodné a uloží jej do `keyPair.snk`.  
  
```  
sn -k keyPair.snk  
```  
  
 Následující příkaz uloží klíč v `keyPair.snk` v kontejneru `MyContainer` v silné název CSP.  
  
```  
sn -i keyPair.snk MyContainer  
```  
  
 Následující příkaz extrahuje veřejný klíč z `keyPair.snk` a uloží jej do `publicKey.snk`.  
  
```  
sn -p keyPair.snk publicKey.snk  
```  
  
 Následující příkaz zobrazí veřejný klíč a token veřejného klíče obsažené v `publicKey.snk`.  
  
```  
sn -tp publicKey.snk  
```  
  
 Následující příkaz ověřuje sestavení `MyAsm.dll`.  
  
```  
sn -v MyAsm.dll  
```  
  
 Následující příkaz odstraní `MyContainer` z výchozího zprostředkovatele kryptografických služeb.  
  
```  
sn -d MyContainer  
```  
  
## <a name="see-also"></a>Viz také  
 [Nástroje](../../../docs/framework/tools/index.md)  
 [Al.exe (Linker sestavení)](../../../docs/framework/tools/al-exe-assembly-linker.md)  
 [Sestavení se silným názvem](../../../docs/framework/app-domains/strong-named-assemblies.md)  
 [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
