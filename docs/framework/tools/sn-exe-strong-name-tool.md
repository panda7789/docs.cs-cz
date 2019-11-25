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
ms.openlocfilehash: 90cad6529b3ac2a8afedaca0c43d5c7561dcf9e6
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74138960"
---
# <a name="snexe-strong-name-tool"></a>Sn.exe (nástroj pro silný název)
Nástroj Strong Name (Sn. exe) pomáhá podepisovat sestavení se [silnými názvy](../../standard/assembly/strong-named.md). Nástroj Sn.exe poskytuje možnosti pro správu klíčů, generování podpisů a ověřování podpisů.  
  
> [!WARNING]
> Nespoléhá se na silné názvy zabezpečení. Poskytují pouze jedinečnou identitu.

 Další informace o silných názvech a sestaveních se silným názvem naleznete v tématu [sestavení se silným názvem](../../standard/assembly/strong-named.md) a [Postupy: podepsání sestavení silným názvem](../../standard/assembly/sign-strong-name.md).  
  
 Nástroj Strong Name je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit nástroj, použijte Developer Command Prompt (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md).  

> [!NOTE]
> Na 64 počítačů 32 spusťte 64bitovou verzi programu sn. exe pomocí Developer Command Prompt pro sadu Visual Studio a verzi 64-bit pomocí příkazového řádku sady Visual Studio x64 win64. 
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
sn [-quiet][option [parameter(s)]]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Možnost|Popis|  
|------------|-----------------|  
|`-a identityKeyPairFile signaturePublicKeyFile`|Generuje data <xref:System.Reflection.AssemblySignatureKeyAttribute> pro migraci klíče identity na podpisový klíč ze souboru.|  
|`-ac identityPublicKeyFile identityKeyPairContainer signaturePublicKeyFile`|Generuje <xref:System.Reflection.AssemblySignatureKeyAttribute> data pro migraci klíče identity na klíč podpisu z kontejneru klíčů.|  
|`-c [csp]`|Nastaví výchozího zprostředkovatele kryptografických služeb (CSP) pro použití k podepisování se silným názvem. Toto nastavení platí pro celý počítač. Pokud název CSP nezadáte, nástroj Sn.exe vymaže aktuální nastavení.|  
|`-d container`|Odstraní zadaný kontejner klíče z CSP silného názvu.|  
|`-D assembly1 assembly2`|Ověří, zda se dvě sestavení liší pouze v podpisu. Toto se často používá jako kontrola poté, co bylo sestavení znovu podepsáno jiným párem klíčů.|  
|`-e assembly outfile`|Extrahuje veřejný klíč ze *sestavení* a uloží jej do *souboru.*|  
|`-h`|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|`-i infile container`|Nainstaluje dvojici klíčů ze *souboru InFile* v zadaném kontejneru klíčů. Kontejner klíčů je umístěn v CSP silného názvu.|  
|`-k [keysize] outfile`|Vygeneruje nový klíč <xref:System.Security.Cryptography.RSACryptoServiceProvider> zadané velikosti a zapíše ho do zadaného souboru.  Do souboru je zapsán veřejný i soukromý klíč.<br /><br /> Nezadáte-li velikost klíče, je dle výchozího nastavení vygenerován 1024bitový klíč, pokud máte nainstalovaný vylepšený zprostředkovatel kryptografických služeb Microsoft. V opačném případě je vygenerován 512bitový klíč.<br /><br /> Parametr *Size* klíče podporuje délky klíčů od 384 do 16 384 bitů v přírůstcích po 8 bitech, pokud máte nainstalovaného rozšířeného zprostředkovatele kryptografických služeb společnosti Microsoft.  Je-li nainstalován základní zprostředkovatel kryptografických služeb Microsoft, podporuje délky klíčů od 384 do 512 bitů v krocích po 8 bitech.|  
|`-m [y|n]`|Určí, zda jsou kontejnery klíčů specifické pro počítač nebo pro uživatele. Pokud zadáte *y*, kontejnery klíčů jsou specifické pro počítač. Pokud zadáte *n*, kontejnery klíčů jsou specifické pro uživatele.<br /><br /> Není-li zadána žádná z hodnot y nebo n, zobrazí tato možnost aktuální nastavení.|  
|`-o infile [outfile]`|Extrahuje veřejný klíč ze *souboru InFile* a uloží jej do souboru. csv. Každý bajt veřejného klíče je oddělen čárkou. Tento formát je užitečný pro pevné zakódování odkazů na klíče jako inicializovaných polí ve zdrojovém kódu. Pokud nezadáte žádný *soubor*, tato možnost umístí výstup do schránky. **Poznámka:**  Tato možnost neověřuje, zda je vstup pouze veřejný klíč. Pokud `infile` obsahuje dvojici klíčů s privátním klíčem, je také extrahován soukromý klíč.|  
|`-p infile outfile [hashalg]`|Extrahuje veřejný klíč z páru klíčů v *souboru InFile* a uloží jej do *souboru*s možností volitelně pomocí algoritmu RSA určeného parametrem *hashAlg*. Tento veřejný klíč lze použít k zpožděnému podepsání sestavení pomocí možností **/delaysign +** a **/keyfile** [linkeru sestavení (Al. exe)](al-exe-assembly-linker.md). Pokud je sestavení podepsáno opožděně, je v době kompilace nastaven pouze veřejný klíč a v souboru je vyhrazen prostor pro pozdější přidání podpisu, až bude znám soukromý klíč.|  
|`-pc container outfile [hashalg]`|Extrahuje veřejný klíč z páru klíčů v *kontejneru* a uloží jej do *souboru*. Použijete-li možnost *hashAlg* , použije se k extrakci veřejného klíče algoritmus RSA.|  
|`-Pb [y|n]`|Určí, zda bude vynucena zásada potlačení silných názvů. Zadáte-li hodnotu *y*, silné názvy pro sestavení s úplným vztahem důvěryhodnosti nejsou ověřovány, pokud jsou načteny do <xref:System.AppDomain>plně důvěryhodného vztahu důvěryhodnosti. Zadáte-li hodnotu *n*, silné názvy jsou ověřovány pro správnost, ale ne pro konkrétní silný název. <xref:System.Security.Permissions.StrongNameIdentityPermission> nemá žádný vliv na sestavení s úplným vztahem důvěryhodnosti. Je zapotřebí provést vlastní kontrolu shody silných názvů.<br /><br /> Pokud není zadán žádný `y` ani `n`, zobrazí tato možnost aktuální nastavení. Výchozí hodnota je `y`. **Poznámka:**  Na 64 počítačů, je nutné nastavit tento parametr v rámci 32 i v instancích systému sn. exe pro 64.|  
|`-q[uiet]`|Určuje použití tichého režimu; potlačí zobrazování zpráv o úspěchu.|  
|`-R[a] assembly infile`|Znovu podepíše dříve podepsané nebo zpožděné podepsané sestavení s dvojicí klíčů v *souboru InFile*.<br /><br /> Je **-li použito-RA** , jsou hodnoty hash přepočítány pro všechny soubory v sestavení.|  
|`-Rc[a] assembly container`|Znovu podepíše dříve podepsané nebo zpožděné podepsané sestavení s dvojicí klíčů v *kontejneru*.<br /><br /> Je **-li použit-RCA** , jsou pro všechny soubory v sestavení přepočítány hodnoty hash.|  
|`-Rh assembly`|Přepočítá hodnoty hash pro všechny soubory v sestavení.|  
|`-t[p] infile`|Zobrazí token pro veřejný klíč uložený v *souboru InFile*. Obsah *souboru InFile* musí být veřejný klíč dříve vygenerovaný ze souboru dvojice klíčů pomocí **-p**.  Nepoužívejte možnost **-t [p]** k extrakci tokenu přímo ze souboru dvojice klíčů.<br /><br /> Nástroj Sn.exe počítá token z veřejného klíče pomocí funkce hash. Z důvodu šetření místem ukládá modul CLR tokeny veřejných klíčů do manifestů jako součást odkazů na jiné sestavení ve chvíli, kdy je do sestavení se silným názvem zaznamenána závislost. Možnost **-TP** zobrazí spolu s tokenem také veřejný klíč. Pokud byl atribut <xref:System.Reflection.AssemblySignatureKeyAttribute> aplikován na sestavení, je token pro klíč identity a zobrazí se název algoritmu hash a klíč identity.<br /><br /> Tato možnost neověřuje popis sestavení a neměla by být použita pro rozhodování o důvěryhodnosti.  Tato možnost zobrazuje pouze nezpracovaná data tokenu veřejného klíče.|  
|`-T[p] assembly`|Zobrazí token veřejného klíče pro *sestavení.* *Sestavení* musí být název souboru, který obsahuje manifest sestavení.<br /><br /> Nástroj Sn.exe počítá token z veřejného klíče pomocí funkce hash. Z důvodu šetření místem ukládá modul runtime tokeny veřejných klíčů do manifestů jako součást odkazů na jiné sestavení ve chvíli, kdy je do sestavení se silným názvem zaznamenána závislost. Možnost **-TP** zobrazí spolu s tokenem také veřejný klíč. Pokud byl atribut <xref:System.Reflection.AssemblySignatureKeyAttribute> aplikován na sestavení, je token pro klíč identity a zobrazí se název algoritmu hash a klíč identity.<br /><br /> Tato možnost neověřuje popis sestavení a neměla by být použita pro rozhodování o důvěryhodnosti.  Tato možnost zobrazuje pouze nezpracovaná data tokenu veřejného klíče.|  
|`-TS assembly infile`|Otestuje podpis podepsaného nebo částečně podepsaného *sestavení* s dvojicí klíčů v *souboru InFile*.|  
|`-TSc assembly container`|Otestuje podpis podepsaného nebo částečně podepsaného *sestavení* s dvojicí klíčů v *kontejneru*kontejneru klíčů.| 
|`-v assembly`|Ověří silný název v *sestavení*, kde *sestavení* je název souboru, který obsahuje manifest sestavení.|  
|`-vf assembly`|Ověří silný název v *sestavení.* Na rozdíl od možnosti- **v** **– VF** vynutí ověření, i když je zakázaný pomocí možnosti **-VR** .|  
|`-Vk regfile.reg assembly [userlist] [infile]`|Vytvoří soubor registračních položek (.reg), které lze použít k registraci zadaného sestavení pro vynechání ověření. Pravidla pro pojmenování sestavení, která platí pro možnost **-VR** , se vztahují také na **– VK** . Informace o možnostech *userlist* a *InFile* najdete v tématu – možnost **– VR** .|  
|`-Vl`|Vypíše aktuální nastavení pro ověřování silných názvů v tomto počítači.|  
|`-Vr  assembly [userlist] [infile]`|Zaregistruje *sestavení* pro vynechání ověření. Volitelně lze také zadat čárkou oddělený seznam uživatelských jmen, pro která by vynechání ověřování mělo platit. Pokud zadáte *soubor InFile*, ověřování zůstane zapnuto, ale veřejný klíč v *souboru InFile* se používá v operacích ověřování. Můžete zadat *sestavení* ve tvaru *\*, StrongName* pro registraci všech sestavení se zadaným silným názvem. Pro *StrongName*zadejte řetězec šestnáctkových číslic, který představuje tokenový tvar veřejného klíče. Chcete-li zobrazit token veřejného klíče, Prohlédněte si možnosti **-t** a **-t** . **Upozornění:**  Tuto možnost použijte pouze během vývoje. Přidání sestavení na seznam pro přeskočení ověření vytvoří ohrožení zabezpečení. Škodlivé sestavení by mohlo použít plně zadaný název sestavení (název sestavení, verze, jazyková verze a token veřejného klíče), které je přidáno do seznamu pro přeskočení ověření, k falšování identity. To by také umožnilo škodlivému sestavení přeskočit ověření.|  
|||  
|`-Vu  assembly`|Zruší registraci *sestavení* pro vynechání ověření. Stejná pravidla pro pojmenovávání sestavení, která se vztahují na **VR** , se vztahují na **VU**.|  
|`-Vx`|Odstraní všechny záznamy o vynechání ověřování.|  
|`-?`|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
> [!NOTE]
> Všechny možnosti nástroje Sn.exe rozlišují velká a malá písmena a musí být pro rozpoznání nástrojem zapsána přesně dle tabulky.  
  
