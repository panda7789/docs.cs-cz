---
title: Sn.exe (nástroj pro silný název)
ms.date: 03/30/2017
helpviewer_keywords:
- public keys, signing files
- Strong Name tool
- Sn.exe
- assemblies [.NET Framework], signing
- signing files
- strong-named assemblies, signing files
- key pairs for signing files
ms.assetid: c1d2b532-1b8e-4c7a-8ac5-53b801135ec6
ms.openlocfilehash: b5eee15a08dcae42263e06939c197ec0848816a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180306"
---
# <a name="snexe-strong-name-tool"></a>Sn.exe (nástroj pro silný název)
Nástroj Silný název (Sn.exe) pomáhá podepisovat sestavení [silnými názvy](../../standard/assembly/strong-named.md). Nástroj Sn.exe poskytuje možnosti pro správu klíčů, generování podpisů a ověřování podpisů.  
  
> [!WARNING]
> Nespoléhejte se na silné názvy pro zabezpečení. Poskytují pouze jedinečnou identitu.

 Další informace o silných pojmenování a sestavení s výrazným názvem naleznete [v tématu sestavení se silným názvem](../../standard/assembly/strong-named.md) a [postup: Podepsání sestavení se silným názvem](../../standard/assembly/sign-strong-name.md).  
  
 Nástroj Strong Name je automaticky nainstalován se sadou Visual Studio. Chcete-li nástroj spustit, použijte příkazový řádek pro vývojáře (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace naleznete v [příkazových koncích](developer-command-prompt-for-vs.md).  

> [!NOTE]
> V 64bitových počítačích spusťte 32bitovou verzi programu Sn.exe pomocí příkazového řádku pro vývojáře pro sady Visual Studio a 64bitové verze pomocí příkazového řádku sady Visual Studio x64 Win64.
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
sn [-quiet][option [parameter(s)]]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Možnost|Popis|  
|------------|-----------------|  
|`-a identityKeyPairFile signaturePublicKeyFile`|Generuje <xref:System.Reflection.AssemblySignatureKeyAttribute> data pro migraci klíče identity do klíče podpisu ze souboru.|  
|`-ac identityPublicKeyFile identityKeyPairContainer signaturePublicKeyFile`|Generuje <xref:System.Reflection.AssemblySignatureKeyAttribute> data pro migraci klíče identity do klíče podpisu z kontejneru klíčů.|  
|`-c [csp]`|Nastaví výchozího zprostředkovatele kryptografických služeb (CSP) pro použití k podepisování se silným názvem. Toto nastavení platí pro celý počítač. Pokud název CSP nezadáte, nástroj Sn.exe vymaže aktuální nastavení.|  
|`-d container`|Odstraní zadaný kontejner klíče z CSP silného názvu.|  
|`-D assembly1 assembly2`|Ověří, zda se dvě sestavení liší pouze v podpisu. Toto se často používá jako kontrola poté, co bylo sestavení znovu podepsáno jiným párem klíčů.|  
|`-e assembly outfile`|Extrahuje veřejný klíč z *sestavení* a ukládá jej do *outfile.*|  
|`-h`|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|`-i infile container`|Nainstaluje dvojici klíčů z *infile v* zadaném kontejneru klíčů. Kontejner klíčů je umístěn v CSP silného názvu.|  
|`-k [keysize] outfile`|Vygeneruje <xref:System.Security.Cryptography.RSACryptoServiceProvider> nový klíč zadané velikosti a zapíše jej do zadaného souboru.  Do souboru je zapsán veřejný i soukromý klíč.<br /><br /> Nezadáte-li velikost klíče, je dle výchozího nastavení vygenerován 1024bitový klíč, pokud máte nainstalovaný vylepšený zprostředkovatel kryptografických služeb Microsoft. V opačném případě je vygenerován 512bitový klíč.<br /><br /> Parametr *keysize* podporuje délky klíčů od 384 bitů do 16 384 bitů v přírůstcích po 8 bitech, pokud máte nainstalovaného zprostředkovatele kryptografických služeb společnosti Microsoft.  Je-li nainstalován základní zprostředkovatel kryptografických služeb Microsoft, podporuje délky klíčů od 384 do 512 bitů v krocích po 8 bitech.|  
|`-m [y|n]`|Určí, zda jsou kontejnery klíčů specifické pro počítač nebo pro uživatele. Pokud zadáte *y*, kontejnery klíčů jsou specifické pro počítač. Pokud zadáte *n*, kontejnery klíčů jsou specifické pro uživatele.<br /><br /> Není-li zadána žádná z hodnot y nebo n, zobrazí tato možnost aktuální nastavení.|  
|`-o infile [outfile]`|Extrahuje veřejný klíč z *souboru* a uloží jej do souboru .csv. Každý bajt veřejného klíče je oddělen čárkou. Tento formát je užitečný pro pevné zakódování odkazů na klíče jako inicializovaných polí ve zdrojovém kódu. Pokud nezadáte *outfile*, tato možnost umístí výstup do schránky. **Poznámka:**  Tato možnost neověřuje, zda je vstup pouze veřejný klíč. Pokud `infile` obsahuje dvojici klíčů se soukromým klíčem, soukromý klíč je také extrahován.|  
|`-p infile outfile [hashalg]`|Extrahuje veřejný klíč z dvojice klíčů v *infile* a ukládá jej do *outfile*, volitelně pomocí algoritmu RSA *určeného hashalg*. Tento veřejný klíč lze použít ke zpoždění podepsat sestavení pomocí **/delaysign+** a **/keyfile** možnosti [propojovacího programu sestavení (Al.exe)](al-exe-assembly-linker.md). Pokud je sestavení podepsáno opožděně, je v době kompilace nastaven pouze veřejný klíč a v souboru je vyhrazen prostor pro pozdější přidání podpisu, až bude znám soukromý klíč.|  
|`-pc container outfile [hashalg]`|Extrahuje veřejný klíč z dvojice klíčů v *kontejneru* a ukládá jej do *outfile*. Pokud použijete možnost *hashalg,* algoritmus RSA se používá k extrahování veřejného klíče.|  
|`-Pb [y|n]`|Určí, zda bude vynucena zásada potlačení silných názvů. Pokud zadáte *y*, silné názvy pro sestavení s plnou důvěryhodností <xref:System.AppDomain>nebudou ověřeny při načtení do úplnédůvěryhodnosti . Pokud zadáte *n*, silné názvy jsou ověřeny pro správnost, ale ne pro konkrétní silný název. Nemá <xref:System.Security.Permissions.StrongNameIdentityPermission> žádný vliv na sestavení s plnou důvěryhodností. Je zapotřebí provést vlastní kontrolu shody silných názvů.<br /><br /> Pokud není `y` `n` zadánani, zobrazí se aktuální nastavení této možnosti. Výchozí formát je `y`. **Poznámka:**  V 64bitových počítačích je nutné nastavit tento parametr v 32bitových i 64bitových instancích sn.exe.|  
|`-q[uiet]`|Určuje použití tichého režimu; potlačí zobrazování zpráv o úspěchu.|  
|`-R[a] assembly infile`|Znovu podepíše dříve podepsané nebo zpožděné podepsané sestavení s dvojicí klíčů v *infile*.<br /><br /> Pokud **-Ra** se používá, hashes jsou přepočítány pro všechny soubory v sestavení.|  
|`-Rc[a] assembly container`|Znovu podepíše dříve podepsané nebo zpožděné podepsané sestavení s párem klíčů v *kontejneru*.<br /><br /> Pokud **-Rca** se používá, hashy jsou přepočítány pro všechny soubory v sestavení.|  
|`-Rh assembly`|Přepočítá hodnoty hash pro všechny soubory v sestavení.|  
|`-t[p] infile`|Zobrazí token pro veřejný klíč uložený *v infile*. Obsah *infile* musí být veřejný klíč dříve vygenerovaný ze souboru dvojice klíčů pomocí **-p**.  Nepoužívejte možnost **-t[p]** k extrahování tokenu přímo ze souboru dvojice klíčů.<br /><br /> Nástroj Sn.exe počítá token z veřejného klíče pomocí funkce hash. Z důvodu šetření místem ukládá modul CLR tokeny veřejných klíčů do manifestů jako součást odkazů na jiné sestavení ve chvíli, kdy je do sestavení se silným názvem zaznamenána závislost. Možnost **-tp** zobrazí veřejný klíč kromě tokenu. Pokud <xref:System.Reflection.AssemblySignatureKeyAttribute> byl atribut použit pro sestavení, token je pro klíč identity a zobrazí se název algoritmu hash a klíč identity.<br /><br /> Tato možnost neověřuje popis sestavení a neměla by být použita pro rozhodování o důvěryhodnosti.  Tato možnost zobrazuje pouze nezpracovaná data tokenu veřejného klíče.|  
|`-T[p] assembly`|Zobrazí token veřejného klíče pro *sestavení.* *Sestavení* musí být název souboru, který obsahuje manifest sestavení.<br /><br /> Nástroj Sn.exe počítá token z veřejného klíče pomocí funkce hash. Z důvodu šetření místem ukládá modul runtime tokeny veřejných klíčů do manifestů jako součást odkazů na jiné sestavení ve chvíli, kdy je do sestavení se silným názvem zaznamenána závislost. Možnost **-Tp** zobrazí veřejný klíč kromě tokenu. Pokud <xref:System.Reflection.AssemblySignatureKeyAttribute> byl atribut použit pro sestavení, token je pro klíč identity a zobrazí se název algoritmu hash a klíč identity.<br /><br /> Tato možnost neověřuje popis sestavení a neměla by být použita pro rozhodování o důvěryhodnosti.  Tato možnost zobrazuje pouze nezpracovaná data tokenu veřejného klíče.|  
|`-TS assembly infile`|Test podepíše podepsané nebo částečně podepsané *sestavení* dvojicí klíčů v *infile*.|  
|`-TSc assembly container`|Test podepíše podepsané nebo částečně podepsané *sestavení* dvojicí klíčů v *kontejneru*klíčů .|
|`-v assembly`|Ověří silný název v *sestavení*, kde *sestavení* je název souboru, který obsahuje manifest sestavení.|  
|`-vf assembly`|Ověří silný název v *sestavení.* Na rozdíl od možnosti **-v** **-v** - vf vynutí ověření, i když je zakázáno pomocí možnosti **-Vr.**|  
|`-Vk regfile.reg assembly [userlist] [infile]`|Vytvoří soubor registračních položek (.reg), které lze použít k registraci zadaného sestavení pro vynechání ověření. Pravidla pro pojmenování sestavení, která platí pro volbu **-Vr,** platí také pro **–Vk.** Informace o *možnostech userlistu* a *infile* naleznete v možnosti **–Vr.**|  
|`-Vl`|Vypíše aktuální nastavení pro ověřování silných názvů v tomto počítači.|  
|`-Vr  assembly [userlist] [infile]`|Registruje *sestavení* pro ověření přeskočení. Volitelně lze také zadat čárkou oddělený seznam uživatelských jmen, pro která by vynechání ověřování mělo platit. Pokud zadáte *infile*, ověření zůstane povoleno, ale veřejný klíč *v infile* se používá v ověřovacích operacích. Můžete zadat *sestavení* ve formuláři * \*, strongname* zaregistrovat všechna sestavení se zadaným silným názvem. Pro *strongname*, zadejte řetězec šestnáctkových číslic představující tokenizovaný formulář veřejného klíče. Podívejte se na možnosti **-t** a **-T** pro zobrazení tokenu veřejného klíče. **Pozor:**  Tuto možnost použijte pouze během vývoje. Přidání sestavení na seznam pro přeskočení ověření vytvoří ohrožení zabezpečení. Škodlivé sestavení by mohlo použít plně zadaný název sestavení (název sestavení, verze, jazyková verze a token veřejného klíče), které je přidáno do seznamu pro přeskočení ověření, k falšování identity. To by také umožnilo škodlivému sestavení přeskočit ověření.|  
|||  
|`-Vu  assembly`|Zruší registrace *sestavení* pro ověření přeskočení. Stejná pravidla pro pojmenování sestavení, která platí pro **-Vr** platí pro **-Vu**.|  
|`-Vx`|Odstraní všechny záznamy o vynechání ověřování.|  
|`-?`|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
> [!NOTE]
> Všechny možnosti nástroje Sn.exe rozlišují velká a malá písmena a musí být pro rozpoznání nástrojem zapsána přesně dle tabulky.  
  
## <a name="remarks"></a>Poznámky  
 **Možnosti -R** a **–Rc** jsou užitečné u sestavení, která byla podepsána zpožděním. V tomto scénáři byl při kompilování nastaven pouze veřejný klíč a podepsání bylo provedeno později, až při znalosti soukromého klíče.  
  
> [!NOTE]
> Pro parametry (například –**VR),** které zapisují do chráněných prostředků, jako je například registr, spusťte SN.exe jako správce.  
  
Nástroj Silný název předpokládá, že jsou generovány dvojice `AT_SIGNATURE` veřejných a soukromých klíčů s identifikátorem algoritmu. Dvojice veřejného a soukromého `AT_KEYEXCHANGE` klíče generované algoritmem generují chybu.

## <a name="examples"></a>Příklady  
 Následující příkaz vytvoří nový náhodný pár klíčů `keyPair.snk`a uloží jej do .  
  
```console  
sn -k keyPair.snk  
```  
  
 Následující příkaz ukládá klíč `keyPair.snk` v `MyContainer` kontejneru v silném názvu CSP.  
  
```console  
sn -i keyPair.snk MyContainer  
```  
  
 Následující příkaz extrahuje veřejný `keyPair.snk` klíč z `publicKey.snk`a ukládá jej do .  
  
```console  
sn -p keyPair.snk publicKey.snk  
```  
  
 Následující příkaz zobrazí veřejný klíč a token pro veřejný `publicKey.snk`klíč obsažený v .  
  
```console  
sn -tp publicKey.snk  
```  
  
 Následující příkaz ověří sestavení `MyAsm.dll`.  
  
```console  
sn -v MyAsm.dll  
```  
  
 Následující příkaz odstraní `MyContainer` z výchozího csp.  
  
```console  
sn -d MyContainer  
```  
  
## <a name="see-also"></a>Viz také

- [Nástroje](index.md)
- [Al.exe (linker sestavení)](al-exe-assembly-linker.md)
- [Sestavení se silným názvem](../../standard/assembly/strong-named.md)
- [Příkazové řádky](developer-command-prompt-for-vs.md)