## <a name="remarks"></a>Poznámky  
 Možnosti **-R** a **– RC** jsou užitečné u sestavení, která byla podepsána opožděně. V tomto scénáři byl při kompilování nastaven pouze veřejný klíč a podepsání bylo provedeno později, až při znalosti soukromého klíče.  
  
> [!NOTE]
> Pro parametry (například –**VR)** , které zapisují do chráněných prostředků, jako je například registr, spusťte nástroj Sn. exe jako správce.  
  
Nástroj Strong Name předpokládá, že páry veřejného a privátního klíče jsou vygenerovány pomocí identifikátoru `AT_SIGNATURE` algoritmu. Páry veřejného a privátního klíče generované algoritmem `AT_KEYEXCHANGE` generují chybu. 

## <a name="examples"></a>Příklady  
 Následující příkaz vytvoří nový, náhodný pár klíčů a uloží jej do `keyPair.snk`.  
  
```console  
sn -k keyPair.snk  
```  
  
 Následující příkaz uloží klíč do `keyPair.snk` v kontejneru `MyContainer` v CSP silného názvu.  
  
```console  
sn -i keyPair.snk MyContainer  
```  
  
 Následující příkaz extrahuje veřejný klíč z `keyPair.snk` a uloží ho do `publicKey.snk`.  
  
```console  
sn -p keyPair.snk publicKey.snk  
```  
  
 Následující příkaz zobrazí veřejný klíč a token pro veřejný klíč obsažený v `publicKey.snk`.  
  
```console  
sn -tp publicKey.snk  
```  
  
 Následující příkaz ověří `MyAsm.dll`sestavení.  
  
```console  
sn -v MyAsm.dll  
```  
  
 Následující příkaz odstraní `MyContainer` z výchozího zprostředkovatele CSP.  
  
```console  
sn -d MyContainer  
```  
  
## <a name="see-also"></a>Viz také:

- [Nástroje](index.md)
- [Al.exe (linker sestavení)](al-exe-assembly-linker.md)
- [Sestavení se silným názvem](../../standard/assembly/strong-named.md)
- [Příkazové řádky](developer-command-prompt-for-vs.md)
